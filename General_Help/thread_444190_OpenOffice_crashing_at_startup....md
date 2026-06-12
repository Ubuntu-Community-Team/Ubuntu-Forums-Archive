---
title: "OpenOffice crashing at startup..."
date: 2007-05-15
forum: General Help
---

### Post by Iceman2980 on 2007-05-15
Hi guys,

I'm a newbie and running feisty, I've had a few problems but looking thorough this forum I've been able to solve them all apart from this one.

When loading openoffice, the splash screen appears then nothing. With the help of other posts I've managed to get the following error information.

/usr/lib/openoffice/program/soffice.bin: error while loading shared libraries: /usr/lib/openoffice/program/libi18nisolang1gcc3.so: invalid ELF header

** (process:16954): WARNING **: Unknown error forking main binary / abnormal early exit ...


does anyone have any ideas on how to fix this?

Any help gratefully recieved.

Thanks

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

