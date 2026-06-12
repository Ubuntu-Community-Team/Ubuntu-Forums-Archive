---
title: "Is it possible to split a LibreOffice Impress file into smaller functional files?"
date: 2013-07-15
forum: General Help
---

### Post by vasa1 on 2013-07-15
I got a biggish LibreOffice Impress file ([http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/PythonAB/files/PythonAB.odp;](http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/PythonAB/files/PythonAB.odp;) ~7.2 MB). Is it possible to break it up into smaller pieces? Opening the full file takes a while. I have no experience with Impress.

There's a pdf version as well ([http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/PythonAB/files/handout.pdf](http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/PythonAB/files/handout.pdf)) which is easy to split but the Impress version looks better.

---

### Post by Buntu Bunny on 2013-07-15
I don't know about splitting Impress files, but is it possible to split the pdf into smaller files with [PdfShuffler]("http://sourceforge.net/projects/pdfshuffler/")?

---

### Post by vasa1 on 2013-07-15
> **Buntu Bunny said:**
> I don't know about splitting Impress files, but is it possible to split the pdf into smaller files with [PdfShuffler]("http://sourceforge.net/projects/pdfshuffler/")?
I have no problem with splitting pdf files. For that I follow [http://askubuntu.com/questions/195037/is-there-a-tool-to-split-a-book-saved-as-a-single-pdf-into-one-pdf-per-chapter/195044#195044](http://askubuntu.com/questions/195037/is-there-a-tool-to-split-a-book-saved-as-a-single-pdf-into-one-pdf-per-chapter/195044#195044)

---

### Post by Cheesehead on 2013-07-15
> **vasa1 said:**
> I got a biggish LibreOffice Impress file ([http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/PythonAB/files/PythonAB.odp;](http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/PythonAB/files/PythonAB.odp;) ~7.2 MB). Is it possible to break it up into smaller pieces? Opening the full file takes a while. I have no experience with Impress.

Splitting the file is easy. The file is simply a zipped set of xml files.

Let's take a look at the contents of the file:
```
me@system:/~$ unzip -l PythonAB.odp   # -l flag means 'list the zipfile contents' 
Archive:  PythonAB.odp
  Length      Date    Time    Name
---------  ---------- -----   ----
       47  2013-05-23 13:51   mimetype
     7421  2013-05-23 13:51   Thumbnails/thumbnail.png
     1091  2013-05-23 13:51   meta.xml
  2630006  2013-05-23 13:51   content.xml
  1004004  2013-05-23 13:51   Pictures/100002010000021A000003963571825F.png
     7007  2013-05-23 13:51   Pictures/10000000000001130000005F310067D4.png
    26870  2013-05-23 13:51   Pictures/1000020100000173000001C18B2EE4BC.png
   252483  2013-05-23 13:51   Pictures/10000201000005B10000061522878AA4.png
    14295  2013-05-23 13:51   Pictures/10000201000000FA000000CEEFE9D816.png
   198170  2013-05-23 13:51   Pictures/100000000000067E00000604A0A38B8B.jpg
   197286  2013-05-23 13:51   Pictures/100000000000067E00000604822E4623.jpg
   222270  2013-05-23 13:51   Pictures/100000000000067E000006047B0BDC64.jpg
   199826  2013-05-23 13:51   Pictures/100000000000067E000006048C56466E.jpg
   220135  2013-05-23 13:51   Pictures/100000000000067E0000060483D0B393.jpg
    79795  2013-05-23 13:51   Pictures/10000000000001E2000000ED7C37E2FF.jpg
   178843  2013-05-23 13:51   Pictures/1000000000000428000002B8C11CD3B0.jpg
    33069  2013-05-23 13:51   Pictures/10000000000001F400000146C5F79C73.jpg
   274618  2013-05-23 13:51   Pictures/1000000000000428000002B874F656ED.jpg
   217156  2013-05-23 13:51   Pictures/100000000000067E0000060456C56BF3.jpg
   175449  2013-05-23 13:51   Pictures/1000000000000428000002B84CD26539.jpg
    29118  2013-05-23 13:51   Pictures/2000003700004C1B000013FB2A632D1A.svm
    52309  2013-05-23 13:51   Pictures/1000000000000298000002203F438643.jpg
   277997  2013-05-23 13:51   Pictures/1000000000000428000002B8B13A7F4F.jpg
    21579  2013-05-23 13:51   Pictures/100000000000012000000090668EC6C2.jpg
     3863  2013-05-23 13:51   Pictures/100000000000007A000000341164862A.jpg
    83496  2013-05-23 13:51   Pictures/1000000000000140000002803C33AC16.jpg
   175847  2013-05-23 13:51   Pictures/10000000000002570000021484C980E7.jpg
    19642  2013-05-23 13:51   Pictures/2000000700004966000044B36C4738B1.svm
    60344  2013-05-23 13:51   Pictures/200000BB000012DE000012DEA8877A76.svm
     1821  2013-05-23 13:51   Pictures/10000000000000E10000003E22ACBC2F.gif
    56630  2013-05-23 13:51   Pictures/1000020100000654000001DF7D4A0A50.png
   132944  2013-05-23 13:51   Pictures/1000020100000C5D00000397C0A4C213.png
    17618  2013-05-23 13:51   Pictures/2000002B000023D400000C672D6A7CBD.svm
   206917  2013-05-23 13:51   Pictures/100000000000067E000006043660AE74.jpg
  1883709  2013-05-23 13:51   Pictures/10000000000005EB0000084FFA05FCEC.jpg
      859  2013-05-23 13:51   Pictures/10000000000000200000002000309F1C.png
    33506  2013-05-23 13:51   Pictures/100000000000033E000001F9C1116CB2.jpg
    70376  2013-05-23 13:51   Pictures/100002010000067E00000604741CC2E2.png
   129556  2013-05-23 13:51   Pictures/10000000000001D9000002778F70ED4A.jpg
   226318  2013-05-23 13:51   Pictures/100000000000067E00000604312A35C8.jpg
   196383  2013-05-23 13:51   Pictures/100000000000067E000006043383FF2E.jpg
    84145  2013-05-23 13:51   Pictures/100000000000014000000280E36CFB49.jpg
    58677  2013-05-23 13:51   styles.xml
        0  2013-05-23 13:51   Configurations2/accelerator/current.xml
        0  2013-05-23 13:51   Configurations2/floater/
        0  2013-05-23 13:51   Configurations2/menubar/
        0  2013-05-23 13:51   Configurations2/toolbar/
        0  2013-05-23 13:51   Configurations2/progressbar/
        0  2013-05-23 13:51   Configurations2/toolpanel/
        0  2013-05-23 13:51   Configurations2/popupmenu/
        0  2013-05-23 13:51   Configurations2/images/Bitmaps/
        0  2013-05-23 13:51   Configurations2/statusbar/
        0  2013-05-23 13:51   Object 1/Configurations2/menubar/
        0  2013-05-23 13:51   Object 1/Configurations2/floater/
        0  2013-05-23 13:51   Object 1/Configurations2/toolbar/
        0  2013-05-23 13:51   Object 1/Configurations2/progressbar/
        0  2013-05-23 13:51   Object 1/Configurations2/statusbar/
        0  2013-05-23 13:51   Object 1/Configurations2/images/Bitmaps/
        0  2013-05-23 13:51   Object 1/Configurations2/popupmenu/
        0  2013-05-23 13:51   Object 1/Configurations2/toolpanel/
        0  2013-05-23 13:51   Object 1/Configurations2/accelerator/current.xml
      696  2013-05-23 13:51   Object 1/content.xml
     6696  2013-05-23 13:51   Object 1/settings.xml
     9923  2013-05-23 13:51   settings.xml
     2191  2013-05-23 13:51   ObjectReplacements/Object 1
     6420  2013-05-23 13:51   META-INF/manifest.xml
---------                     -------
  9789421                     66 files

```

Most of the file is images. A few large JPEGs (one is 1.8MB!) and others.
Each time the file is opened, LibreOffice must read every one of those images, and then scale each image to the display size - that's a a vast amount of wasted effort, and causes much more delay than reading from disk.

Instead of splitting, consider resizing a few of the larger images in the zipfile to match the display size. You should see an immediate improvement.

---

### Post by vasa1 on 2013-07-15
@Cheesehead, thanks for responding!

I think I wasn't clear about  what I meant by "splitting". That Impress file has 431 slides. I was wondering if there was a way to have, say, 10 new impress files with ~ 40 slides. As you explained, loading the whole file does get my laptop all excited for a while.

But could you explain what you mean by "consider resizing a few of the larger images in the zipfile to match the display size"? What display size are you referring to? And what program is to be used for achieving the resizing? I'm not good at using things like the GIMP.

---

### Post by coldraven on 2013-07-15
Open the file in Impress. Select the tab "Slide Sorter", select how many slides you want, right click "Cut".
Then File>New Presentation>Paste. Then name it "part1" and Close
Repeat

---

### Post by vasa1 on 2013-07-15
> **coldraven said:**
> Open the file in Impress. Select the tab "Slide Sorter", select how many slides you want, right click "Cut".
Then File>New Presentation>Paste. Then name it "part1" and Close
Repeat
Thank You! That works very well. Marking this as "Solved".

---

