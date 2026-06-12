---
title: "LibreOffice Macro"
date: 2012-11-28
forum: General Help
---

### Post by jaykays on 2012-11-28
Hi,
I have the following VBA code which works fine in microsoft office. Full code below.  I get a "basic run error '1' (see screenshot) at [COLOR="YellowGreen"] Workbooks.Open Filename:= "http://www.dartsdatabase.co.uk/EventResults.aspx?EventKey=" & i[/COLOR]

I'm new to libre office and not sure how to fix it. Any Ideas

[CENTER]**Full code**[/CENTER]
Rem Attribute VBA_ModuleType=VBAModule
Option VBASupport 1

Sub Darts_Grab()

'Don't give any popups
Application.DisplayAlerts = False


Dim bottomrow As Integer

For i = 2 To 10

    'Open that page
    Workbooks.Open Filename:= "http://www.dartsdatabase.co.uk/EventResults.aspx?EventKey=" & i
    
'Find the last results row, hopefully it's not the row we put it at 60000
    Cells(60000, 1) = "Prize Results"
    Cells.Find(What:="Prize Results", After:=ActiveCell, LookIn:=xlFormulas, _
        LookAt:=xlPart, SearchOrder:=xlByRows, SearchDirection:=xlNext, _
        MatchCase:=False, SearchFormat:=False).Activate
    bottomrow = ActiveCell.Row - 1
  
    If bottomrow < 60000 Then
    
        'If it's not the row we put in, copy the data
         Range("B9: D" & bottomrow - 1).Copy
    
        'Activate the original excel sheet
        Windows("Darts_Grab.xls").Activate
        Sheets("Output").Select
    
        'Find the bottom row and paste just below it
        Range("A65000").Select
        Selection.End(xlUp).Select
        Cells(ActiveCell.Row + 3, 1).Activate
        ActiveSheet.Paste
    
    End If
   
   
    'Close the temporary results page
    Windows("EventResults.aspx").Activate
    ActiveWorkbook.Close
    
    
Next i

Application.DisplayAlerts = True

End Sub


Thanks
Jaykays

---

### Post by Lars Noodén on 2012-11-28
LibreOffice can accept macros in JavaScript, Python, Basic or BeanShell.  I think Java might also be an option.

---

### Post by Hagar Delest on 2012-11-30
The macro language depends on the application and VBA cannot be completely implemented in other applications.

Either rewrite your macros in OOo/LO/AOO Basic or better, chose another language. Python is often advised on the [AOO English forum]("http://forum.openoffice.org/en/forum/index.php").

---

