---
title: "Can't run zip."
date: 2013-04-18
forum: General Help
---

### Post by Roxbury on 2013-04-18
Trying to run Dark Comet on Ubuntu 12.04.

After I do

unzip file.zip

It finishes, but then I can't open the exe. I get this error: 

Archive:  /home/j/Downloads/DarkComet.exe
[/home/j/Downloads/DarkComet.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/j/Downloads/DarkComet.exe or
          /home/j/Downloads/DarkComet.exe.zip, and cannot find /home/j/Downloads/DarkComet.exe.ZIP, period.

What's wrong? I appreciate help.

---

### Post by slickymaster on 2013-04-18
The problem is exactly what it says. Unzip can't find the line of code that signals the end of the archive, so either the archive is corrupt or it is not a .zip archive.
One other thing, the program you're trying to unzip has a **.exe** extension, which tell us that is made for Windows, so you need Wine to run it.

---

### Post by Impavidus on 2013-04-18
Ubuntu tries opening .exes using an archive program because the only .exes it can open are self-extracting archives (I presume). This seems to be an ordinary windows program. Wine may be able to run it, but don't put your money on it.

---

