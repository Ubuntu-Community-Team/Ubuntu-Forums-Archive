---
title: "How to recover an odp (Libreoffice Impress)"
date: 2022-08-25
forum: General Help
---

### Post by cigtoxdoc on 2022-08-25
When I went to open an odp file I had been working on before shutting down my PC, Libreoffice tells me the file is corrupt.  When I try the LibreOffice recovery procedure, it returns a blank presentation.  My fault in not having backup time set.  Nothing I cannot go back to where I was starting from (I was modifying an existing presentation) and redo the first couple of slides, but this is first time I had LibreOffice file go corrupt.  Partition is exfat.

Thank you,

John

---

### Post by Holger_Gehrke on 2022-08-25
If you still have the damaged file, there are things you can try. All the OpenDocument files are actually zip-archives containing xml, css, and some other files. First try 'unzip -t file.odp' (substitute path and name of the file for 'file.odp). This will tell you if the zip compression is ok and if the files inside the zip are okay. The files can be compressed ok but still not right; one typical error I've encountered multiple times in the past were malformed XML files which had two instances of the same attribute on one tag. If the archive is okay, unzip it's contents into a new, empty directory. To find malformed XML files you can use xmllint from the package libxml2-utils on the files. Alternatively if you're using emacs you can just load an xml file into emacs and use ctrl-c ctrl-n to jump from one error to the next (emacs does have a schema for Open Document files but it's out of date, so there will be a lot of stuff emacs sees as wrong; 'attribute not allowed' and 'attribute value invalid' can probably be disregarded). Once you've found and fixed the errors you can zip everything back together, rename the zip file to odp and try to load it into LibreOffice.

Holger

---

### Post by cigtoxdoc on 2022-08-25
Thank you very much.  Output of unzip -t follows.  How do I deal with "bad zipfile offset"?  I took an existing odp file, changed the first file and then added a few new slides
john@john-Precision-7720:~/Documents$ unzip -t 75TSRC139.odp
Archive:  75TSRC139.odp
    testing: mimetype                 OK
file #2:  bad zipfile offset (local header sig):  85
file #3:  bad zipfile offset (local header sig):  139
file #4:  bad zipfile offset (local header sig):  195
file #5:  bad zipfile offset (local header sig):  249
file #6:  bad zipfile offset (local header sig):  307
file #7:  bad zipfile offset (local header sig):  363
file #8:  bad zipfile offset (local header sig):  421
file #9:  bad zipfile offset (local header sig):  477
file #10:  bad zipfile offset (local header sig):  538
file #11:  bad zipfile offset (local header sig):  592
file #12:  bad zipfile offset (local header sig):  1489
    testing: Pictures/TablePreview5.svm   OK
    testing: Pictures/1000000000000623000009AC9BCBA073277EB3AD.jpg   OK
    testing: Pictures/100000010000029E000002496721FDD3CD6C7CC9.png   OK
    testing: Pictures/1000000000000343000002A3788428706156F52A.jpg   OK
    testing: Pictures/1000000000000649000004AED0B9BE4DEF455D5E.png   OK
    testing: Pictures/1000000000000393000002EA91ECD2DFC83E61BF.jpg   OK
    testing: Pictures/10000001000003F0000002F41ED317798767FC49.png   OK
    testing: Pictures/TablePreview1.svm   OK
    testing: Pictures/10000000000003F0000002F4FC81A3589E50D01A.jpg   OK
    testing: Pictures/TablePreview2.svm   OK
    testing: Pictures/100000000000018F00000261E690BB094EE1658A.jpg   OK
    testing: Pictures/TablePreview3.svm   OK
    testing: Pictures/10000000000006300000056B4079858E95EF75A8.jpg   OK
    testing: Pictures/10000000000003F0000002F4B8BB57EB1FFECAB3.jpg   OK
    testing: settings.xml             OK
    testing: Thumbnails/thumbnail.png   OK
    testing: meta.xml                 OK
    testing: META-INF/manifest.xml    OK
    testing: content.xml              OK
    testing: styles.xml               OK
At least one error was detected in 75TSRC139.odp.
john@john-Precision-7720:~/Documents$

---

### Post by cigtoxdoc on 2022-08-25
I took the content.xml file, opened it in Firefox, and it gave me the text for each file.  That is what I needed.  John

---

### Post by Holger_Gehrke on 2022-08-25
If the zip archive is broken, then you're out of luck. You could try repairing the file with 'zip -F file.odp -o filefix.odp' or 'zip -FF file.odp -o filefixfix.odp'. Read the man page for zip (man zip) for details, they are probably important. As far as I can tell you're missing the manifest.rdf, Pictures/TablePreview4.svm - unless there is no Table4 - and the directory Configuration2 and the - usually empty - directories inside it: accelerator, floater, images, images/Bitmaps, menubar, popupmenu,progressbar, statusbar, toolbar, and toolpanel. If 'zip' can't reconstruct the file, you can try unpacking it, getting the manifest.rdf from another odp file (it should be boilerplate, usually the same for all files) and creating the directory structure in Configurations2 and zipping the whole thing up again.

Holger

---

### Post by mIk3_08 on 2022-08-26
> **cigtoxdoc said:**
> I took the content.xml file, opened it in Firefox, and it gave me the text for each file.  That is what I needed.  John

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

