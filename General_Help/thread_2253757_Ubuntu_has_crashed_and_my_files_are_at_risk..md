---
title: "Ubuntu has crashed and my files are at risk."
date: 2014-11-22
forum: General Help
---

### Post by goghvv on 2014-11-22
Hi.
So I'm writing from Windows 7 now, since I have Windows 7 running alongside Ubuntu 14.04 in a dual boot.
I was writing some latex code in TexStudio - nothing out of the ordinary, since I've been doing it for a couple of months now - when suddenly, while clicking Ctrl+S to save my work, TexStudio pops a pop-up saying it can't save the file!
I then opened my home folder, and found out that all the folders there have lock icon on them!
I rebooted my machine, picked Ubuntu from the dual boot menu, but Ubuntu won't launch! all I see on the screen is the underscore symbol '_' blinks in the left upper corner of the screen, and nothing happens.

Please! I have very important files there!
Is there a way to recover Ubuntu?
And if not, is there a way to access them through Windows 7 (please say yes)?

---

### Post by miguelpires on 2014-11-22
Hi,
From windows is complicated. Have you a live cd of Ubuntu? If yes you can run the live CD, choose the option "try Ubuntu" (experimentar UBUNTU (that what appears to me in Portuguese) and then try from the live CD to mount and copy your files.
After this maybe we can try to help you out (have a similar problem, and have to solve from grub recue)
Regards
Miguel

---

### Post by flaymond on 2014-11-22
You need to BACKUP your files immediately after you install Ubuntu for first time to dodge this issue from happened. As a newbie, I suggest to reinstall back without deleting your current works on Ubuntu. But, that would be a high risk to lose all your file. I think yes, there's a way...sorry...can't help much...


>  ***miguelpires ***Hi,
From windows is complicated. Have you a live cd of Ubuntu? If yes you  can run the live CD, choose the option "try Ubuntu" (experimentar UBUNTU  (that what appears to me in Portuguese) and then try from the live CD  to mount and copy your files.
After this maybe we can try to help you out (have a similar problem, and have to solve from grub recue)
Regards
Miguel

- That won't solve it because it will run like empty cd...when you boot using the CD (try ubuntu)..you only get the default installation desktop, your files won't available on the try ubuntu mode and even you download a files using the try ubuntu,it won't save to your pc memory because it's a (trying out ) installation mode.

---

### Post by goghvv on 2014-11-22
Yes!!! My baby is back!
I rebooted again, and decided I'll wait for as long as I possibly can, and just pray to the god of binary digits.
After 4 or 5 minutes of waiting, I get the screen of "Ununtu found errors in the disk", so I pressed 'F' to fix the errors, and this appears:
[IMG]http://i59.tinypic.com/2e498wk.jpg[/IMG]

Then a reboot happens again, and my Ubuntu is up.

I did a backup to my Documents folder in a flash drive.
How can I prevent this from happening again?
Is there a way to make ubuntu automatically backup my files every several hours?

---

### Post by flaymond on 2014-11-22
Im sorry, what I meant keep your backup files outside from your pc like in USB or CD. If you need to reinstall (for paticular reasons), you probably need the backup files after installation or you will lose all your current works on last session. Freezing and crash cannot preventing from happened, but we can take precaution by keep 'only' important files or big files in case you need to reinstall Ubuntu and need your last session files. Yes, there is....I heard there automatic backup keeper...it will save everything you do in the softwares....every seconds or mins

---

### Post by goghvv on 2014-11-22
Hi InterProg, thanks for commenting.
Can you recommend some automatic tool that will backup my files? preferebly on my dropbox, is there something like that?

---

### Post by miguelpires on 2014-11-22
> **InterProg said:**
> You need to BACKUP your files immediately after you install Ubuntu for first time to dodge this issue from happened. As a newbie, I suggest to reinstall back without deleting your current works on Ubuntu. But, that would be a high risk to lose all your file. I think yes, there's a way...sorry...can't help much...




- That won't solve it because it will run like empty cd...when you boot using the CD (try ubuntu)..you only get the default installation desktop, your files won't available on the try ubuntu mode and even you download a files using the try ubuntu,it won't save to your pc memory because it's a (trying out ) installation mode.

Hi,
That  is not correct. You can mount the system file from the ubuntu instalation (mount the hard disk without any problem). From their you can copy them! Have done that a lot of times.

But what is important is that I recover the files, soo ...
Regards
Miguel
PS: If you wana I can post some screenshots

---

### Post by mörgæs on 2014-11-22
@Interprog: Live booting is a good and simple method (maybe the best) of rescuing data whenever a hard disk is failing or other errors appear.

Please don't discourage people from doing so.

---

### Post by flaymond on 2014-11-22
You can try SpiderOak. ( I don't know if it still available, im using other software that light)

---

### Post by pqwoerituytrueiwoq on 2014-11-22
what happened was something went wrong accessing the hdd and ubuntu switched to read-only mode to prevent damage to data
i would run a disk self check from gsmartcontrol, to make sure the storage is not damaged/failing
> **goghvv said:**
> Hi InterProg, thanks for commenting.
Can you recommend some automatic tool that will backup my files? preferebly on my dropbox, is there something like that?does dropbox not have a sync client?
i use owncloud, handles backup/syncing for me

---

### Post by coffeecat on 2014-11-22
> **InterProg said:**
> - That won't solve it because it will run like empty cd...when you boot using the CD (try ubuntu)..you only get the default installation desktop, your files won't available on the try ubuntu mode and even you download a files using the try ubuntu,it won't save to your pc memory because it's a (trying out ) installation mode.

@InterProg, this is not correct. Using the live desktop session of an Ubuntu CD is a common way to retrieve files from Ubuntu systems that will not boot.

---

### Post by nknwn on 2014-11-22
I wonder if your hard drive is about to fail.

---

