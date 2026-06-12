---
title: "OpenOffice not loading"
date: 2007-01-20
forum: General Help
---

### Post by paydaydaddy on 2007-01-20
Newbie here. I loaded dapper and it seemed to work quite well at first. Then I did the recommended updates and now OpenOffice will not load. I click on it and the logo pops up for a moment then goes away and that's the end of it. Any clues on how to fix this?

---

### Post by highneko on 2007-01-20
Is there an error message or anything? Try starting ooffice in a terminal and see if there's an error message.

---

### Post by paydaydaddy on 2007-01-20
Being the noobie that I am I don't know much about using line commands in the terminal. I can open the terminal and tried using help but it was pretty much greek to me. If it's not too much trouble would you give me the command line to open office in the terminal. So far I have gotten no error message. Thanks.

---

### Post by peterLinux on 2007-01-20
Okay so open that terminal and type 2 lower case o's followed by 2 tabs

oo [tab] [tab]

You should see something like this:

peter@ontario:~$ oo
oobase          ooffice         oomath          oowriter
oocalc          oofromtemplate  ooo-wrapper
oodraw          ooimpress       ooweb
peter@ontario:~$ oo

If you don't see oowriter it is not installed...

If it is installed complete the command by typing writer behind the 2 o's.

Post the output (cut & paste) if oowriter does not start up.

Peter

---

### Post by paydaydaddy on 2007-01-20
Here is the output from the line command:

paydaydaddy@pacman:~$ oowriter
/usr/lib/openoffice/program/soffice: line 233: 12534 Segmentation fault      "$s d_prog/$sd_binary" "$@"

** (process:12521): WARNING **: Unknown error forking main binary / abnormal ear ly exit ...
paydaydaddy@pacman:~$

---

### Post by paydaydaddy on 2007-01-21
moving to the top of the page. I'm sure somebody has some more clues for me.

---

### Post by paydaydaddy on 2007-01-21
Well, I did a lot of reading and tried a number of things with no results. As a last resort I tried uninstalling/re-installing OpenOffice. The uninstall went okay, but I was unable to re-install. The end result is that it totally killed Ubuntu. I can't even get the live CD to run now. I have ordered the pressed cd and will try re-installing when/if I receive it. While I consider myself pretty knowledgeable in the workings of MSwindows, I am sadly lacking in skills required to troubleshoot and fix a linux based system. I will continue to educate myself as I actually do want to make this work. It is the rainy season here in WA State  and a guy needs an indoor hobby {:^).

---

### Post by peterLinux on 2007-01-22
Segmentation Fault... that is not good.

Make sure your memory and harddisk are in good condition.
I suspect failing hardware in this case!

Peter

---

### Post by paydaydaddy on 2007-01-22
Thanks for the reply. I slapped a hard drive back in with XP installed and the machine seems to work fine which would point to a hard drive problem. A definite possibility since the hard drive I was uning for the Linux Distro is an older 30 gig WD. I think I will still wait for the pressed copy before I re-install since the download CDs keep coming up with errors showing. Minor, but errors just the same. In the mean time I will seek out a good buy on a new hard drive, test the memory, and continue to read up on useful tips for getting the most out of Linux.

---

