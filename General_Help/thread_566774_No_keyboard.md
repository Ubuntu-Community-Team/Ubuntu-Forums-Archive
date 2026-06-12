---
title: "No keyboard"
date: 2007-10-03
forum: General Help
---

### Post by flower199 on 2007-10-03
Hey people, this is my first post here + first time with linux :D

Since the Live CD my keyboard hasn't worked. I managed to choose a user name and password using Open Office Writer and choosing Insert>Special caracter and copy+pasting it into the box.

I have a Logitec MX Revolution mouse and a Logitech PS-2 keyboard. I have tried another PS-2 keyboard and having a PS-2 mouse instead of cordless USB but had no luck. PC in question is in my signature.

Any help as to where to start looking would be much appreciated, as I can't sign into my new distro!!

---

### Post by p_quarles on 2007-10-03
> **flower199 said:**
> I managed to choose a user name and password using Open Office Writer and choosing Insert>Special caracter and copy+pasting it into the box.
This is kind of confusing. Are you saying that the keyboard works in OpenOffice, but not in other programs?

---

### Post by flower199 on 2007-10-03
> **p_quarles said:**
> This is kind of confusing. Are you saying that the keyboard works in OpenOffice, but not in other programs?

Nope, like [this]("http://latlcui.unige.ch/phonetique/fonts/preview_insert_special_characters.png"), I selected the caracters and then inserted them onto the page, cut and copied it.

My key board just doesn't show up. The num-lock key stays on and I can't caps-lock or get anything else to light up.

Could it be that it wants a USB one??

---

### Post by p_quarles on 2007-10-03
Okay, I get it: you were using the mouse. :D Well, at least that works.

I'm not sure what to tell you, but I can tell you that this is an extremely unusual problem. Keyboard support in Linux is nearly perfect. Because of that, I wonder if there's possibly a problem with the disk that you used to install. 

Both of the following problems are pretty common:
1) The .iso image gets corrupted during the download process
2) The .iso gets corrupted during the write-to-disk process.

The first problem can be solved by checking the MD5 hash after you've downloaded the file. The second can be minimized by burning the disk at a very low speed (~4x).

---

### Post by flower199 on 2007-10-03
> **p_quarles said:**
> Okay, I get it: you were using the mouse. :D Well, at least that works.

I'm not sure what to tell you, but I can tell you that this is an extremely unusual problem. Keyboard support in Linux is nearly perfect. Because of that, I wonder if there's possibly a problem with the disk that you used to install. 

Both of the following problems are pretty common:
1) The .iso image gets corrupted during the download process
2) The .iso gets corrupted during the write-to-disk process.

The first problem can be solved by checking the MD5 hash after you've downloaded the file. The second can be minimized by burning the disk at a very low speed (~4x).

The disk I used was burned @ x4. How can I check the MD5 hash, with the live CD? I think I saw an option for checking the CD's contents at the Live CD boot menu?

Thanks for your help so far though.

---

### Post by p_quarles on 2007-10-03
> **flower199 said:**
> The disk I used was burned @ x4. How can I check the MD5 hash, with the live CD? I think I saw an option for checking the CD's contents at the Live CD boot menu?

Thanks for your help so far though.
Yes, there is an option to check disk integrity during the boot process. Running that can be useful, too, but it takes more time than checking the MD5 sum.

Here are the official instructions for checking the MD5 sum for Ubuntu downloads:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Check the file that you downloaded. If the numbers don't match, it means the download was corrupted.

---

### Post by flower199 on 2007-10-03
> **p_quarles said:**
> Yes, there is an option to check disk integrity during the boot process. Running that can be useful, too, but it takes more time than checking the MD5 sum.

Here are the official instructions for checking the MD5 sum for Ubuntu downloads:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Check the file that you downloaded. If the numbers don't match, it means the download was corrupted.

I will look into that thanks, I'll post back if I have any issues :)

EDIT : It seems my problem could be solved [link]("http://www.linuxquestions.org/questions/showthread.php?t=563962"). Aparently it doesn't want PS-2 :/

---

