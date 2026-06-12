---
title: "How to unzip 2gb+ zip file? [Most annoying Linux issue]"
date: 2012-12-01
forum: General Help
---

### Post by altjx on 2012-12-01
This has to be one of the most annoying issues yet that I've run into on Linux.

I have just downloaded a .zip file which is approximately 2.5GB and I cannot unzip it for nothing in the world. I've been spending over an hour on just doing this what should be simple task!

```
alt0n@h4x:~/Downloads/BT5R3-GNOME-32-VM$ gunzip BT5R3-GNOME-32-VM.zip
gzip: BT5R3-GNOME-32-VM.zip: unknown suffix -- ignored

```

```
alt0n@h4x:~/Downloads/BT5R3-GNOME-32-VM$ unzip BT5R3-GNOME-32-VM.zip 
Archive:  BT5R3-GNOME-32-VM.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of BT5R3-GNOME-32-VM.zip or
        BT5R3-GNOME-32-VM.zip.zip, and cannot find BT5R3-GNOME-32-VM.zip.ZIP, period.
```

```
alt0n@h4x:~/Downloads/BT5R3-GNOME-32-VM$ p7zip BT5R3-GNOME-32-VM.zip -d
/usr/bin/p7zip: BT5R3-GNOME-32-VM.zip: unknown suffix -- ignored
alt0n@h4x:~/Downloads/BT5R3-GNOME-32-VM$ md5sum BT5R3-GNOME-32-VM.zip 
bca6d3862c661b615a374d7ef61252c5  BT5R3-GNOME-32-VM.zip

```

```
alt0n@h4x:~/Downloads/BT5R3-GNOME-32-VM$ file BT5R3-GNOME-32-VM.zip 
BT5R3-GNOME-32-VM.zip: 7-zip archive data, version 0.3
alt0n@h4x:~/Downloads/BT5R3-GNOME-32-VM$ zip
Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
Zip 3.0 (July 5th 2008). Usage:

```

It's the same MD5 as the one posted on the original site, it works on a Windows system at work... I just have no idea why this can't be as simple as extracting it like anything else.

Would really appreciate someone helping me save another 2+ hours of my life trying to unzip this file.

Thanks.

---

### Post by 3rdalbum on 2012-12-01
> **altjx said:**
> 

```
alt0n@h4x:~/Downloads/BT5R3-GNOME-32-VM$ p7zip BT5R3-GNOME-32-VM.zip -d
/usr/bin/p7zip: BT5R3-GNOME-32-VM.zip: unknown suffix -- ignored

```

```
alt0n@h4x:~/Downloads/BT5R3-GNOME-32-VM$ file BT5R3-GNOME-32-VM.zip 
BT5R3-GNOME-32-VM.zip: 7-zip archive data, version 0.3
```


There's your answer: It's a 7zip archive, but when you use p7zip it says "I don't understand files with the '.zip' suffix".

Rename the file to end with .7z and it will work in p7zip.

The reason it works on Windows is because the 7zip program in Windows is a full archive manager with its own support for a whole range of different archives. The Windows software understands ordinary Zip archives, and when it tries to open this file as a .zip it is smart enough to treat it as the file it really is. The Linux program only knows .7z so won't even attempt to open a file with the wrong extension.

Having said that, I find it dumb that Linux software seems to be dependent on filename suffixes - this isn't Windows! What's next, drive letters?!

---

### Post by altjx on 2012-12-01
> **3rdalbum said:**
> There's your answer: It's a 7zip archive, but when you use p7zip it says "I don't understand files with the '.zip' suffix".

Rename the file to end with .7z and it will work in p7zip.

The reason it works on Windows is because the 7zip program in Windows is a full archive manager with its own support for a whole range of different archives. The Windows software understands ordinary Zip archives, and when it tries to open this file as a .zip it is smart enough to treat it as the file it really is. The Linux program only knows .7z so won't even attempt to open a file with the wrong extension.

Having said that, I find it dumb that Linux software seems to be dependent on filename suffixes - this isn't Windows! What's next, drive letters?!

Haha, drive letters. Seriously. I'm glad I'm not the only one who thinks this is absolutely stupid the way this is done. I'm in the process of copying the file over again since I accidentally deleted it. I can't believe this has been the reason all this time! >_< Thank you for your help! I am convinced that it will work now :)

---

### Post by altjx on 2012-12-01
And it worked! Thank you man! Spent so much time on this and got a headache over this annoying issue. Glad to finally have it going :)

---

### Post by dcstar on 2012-12-01
> **altjx said:**
> And it worked!

Then MARK the thread!

---

