---
title: "LibreOffice .desktop file contents wanted"
date: 2013-03-07
forum: General Help
---

### Post by vasa1 on 2013-03-07
Can someone who uses LibreOffice 3.6 installed by default with Ubuntu or installed from the PPA please post the contents of the .desktop file for LibreOffice Calc or Writer? It should be in here: /usr/share/applications.

I don't want the .desktop file if you've installed LibreOffice directly from libreoffice.org!

Thanks!

---

### Post by BlindSoothsayer on 2013-03-07
I have version 3.6.2.2 installed by default with Ubuntu.  In that directory, I have a symbolic link to /usr/lib/libreoffice/share/xdg/calc.desktop

The contents of that file are below:

```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice-calc
Type=Application
Categories=Office;Spreadsheet;
Exec=libreoffice --calc %U
MimeType=application/vnd.oasis.opendocument.spreadsheet;application/vnd.oasis.opendocument.spreadsheet-template;application/vnd.sun.xml.calc;application/vnd.sun.xml.calc.template;application/msexcel;application/vnd.ms-excel;application/vnd.openxmlformats-officedocument.spreadsheetml.sheet;application/vnd.ms-excel.sheet.macroenabled.12;application/vnd.openxmlformats-officedocument.spreadsheetml.template;application/vnd.ms-excel.template.macroenabled.12;application/vnd.ms-excel.sheet.binary.macroenabled.12;text/csv;application/x-dbf;text/spreadsheet;application/csv;application/excel;application/tab-separated-values;application/vnd.lotus-1-2-3;application/vnd.oasis.opendocument.chart;application/vnd.oasis.opendocument.chart-template;application/x-dbase;application/x-dos_ms_excel;application/x-excel;application/x-msexcel;application/x-ms-excel;application/x-quattropro;application/x-123;text/comma-separated-values;text/tab-separated-values;text/x-comma-separated-values;text/x-csv;
Name=LibreOffice Calc
GenericName=Spreadsheet
GenericName[zu]=Ikhasi lokubala
Comment=Perform calculations, analyze information and manage lists in spreadsheets by using Calc.
Comment[zu]=Perform calculations, analyze information and manage lists in spreadsheets by using Calc.
InitialPreference=5
X-Ayatana-Desktop-Shortcuts=X-New
[X-New Shortcut Group]
Name=New Spreadsheet
Name[zu]=New Spreadsheet
Exec=libreoffice --calc %U
TargetEnvironment=Unity
```

---

### Post by vasa1 on 2013-03-08
[QUOTE=BlindSoothsayer;12545661]I have version 3.6.2.2 installed by default with Ubuntu.  In that directory, I have a symbolic link to /usr/lib/libreoffice/share/xdg/calc.desktop

Thank you very much! I'm sorry I didn't thank you earlier!

I'll mark it [Solved] as soon as I can figure out how to do so.

Edit: I wanted to know the sequence of 'Name=' and 'Exec=' lines. For whatever reason, LibreOffice .desktop files have an odd order. Most .desktop files have the Name= line first.

---

### Post by BlindSoothsayer on 2013-03-08
I'm glad I could help!  I am pretty new to Ubuntu, so if you ask me to do much more than post the contents of a file, I probably won't be of much use.

---

