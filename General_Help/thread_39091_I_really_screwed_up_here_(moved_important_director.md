---
title: "I really screwed up here (moved important directories)"
date: 2005-06-03
forum: General Help
---

### Post by _cashel on 2005-06-03
I *really* need some help fast on this one. I've been working the last few days on installing dedicated servers for various games on my linux box for a lan I'm having TOMORROW. 

I was patching UT2K4 to the latest version and needed to move the files to overwrite the original, older ut2k4 files. I thought I typed in the right command, but evidently not. What actually happened was I moved all of the folders and files that could be moved from the root directory into my ut2004 folder. 

Now I'm unable to do anything. PuTTy doesn't work, I can't access anything on the box itself. I CAN, however, navigate through the machine on WinSCP. I CANNOT move the directories though, because I don't have root access. At this point, if I need to reformat, I'll probably be pulling an allnighter, and with SAT's tomorrow, that's not a thing I want/need to do  :wink: . If you could *PLEASE* lend your support here, I'd be very very very grateful. Thanks.


edit: This just gets better and better. When trying to backup the directory I have for all of my dedicated servers to my Windows machine, I get an 'access denied' error. It can't even copy it? wtf?

---

### Post by adwait on 2005-06-03
I haven't completely understood about what your current status is, but if you cannot even boot into Ubuntu....you might want to try using the run level 3, which will boot your pc into a fail safe terminal session. In order to do this, at the boot loader prompt, press 'e' to edit the kernel arguments and at the end add the number 3. Now  choose to boot......this will start the system(hopefully) into the failsafe terminal session. Now login as the root, and move the directories back to their original places (again, hoping you which exact directories you moved...). Logout and reboot and everything might just be fine :) 

Best of luck

---

### Post by _cashel on 2005-06-03
I'm still pretty new to Linux, so I dont' quite follow you. I understand what needs to be done, however I don't know how to get where I need to do it. I'm getting an error when it loads GRUB, an error 15. I can't press anything that I know of (including 'e') to bypass that and edit what I need to. I appreciate the help so far.

---

### Post by shakin on 2005-06-03
Boot from any live cd (ubuntu, knoppix, etc) and use the file manager from the live cd to browse your ubuntu filesystem. You should be able to simply copy all the files back to where they belong in one big drag and drop operation (or by command line, but given your recent history I'd suggest staying away from that :-P ).

---

### Post by _cashel on 2005-06-03
[QUOTE=shakin]Boot from any live cd (ubuntu, knoppix, etc) and use the file manager from the live cd to browse your ubuntu filesystem. You should be able to simply copy all the files back to where they belong in one big drag and drop operation (or by command line, but given your recent history I'd suggest staying away from that :-P ).[/QUOTE]



lol I need to atleast focus on what I'm typing. I had been working on installing everything for a few hours prior, and just sorta stopped lost focus. Anyways, I just went ahead and reinstalled Ubuntu. I've got most of the server installs backed up, it shouldn't be as bad as I predicted. Thanks for the help though.

---

