---
title: "GRUB config and editing"
date: 2007-09-03
forum: General Help
---

### Post by emanresu on 2007-09-03
i ran into a problem yesterday with GRUB that i hope there is an explanation for.

i was working at my laptop in Ubuntu (its also has MS and openSUSE installed on it) and then went to eat, so it sat idle for a while and then went into suspend or hibernation or whatever. before leaving the computer, i had been trying to chmod a directory without success. when i returned, i hit the power button to start up, as usual. 

the GRUB options screen came up, but none of my partitions would load. i was getting an "Error 15 file not found" for the SUSE partitions and an "Error 17 can't mount the selected partition" for the Ubuntu and MS partitions. i don't know what 15 means, because i don't know what file it refers to. and i didn't know why any partitions couldn't be mounted because i hadn't messed with any partitioning recently. 

after fumbling around with GRUB Super Disk (what a savior!), i was able to get everything pretty much working again. somehow, my /boot/grub/menu.lst file on Ubuntu was edited. a couple of lines of the MS partition information were removed, which was why it wouldn't work, i guess. the Ubuntu partition info saw a line changed to (hd0,0) when it was supposed to be (hd0,6) and the old kernel i had for Ubuntu, which had been edited out of the GRUB startup menu, had been uncommented, so it showed up in the GRUB startup menu again. 

sorry for the long post, but here is my question: how did all the things in the previous paragraph happen? i wasn't anywhere near /boot, let alone GRUB, when i was most recently logged into Ubuntu. is there some kind of explanation for how GRUB got edited without me doing anything to it?

---

### Post by InGunsWeTrust on 2007-09-03
The only explanation I have is that when you walked away somebody else walked up and thought it would be really funny to mess with you. Contrary to the believe of anybody who is computer illeterate, computers do not have a mind of their own and can only do what they are told to do. Nothing on a compuer is truely random either. Even the random number functions in programming languages actually reference CPU cyclies so for me picking the same random number is really only a 1 in 1.66 billion chance instead of a one in infinity chance. Another remote possibility is that somehow you were victimized by some happy hacker that wanted to mess with you and somehow keylogged your password or something. I mean there is just no way any operating system could just randomly come out with some random change on your menu.lst.

---

### Post by emanresu on 2007-09-03
> **InGunsWeTrust said:**
> The only explanation I have is that when you walked away somebody else walked up and thought it would be really funny to mess with you. 
the only other person in the house is my girlfriend and she wouldn't know where to start. 

>  Another remote possibility is that somehow you were victimized by some happy hacker that wanted to mess with you and somehow keylogged your password or something. I mean there is just no way any operating system could just randomly come out with some random change on your menu.lst.
i was worried someone would say something like this. 
anyway to tell if there is a keylogger or somesuch on my computer?

---

### Post by por100pre1 on 2007-09-04
Many users experienced GRUB issues after the kernel update this weekend. You are not alone.

---

### Post by emanresu on 2007-09-04
thanks for the answer.  it was a pretty strange occurrence though, so i'm staying paranoid for now.

---

