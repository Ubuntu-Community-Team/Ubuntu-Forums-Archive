---
title: "is this file management errors by Nautilus or else?"
date: 2018-07-03
forum: General Help
---

### Post by bijaydeyp on 2018-07-03
Hi guys
 I am using ubuntu(14.04 32-bit) since last 3 years.I update my system regularly.
I have encountered a strange problem from last few months. 

Case-I
sometimes, when I copy-paste or cut-paste a file ( >= 200MB), in middle of operation the progress bar of Dialogue box stalls. the cross button does not work & cant close the box. if I press Alt+ctrl+bksp (which otherwise work fine) Login screen dont reappear, instead shows blank screen. I have to forcefully shutdown.
Case-II
sometimes, when I select all contents of a drive & click for  Properties the number of total files & sizes change constantly instead showing a fixed value.  e.g below are two screenshots taken in 3 sec interval.

 My Quary:
any idea what causing the problem & how to solve? 
Is my Nautilus files manager got corrupted?

---

### Post by Holger_Gehrke on 2018-07-03
For case-I check whether you get the same behaviour with a different file manager (Thunar or PCManFM come to mind as good alternatives, the default file managers of XUbuntu and LUbuntu respectively; 'sudo apt install thunar' or 'sudo apt install pcmanfm') or with the command line. You could also provoke the error and then try to drop to a virtual console (ctrl-alt-f1 to ctrl-alt-f6, ctrl-alt-f7 should return you to your graphical environment), log in on that and use the shell to find out what has stalled and why.

For case-II: Does it change randomly or is it just going up ? If it's the latter, than that's normal, especially for big directories with lots of files in lots of directories. On my system it takes quite a while (>> 1min) to get the number of files and the total size for an external 2tb drive.

Holger

---

### Post by bijaydeyp on 2018-07-03
Thanks Holger, for your help!

"For case-I check whether you get the same behaviour with a different file manager......"
I have tried same file with pcmanFM from fedora(multi-booted) but no issue there.

"For case-II: Does it change ramdomly...."
yes, it changes ramdomly, up-down continuously. dont show fixed value

---

### Post by bijaydeyp on 2018-07-03
one of two missing screenshots bcoz unable to upload other identical file. why? dont know!

---

### Post by bijaydeyp on 2018-07-03
screenshot of same directory from PCmanFM of Fedora

---

### Post by bijaydeyp on 2018-07-04
Still no clues, I am in total darkness. Any help is appreciated!

---

### Post by Claus7 on 2018-07-04
Hello,

I haven't noticed the problem you are reporting, as a result I will provide some ideas.

The first thing you could do is to open synaptic and from there to reinstall anything that has to do with nautilus. You could purge completely nautilus first, and then try to reinstall it. This solution is easy.

A second thing you could try is this:
[http://linuxg.net/how-to-reset-nautilus-to-the-default-settings-via-commandline/](http://linuxg.net/how-to-reset-nautilus-to-the-default-settings-via-commandline/)

removing nautilus files you could check if this solves your issue. If happy, then you can get rid of the old files.

Regards!

---

### Post by Holger_Gehrke on 2018-07-04
> **bijaydeyp said:**
> 
"For case-I check whether you get the same behaviour with a different file manager......"
I have tried pcmanFM from fedora(multi-booted) but no issue there.


I actually meant a different fm installed on the same system. The problem might lie not with the fm itself but with some underlying piece of software, gvfs for example.By trying different methods of doing the same thing on the same OS-installation you might pinpoint the responsible party by checking the dependencies of the various file managers. But at least trying it from a different OS shows us that it's unlikely to be a hardware fault at the root of the problem.

> **bijaydeyp said:**
> 
"For case-II: Does it change ramdomly...."
yes, it changes ramdomly, up-down continuously. dont show fixed value

Any possibility of this actually being right ? I mean are there any files and directories used for cache or rotating logs in there and do you know for sure that the data should be static in size with no other programs accessing files in those directories concurrently ?

Holger

---

