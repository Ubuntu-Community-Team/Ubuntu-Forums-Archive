---
title: "New (Frustrated) Ubuntu user - Install problem"
date: 2007-01-21
forum: General Help
---

### Post by Knewguy on 2007-01-21
Hello all,

I am a new user of Ubuntu (and Linux, in general) and think the OS is great. Since install the OS, I rarely use Windows but I have a problem with an installation of Dreamweaver 8.

I know there are other Linux based programs similar to Dreamweaver but I need to learn this program for my job.

For the longest time, I have searched and used the recommendations of threads here on this topic BUT I still can't get wine to run Dreamweaver.

The problem I'm having is the program starts and goes through the initializing stage but then just ends...or disappears. It just stops loading.

I have wasted many hours trying to get Dreamweaver to work. Again, I think Ubuntu is great and want to keep using it but a "simple" install like this is getting to be very frustrating.

I appreciate any help on this topic.

Thanks.

---

### Post by houstonbofh on 2007-01-21
"Simple install?!?"  Have you tried to run a linux binary in windows?  This stuff is NOT trivial.

I would start in the WineHQ support places. [http://www.winehq.com/site/getting_help](http://www.winehq.com/site/getting_help)  They know Wine best.  This page may help. [http://appdb.winehq.org/appview.php?iVersionId=3482](http://appdb.winehq.org/appview.php?iVersionId=3482)

If that doesn't work, you can always try a VM like qemu and run a virtual Windows.

---

### Post by Knewguy on 2007-01-21
The "simple install" comment pertained to some of the other threads I read on how to install DW8 as an easy process of copying and pasting files and converting reg files.

I'll check out those links you provided. But, soon I might give up on the process (b/c I've wasted MANY hours on it), move on and realize I have to run Windows for Macromedia products and learn a WYSIWYG program naive to Linux.

I appreciate your help.

Thanks.

---

### Post by crane on 2007-01-21
Next time you run the program be sure to run it from the terminal with the wine command. Then when it crashes look at the last few things in the list and see if it gives any errors. You can also post the error here for others to help. There are a lot of determining factors to consider once you narrow the errors down.
One thing to note is versions? OS, Wine, DW?

---

### Post by Knewguy on 2007-01-21
Thanks...OS Ubuntu 6.10, DW 8, Wine 0.9.29...

I'll try the terminal again and post the info. :)

Info. 

~$ wine dreamweaver
wine: could not load L"c:\\windows\\system32\\dreamweaver.exe": Module not found

---

