---
title: "Not overwrite files on 2nd drive"
date: 2018-08-02
forum: General Help
---

### Post by raleigh3 on 2018-08-02
Today I had a situation where I could not boot up. I used Clonezilla to restore a 2 day old image.


  So my script which is in Autostart copied the zip files(July 31) from my main drive to my second drive.
And overwrote my files which were from Aug. 2.

  
I lost a lot of work.

  
Is there anything I can change in my script to prevent that again?

  
I think I need to compare the file date of Ubuntu_Documents.zip in sda1 with that of the one in sdb1.
And then decide whether to copy or not.

  
This is part of my backup script.      

  ```
 cd ~/Documents
 zip -u -q Ubuntu_Documents.zip *.txt *.doc *.rtf *.html *.png *.pdf *.odt *.ods *.odg 
 cp -u -f Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
```

---

### Post by HermanAB on 2018-08-03
Replace the cp command with rsync.  It has many more options to control the copying.

---

