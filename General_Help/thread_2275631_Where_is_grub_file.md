---
title: "Where is grub file?"
date: 2015-04-27
forum: General Help
---

### Post by natchezjohn on 2015-04-27
I installed linuxmint first, then later installed ubuntu. I want to uninstall mint but fear I will mess up the boot if the grub (boot?) file if it is in the mint partition.

Where is it?

---

### Post by dino99 on 2015-04-27
grub (formely grub-pc, aka grub2) install into MBR (/dev/sd?, usually /dev/sda) on bios hardware; its different with uefi with/without gpt

---

### Post by natchezjohn on 2015-04-27
mint is in sda1, ubuntu is in sda6.

Where is grub?

---

### Post by natchezjohn on 2015-04-27
Found out how to do it!

Re: Change boot partition
Use the following command to install grub on sda:

Code:
sudo grub-install /dev/sda
then run:

Code:
sudo update-grub
This should be done while running Ubuntu

Followed above-deleted sda1 with gparted-rebooted-ubuntu only os on boot

SUCCESS!!!

---

### Post by natchezjohn on 2015-04-27
Forgot to give credit to cariboo

Post at [http://ubuntuforums.org/showthread.php?t=2275039&highlight=dual+boot+change+default+os](http://ubuntuforums.org/showthread.php?t=2275039&highlight=dual+boot+change+default+os)

Thanks

---

### Post by Bashing-om on 2015-04-27
natchezjohn; Hey, hey ;

You do good work. 
Thanks for providing the means to the solution.
As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]ain't it wonderful
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by natchezjohn on 2015-04-27
Wanted to mark it "Solved" but didn't know how. DOH!!

---

### Post by Bashing-om on 2015-04-27
natchezjohn; Hey !

It is all a process of learning . The guide is in the link provided above.
Short instruction:
1st post -> thread tools -> "mark as solved" .

only you can say that your issue is solved ( or a forum mod can mark ) .

[INDENT][INDENT]not done 'till
[INDENT][INDENT][INDENT]the paper work is done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

