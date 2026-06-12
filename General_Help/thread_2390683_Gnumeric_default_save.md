---
title: "Gnumeric default save"
date: 2018-05-01
forum: General Help
---

### Post by kakashi_12 on 2018-05-01
Don't won't to install Libre Office or Open Office if I don't have to.
Since Gnumeric comes installed.
How do I change the default save as to .xls extension?

I figured it out for AbiWord.

---

### Post by delfiler on 2018-05-01
so if i am reading this right you already found the solution or do you still need the solution? cause that last part is a bit confusing as it indicates that you already know what to do

---

### Post by jbrefort on 2018-05-02
This is not recommended because the .xls format is not fully compatible with gnumeric and .xls files are almost impossible to recover  if something goes wrong. .xlsx or .ods are better, but still not the best. The only fully compatible format is .gnumeric.

Anyway, it is possible to change the default format. You need to manually edit the appropriate plugin.xml (as root if gnumeric was installed systemwide, but this will impact other users if any) and change the line:
<service type="file_saver" overwrite_files="TRUE" mime_type="application/vnd.ms-excel" id="excel_biff8" format_level="auto" file_extension="xls" default_saver_priority="1">
to
<service type="file_saver" overwrite_files="TRUE" mime_type="application/vnd.ms-excel" id="excel_biff8" format_level="auto" file_extension="xls" default_saver_priority="60">
(any value larger than 50 should work).

---

### Post by kakashi_12 on 2018-05-02
@delfiler, no I didn't find the solution.
That's an alternative.

@jbrefort, thanks for your help. That worked.

---

