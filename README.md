About Project and what we have done:
This project gives us Atliq’s all employees presence for the months April , May and June (in the year 2022).
Insights drawn in this project:
- How many employees were present (in each month separately and across all months).
- For every month how many people preferred working from home.
- How many people were present , opted for Sick-leave and Work from home across all the 3 months (both by Day of week and Employee-code).
- Daily Attendance of all employees.
- KPIs for these data:
    Total Working Days
    Present Days
    Presence %
    Work from Home (abbreviated as WFH) %
    Sick Leave (abbreviated as SL) %
- Trends observed in these data:
    Sick Leave (abbreviated as SL) 
    Work from Home (abbreviated as WFH) 
    Presence







Measures used:
- WFH % = DIVIDE([WFH Count],[Present Days],0)*100


- Total Working Days =


VAR totaldays = COUNT('Final Data'[Value])
VAR nonworkdays = CALCULATE( COUNT('Final Data'[Value]),'Final Data'[Value] in {"WO","HO"})


RETURN totaldays - nonworkdays
- WFH Count = SUM('Final Data'[WFH Count])

- SL Count = SUM('Final Data'[SL Count])

- SL % = DIVIDE([SL Count],[Total Working Days],0)*100
- Present Days =


VAR Presentdays =
    CALCULATE(
        COUNT('Final Data'[Value]),
        'Final Data'[Value] = "P"
    )


RETURN Presentdays + [WFH Count]



- Presence % = DIVIDE([Present Days],'Measure Table'[Total Working Days],0) * 100




New columns created:
- WFH Count = SWITCH(TRUE(),
'Final Data'[Value] = "WFH",1,
'Final Data'[Value] = "HWFH",0.5,
0)
- SL Count = SWITCH(TRUE(),
'Final Data'[Value] = "SL",1,
'Final Data'[Value] = "HSL",0.5,
0)
- Month = FORMAT('Final Data'[Date], "MMMM")
- Day of week = FORMAT('Final Data'[Date],"ddd")






Conclusion drawn:
- Sick-leaves are increasing with time
- Employees are not preferring to work from office with time (Since Presence % is decreasing)


