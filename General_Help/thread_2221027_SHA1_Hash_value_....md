---
title: "SHA1 Hash value ..."
date: 2014-04-30
forum: General Help
---

### Post by Cerberus90 on 2014-04-30
Hey guys! I start just downloading (home premium 64bit),

[http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/windows-7-download-from-digital-river-doesnt-seem/4789ffda-14d7-419c-92cf-662b56ef408c](http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/windows-7-download-from-digital-river-doesnt-seem/4789ffda-14d7-419c-92cf-662b56ef408c)

and i want to know hot to check 
 SHA1 Hash value without make any change to iso file?

Thx...

---

### Post by Vinodh Moodley on 2014-04-30
To check SHA1 in:
 
Windows
[http://support.microsoft.com/kb/889768](http://support.microsoft.com/kb/889768)

Mac:
[http://osxdaily.com/2012/02/05/check-sha1-checksum-in-mac-os-x/](http://osxdaily.com/2012/02/05/check-sha1-checksum-in-mac-os-x/)

Ubuntu:

[http://askubuntu.com/questions/61826/how-do-i-check-the-sha1-hash-of-a-file](http://askubuntu.com/questions/61826/how-do-i-check-the-sha1-hash-of-a-file)

---

### Post by claracc on 2014-04-30
> **Cerberus90 said:**
> Hey guys! I start just downloading (home premium 64bit),

[http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/windows-7-download-from-digital-river-doesnt-seem/4789ffda-14d7-419c-92cf-662b56ef408c](http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/windows-7-download-from-digital-river-doesnt-seem/4789ffda-14d7-419c-92cf-662b56ef408c)

and i want to know hot to check 
 SHA1 Hash value without make any change to iso file?

Thx...

I think you would obtain better answers in a windows forum, but from the link you provide, it states:

"1) After downloading the correct .iso file install HashCalc and validate the SHA1 hash value
is correct. If the download is not corrupt, the value HashCalc returns will match the SHA1 value I posted.
HashCalc: http://www.slavasoft.com/hashcalc/index.htm"

So, follow the instructions, install the program, run it and compare with the number provided by the download.

---

### Post by SeijiSensei on 2014-04-30
In Linux you can use the sha1sum command from the prompt:
```
sha1sum < /path/to/the/file.iso
```

---

