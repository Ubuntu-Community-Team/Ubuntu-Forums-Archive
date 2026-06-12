---
title: "Libre Office 5.1.4.2 after upgrade to 16.04"
date: 2016-08-15
forum: General Help
---

### Post by Panawe on 2016-08-15
Hi,

Have just upgraded to 16.04 and it is very nice. However, I've noticed that the new version of Libre Office seems a bit buggy. In particular, I edited a document and after saving discovered the file was blank! Fortunately I had a backup and recovered this file. Has anyone else noticed problems with this version of LO?

TIA

---

### Post by grahammechanical on 2016-08-15
I have not experienced that issue with Libreoffice 5.1.4.2. In fact I have seen some improvement in the latest revision compared with 5.1 when it first came into Ubuntu.

I used to get a system freeze (GPU lockup) if I selected large blocks of text and I was running on the open source video driver. Also, large documents would take a long time to load and to save. But I am not experiencing either of those problems anymore.

I have noticed that when I copy text from one document to another sometimes part of the text would lose its font and change to the page default font. So, with a block of text in the freeserif font the last few words would be formatted as Liberation serif. It is intermittent.

Regards.

---

### Post by ajgreeny on 2016-08-15
I am using the 5.2.0.4 version from the LO ppa at [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa) and have never seen any problems with it since I started using it (can't remember when that was).

Could be worth a try as you can disable the ppa if it still is a problem and revert to the repos version again, or use ppa-purge to do that for you.

It may also be worth renaming the configuration folder in /home/username/.config/libreoffice in case that has become corrupted in some way or has an incompatible setting somewhere.  A new config will be made automatically when you restart LO.

---

### Post by Panawe on 2016-08-16
Done that (renamed libreoffice in .config) and restarted. Will keep a wary eye open when modifying files.

I suppose it's another lesson to always back up!

---

### Post by gordintoronto on 2016-08-17
I have seen the same thing. My CPU is also a Phenom II. Coincidence?

---

