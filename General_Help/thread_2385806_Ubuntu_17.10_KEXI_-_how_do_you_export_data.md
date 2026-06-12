---
title: "Ubuntu 17.10 KEXI - how do you export data?"
date: 2018-02-25
forum: General Help
---

### Post by PopsTheSailor on 2018-02-25
I have a database I built in Kexi but haven't used for several months. When I tried to open it, I had some issues with Kexi and decided that I want my data in LibreOffice Calc (or some other non MS spreadsheet). In reading the old Kexi manuals you are supposed to be able to open a table, then click on the External Data tab and then export the data. That option is not there. 

Does anyone know how to export out of Kexi? Or even open the spreadsheet app and import the data?

Ubuntu 17.10
Kexi 3.0.2 installed using Synaptic

---

### Post by vasa1 on 2018-02-25
I don't know anything about *kexi* but is it possible that installing some of the "suggests" may help?

```
The following additional packages will be installed:
  kexi-data libkdb-data libkdb3-3 libkdb3-driver-sqlite libkproperty-data libkpropertycore3-3 libkpropertywidgets3-3 libkreport-data libkreport3-3
Suggested packages:
  **kexi-mysql-driver kexi-postgresql-driver kexi-web-form-widget**
```

---

### Post by PopsTheSailor on 2018-02-25
Hum???? I can try but I don't know postgress or mysql but maybe it will give me other options if I install those. Now sure about the web-form widget. I'll install all of them and see.

---

### Post by PopsTheSailor on 2018-02-27
For anyone that stumbles across this thread looking for a solution, you now right click on the table and the export option shows up although i could never get it to work. I found another crazy way to get my data. I'm shutting down using Kexi and will put it into a spreadsheet instead.

---

### Post by burobaaje2 on 2018-10-09
I have not been able to get any information on how to export CSV files from Kexi.  Some documentation shows a picture  File export, but I have not seen it in the actual app.  Maybe the picture is from the windows version.  I have tried it in ubuntu and kubuntu and does not look anthing like their picture.  Right clicking a table does show a export option, but I also have not been able to get it to work.

It is easy to import a CSV file to a table.  Make sure the first line of the CSV file has the field names.  Open the CSV file in a plain text processor, copy the entire file, select Data from Kexi menu, then Paste Special.  You will see a window with the the data you copied from CSV file and you need to select the delimiter.  I have only used CSV files but I presume you could use TAB delimited files as well.  This is the only way I have ever been able to import data into Kexi.

From my experience Kexi in ubuntu and kubuntu crashes easily.  But after using you learn what makes it crash and can avoid them.

---

### Post by oldos2er on 2018-10-09
Closing since 17.10 is no longer supported; anyone with questions should start a new thread.

---

