---
title: "Basic Question - grub.cfg changes"
date: 2012-11-08
forum: General Help
---

### Post by despuit on 2012-11-08
Outline:

Modify file:///boot/grub/grub.cfg

Reason: 

To modify the menuentry titles in the grub.cfg file.

System Information:

Linux version 3.5.0-17-generic (buildd@roseapple) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #28-Ubuntu SMP Tue Oct 9 19:35:58 UTC 2012

Distro: ubuntu 12.10
Memory: 7.9GB
Processor: Intel Core i5 CPU 750 @ 2.67 GHz x 4
Graphics: Unknown (No drivers installed)
OS Type: 32-bit
Disk: 31.7 GB

What would be the easiest way to do this?

Thanks

---

### Post by Popenuj on 2012-11-08
It seems that you are fairly new to this. Messing with the grub files could seriously mess things up. Maybe if you describe what you are trying to accomplish then somebody could walk you through the whole process step by step? Are you simply trying to change the names?

---

### Post by despuit on 2012-11-08
Yeah feel naïve for posting this thread, wasn't thinking. Has been awhile since I've really done anything with Linux as I no longer have to as a part of my profession. However with a little pondering I just modified the file with a simple pico command in terminal. 

Thanks again!

---

### Post by despuit on 2012-11-08
@Popenuj thanks for the response. Not really new per se just been awhile. The grub files have no effect on my computer as per the way it's configured. Yes you are correct was just a simple name change, knew how to add entries oddly enough however for the life of me couldn't remember how to change entries.

---

### Post by hal8000 on 2012-11-08
The easy way is to install Grub Customizer to rename the menu entries.

sudo apt-get install grub-customizer


There is a thread on renaming entries below:


[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)


and more documentation below:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Popenuj on 2012-11-08
You're welcome, I hope I didn't offend. I just didn't want to give advice to somebody and have it irreparably damage something.

---

### Post by Mark Phelps on 2012-11-09
While it's OK to modify grub.cfg if you're testing GRUB config changes, you need to understand that those changes are not permanent.

The next time you do a routine Ubuntu update that affects GRUB, the grub.cfg file will be completely rewritten automatically -- removing any changes you made.

That's one of the main reasons the file itself includes text telly folks NOT to make changes to it.

---

### Post by grahammechanical on 2012-11-09
You will find this useful:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

and may be this:

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")

I know I have.

Regards.

---

