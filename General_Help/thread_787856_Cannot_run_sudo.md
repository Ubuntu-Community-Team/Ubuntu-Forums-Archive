---
title: "Cannot run sudo"
date: 2008-05-09
forum: General Help
---

### Post by MadHADR on 2008-05-09
Hi all, 

Whenever I attemtp to use sudo I get the following error:

bash: /usr/bin/sudo: Input/output error

Then in dmesg I see:

[  666.744000] attempt to access beyond end of device
[  666.744000] hdc1: rw=0, want=17221280496, limit=57464442

I have checked the drive with the manufacturers diag and it is ok. fsck runs fine. This is 7.04. I was planning on upgrading but I am not sure if that will help.

Thanks in advance.

---

### Post by GOROSSI on 2008-05-09
If you was going to upgrade I would just do a clean install after backing your stuff up when you have an issue like that. hardy is very good

---

### Post by wdaniels on 2008-05-09
This seems to be an obvious filesystem error, but fsck should have picked it up :confused:

Unless the error exists only in the cache, which might indicate a memory problem, but then I would have expected the numbers to differ only by one bit somewhere...

Is it a persistent problem even after a reboot?  I would definitely try to repair the filesystem again.

---

### Post by MadHADR on 2008-05-09
Yep, this happens across reboots, I have even changed controllers. My main problem at this point is that I cannot run ANY commands that require sudo.

---

### Post by wdaniels on 2008-05-09
> **MadHADR said:**
> My main problem at this point is that I cannot run ANY commands that require sudo.

Yeah I can see how that would make things difficult :D  Presumably it's the same with gksu?  I expect that uses all the same files, but it might do something slightly differently - worth a try perhaps?

Otherwise, the easiest way has to be a live CD.  Maybe best to make a Hardy install disk, boot into the live CD and try to repair the filesystem from there.

As for just upgrading, other than reformatting the root partition, I'm not sure what would happen if the installer tried to update the bad files and got an I/O error... (does it even do that from the live CD install?  I've always upgraded with apt so I don't even know)... personally, I think I would want to persist a little longer and try to fix the problem.

---

### Post by MadHADR on 2008-05-09
Thanks for the replies. I did run the fsck yesterday from a linux rescue CD(RIP Linux). I have been dealing with this for about 3 days and I definitely want to fix it vs a rebuild. Unfortunately, I do not have gksu installed, cant install it without sudo so that is not an option.

Will LiveCD do anything else for me besides the rescue CD? Sorry, I am fairly new to Ubuntu so I am not that familiar with the LiveCD.

---

### Post by wdaniels on 2008-05-09
> **MadHADR said:**
> Will LiveCD do anything else for me besides the rescue CD?

If you get stuck like this, the LiveCD tends to be the most convenient way to fix stuff.  I'm not sure about this RIP Linux, but most rescue CDs just have a bootable kernel and a collection of command line tools, which is fine if you already know what you need to do, but a full desktop can be more convenient if you need to research on the net and poke around a bit, plus once you've had enough you can just go straight into a re-install from there.

---

### Post by MadHADR on 2008-05-09
Good enough then. I think I have that LiveCD here somewhere, otherwise I will just download it. 

Will keep you posted.

---

### Post by wdaniels on 2008-05-09
It would be nice to figure out exactly which file(s) are damaged here that prevent sudo from working.  For example, two prime candidates are /usr/bin/sudo and /etc/sudoers.  You need root to access these files normally, but from a LiveCD you can access them and see if they are broken.

Ideally, you want to check and fix the whole filesystem, but from a LiveCD you might be able to fix sudo manually at least... it could be a long and difficult process, but if you have the time and the patience, this is how to learn linux "properly" :D

---

### Post by MadHADR on 2008-05-09
Looks like sudo and sudoedit are both hosed.

-rwsr-xr-x 32770 32768 32768 9223512776490739060 1938-09-21 13:29 /usr/bin/sudoedit
-rwsr-xr-x 32770 32768 32768 9223512776490739060 1938-09-21 13:29 /usr/bin/sudo

Now I need to figure out how to fix this. Great. Looks like I just saw another problem....

iscsi@hw-iscsi-target:/usr/bin$ ls
ls: memory exhausted

---

### Post by MadHADR on 2008-05-09
So much for that. Did a fresh install of 8.04, problem solved. Its nice that it has iscsi built in as well as this is what this machine is used for. 

Thanks again.

---

