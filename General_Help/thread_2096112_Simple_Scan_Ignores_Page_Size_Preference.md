---
title: "Simple Scan Ignores Page Size Preference"
date: 2012-12-19
forum: General Help
---

### Post by Ralph L on 2012-12-19
I am using Simple Scan 3.4.1 on my HP Photosmart c6180 all-in-one printer, fax, scanner using Ubuntu 12.04.1 Precise Pangolin.  It works fine except that it always scans in legal 8.5X14 paper size.  I can set the Preference for 8.5x11, but this setting is ignored.  

Does anybody know how to fix this problem?  Does the Simple Scan 3.6.0 fix the problem?  If so, does anybody know how to install Simple Scan 3.6.0?  When I try to do the "configure", I get the error listed below.

Thanks in advance.
Ralph
```
checking for SIMPLE_SCAN... no
configure: error: Package requirements (
    gtk+-3.0
    gmodule-export-2.0
    gthread-2.0
    zlib
    cairo
    gdk-pixbuf-2.0
    gudev-1.0
) were not met:

No package 'gtk+-3.0' found
No package 'cairo' found
No package 'gdk-pixbuf-2.0' found
No package 'gudev-1.0' found
```

---

### Post by Ralph L on 2013-01-13
I didn't put in the effort to try simple-scan 3.6.0, but I did find a far from perfect, but better than nothing, work-around to simple scan's ignoring page size preference.  If you just have a single page to scan, put it on the glass or in the feeder, click Document>New, and then click the Scan button.  Then go to Page>Crop> and select the document size.  Then go to the window with the scanned item in it and drag the crop frame up to the top (or wherever you want it) of the scanned page. Then click the save button to save the document.

If you have a multi-page document put it in the feeder and click Document>New.  Then click Page>Crop> and select the paper size.  Go to the scan window and drag the crop frame to the top (or wherever), pull down the arrow to the right of the Scan button, and select "Scan All Pages From the Feeder".  Now all pages will have the same cropping.  Save the document.  

If you have a multi-page document and no feeder, do the same as above, setting the crop frame before scanning, and then do the scanning manually putting documents on the glass.  Don't select Document>New between pages or you will not get a multi-page document.

Hope this helps somebody.

Note that the Crop button doesn't allow crop size selection.  Therefore, you always need to use Page>Crop.

---

### Post by HughR on 2013-01-28
Simplescan is infuriating.  Its interface is pretty good for me, the casual user.  Sure, there could be improvements, but it is much easier than xsane!

On the other hand, it is unbelievably buggy.  I don't know how many times it has simply crashed on me, usually a few pages into a job.

Right now I'm frustrated because it doesn't let me scan a legal sized document.  I set the preference to "legal" and it gives me letter.  I set the preference to "automatic" and it gives me letter.  I don't see how to crop a letter-sized image into a legal one, with all the missing bits!

My scanner is well supported: a Fujitsu fi-6130.

I've had similar problems with Simplescan on Fedora with a different scanner.  I don't remember if they were identical.

Anyone suggest a better choice than Simplescan or xsane?  Perhaps a cookbook for navigating xsane's interface would be enough.

---

### Post by HughR on 2013-02-04
This problem is probably related to [http://ubuntuforums.org/showthread.php?p=9310891]("http://ubuntuforums.org/showthread.php?p=9310891")

---

