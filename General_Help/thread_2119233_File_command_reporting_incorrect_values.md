---
title: "File command reporting incorrect values"
date: 2013-02-23
forum: General Help
---

### Post by bkline on 2013-02-23
Has anyone else noticed that the [FONT="Courier New"]file[/FONT] command in Ubuntu is reporting the wrong file type for some Excel spreadsheets?
```
$ file -i foobar.xls 
foobar.xls: application/msword; charset=binary
```

---

### Post by Doug S on 2013-02-23
Yes. Some example output (both right and wrong and no information):```
doug@doug-64:~/backup_doug_xps/house$ file -i 682bud_zero.xls
682bud_zero.xls: ; charset=binary
doug@doug-64:~/backup_doug_xps/house$ file 682bud_zero.xls
682bud_zero.xls: Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, Code page: 1252, Author: D Smythies, Last Saved By: Doug Smythies, [COLOR=red]Name of Creating Application: Microsoft Excel[/COLOR], Last Printed: Fri Mar 14 22:41:54 1997, Create Time/Date: Wed Oct 16 02:03:50 1996, Last Saved Time/Date: Wed Jul 10 00:25:24 2002, Security: 0
doug@doug-64:~/backup_doug_xps/test/restore$ file 2007_totals.xls
2007_totals.xls: Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.1, Code page: 1252, Last Saved By: dsmythies, Last Printed: Tue Mar 11 21:45:52 2008, Create Time/Date: Mon Mar  3 00:05:16 2008, Last Saved Time/Date: Sun Mar 23 02:51:36 2008, Security: 0
doug@doug-64:~/backup_doug_xps/test/restore$ file -i 2007_totals.xls
2007_totals.xls: [COLOR=red]application/msword[/COLOR]; charset=binary
doug@doug-64:~/backup_doug_xps/test/restore$ file -i z1.xls
z1.xls: [COLOR=red]application/msword[/COLOR]; charset=binary
doug@doug-64:~/backup_doug_xps/test/restore$ file z1.xls
z1.xls: Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.1, Code page: 1252, Last Saved By: dsmythies, Create Time/Date: Wed Jun  4 01:19:10 2008, Last Saved Time/Date: Wed Jun  4 19:46:06 2008, Security: 0
doug@doug-64:~/backup_doug_xps/temp/temp/temp/temp/temp$ file ave_data.xlsx
ave_data.xlsx: [COLOR=red]Microsoft Excel 2007+[/COLOR]
doug@doug-64:~/backup_doug_xps/temp/temp/temp/temp/temp$ file -i ave_data.xlsx
ave_data.xlsx: [COLOR=red]application/vnd.ms-excel[/COLOR]; charset=binary

```

---

### Post by prodigy_ on 2013-02-23
Try **mimetype**, maybe you'll get better results.

```
$ file -i foobar.doc
foobar.doc: ; charset=binary

$ sudo apt-get install libfile-mimeinfo-perl
...
$ mimetype foobar.doc                     
foobar.doc: application/msword

$ file -i sample.xls 
sample.xls: application/msword; charset=binary
$ mimetype sample.xls           
sample.xls: application/vnd.ms-excel
```

---

### Post by bkline on 2013-02-23
> **prodigy_ said:**
> Try **mimetype**, maybe you'll get better results.
Thanks for the suggestion.  However that command is just a Perl script which looks up the MIME type based on the filename extension.```
$ echo foobar > bogus.xls
$ mimetype bogus.xls
bogus.xls: application/vnd.ms-excel

```For a web app which is trying to guard against users trying to get around restrictions on allowable file types, that won't be sufficient.  The [FONT="Courier New"]file[/FONT] command is determining (or claims to determine) the MIME type based on the actual file contents.  It's just giving the wrong answer for some valid Excel files.

---

### Post by prodigy_ on 2013-02-23
> **bkline said:**
> The [FONT="Courier New"]file[/FONT] command is determining (or claims to determine) the MIME type based on the actual file contents.
Not exactly. It can read metadata and it uses magic numbers from **/usr/share/file/magic.mime** database to guess mime types. You can trust it most of the time.

The rest depends on your project requirements. If you really need to know what's inside, you're going to have a lot of fun writing import filters for every file type on your whitelist.

---

### Post by bkline on 2013-02-23
> **prodigy_ said:**
> Not exactly. It can read metadata and it uses magic numbers from **/usr/share/file/magic.mime** database to guess mime types.
Not sure what you mean by "not exactly"; what can it be doing with those "magic numbers" if it's not comparing them with the bytes it finds in the file (which, in this context, is what I mean by the "file contents")?

> If you really need to know what's inside, you're going to have a lot of fun writing import filters for every file type on your whitelist.
I don't need to know what data is in the spreadsheet.  I just need to know that it's a spreadsheet, if that's what it actually is.  Telling the user that his or her file won't be accepted on the grounds that it's not an Excel file, when in fact it really is a perfectly valid Excel file is pretty dreadful behavior.  On the other hand trusting the file extension isn't much better.  It often happens that users right-click on a web link, and select "save as ..." providing a file name that matches what they assume the downloaded bytes will be, when in fact those bytes represent an intermediate HTML page on the way to the actual file retrieval.  Simply storing the result with the mime type for Excel workbook will result in trouble reports from subsequent users who are trying to retrieve and view the file unsuccessfully because the application launched on the user's workstation based on these assumptions doesn't know what to do with what it gets.  Does this help clarify the problem I'm trying to describe?  I don't want to be told that an Excel file is a Microsoft Word document when it isn't.

---

