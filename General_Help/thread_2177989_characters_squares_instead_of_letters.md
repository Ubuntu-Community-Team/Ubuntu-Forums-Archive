---
title: "characters squares instead of letters"
date: 2013-10-01
forum: General Help
---

### Post by Voncina on 2013-10-01
Hi,

I have very strange problem who comes with latest update on my Ubuntu 12.04x64. I tried to reinstall desktop, but problem ist still here. 
The problem is in characters squares instead of letters. 

Can someone explain me please, what is going wrong? I have la Lenovo laptop with intel Centrino 2 chipset and Intel graphic till today without problems.

Thank you for any help.

---

### Post by t0p on 2013-10-01
I have encountered this before, with Linux and other OSes, and on cellphones (dumb and smart).  It has always appeared to me that the computer is trying to display some text which isn't included in the OS - eg I tell my pc during installation that I use British English, so the OS's locale doesn't bother including non-English characters.  So, when I try to read a file that includes say Cyrillic or Chinese characters, the computer doesn't know what it is all about and prints squares instead.  I don't know a work-around, except seeing if you can install the required locale files.

---

### Post by TheFu on 2013-10-01
Your probably are trying to view international characters with a limited character set. Change your locale and characters appropriately - usually UTF8 is what you want.

**sudo dpkg-reconfigure console-** .... something. Don't have time to look it up now.  console-common  console-data    console-setup are the choices.

---

### Post by Voncina on 2013-10-01
Ok. Thank you for your help. I will try to reinstall (third time  :mad:) and I will set character set to English (UK) and only a LibreOffice to my local language.

---

### Post by TheFu on 2013-10-01
> **Voncina said:**
> Ok. Thank you for your help. I will try to reinstall (third time  :mad:) and I will set character set to English (UK) and only a LibreOffice to my local language.

Why reinstall to OS?  Just run those commands and select a different characterset. UTF8 should cover it. This isn't a big deal.  3 minutes.  Uh ... the file system should also be UTF8 when created.  I thought that was the default - perhaps I'm wrong

You can read the wikipedia articles on UTF8 and locales to understand more.

---

