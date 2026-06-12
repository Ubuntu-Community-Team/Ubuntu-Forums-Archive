---
title: "Paretition drive"
date: 2012-10-17
forum: General Help
---

### Post by rigidigital on 2012-10-17
could anyone help with my partitioning of my drive. I want to instal ubuntu, and win 7 and have a small 3rd partition that both systems can access ?  Its dgoing to be dual boot of course. 

Ive not done this exact thing before and am a bit of a newb.  Is there likly some partitioning software needed ? I hope you fellas have an answer even if its not nice :)

thanks again,

           Rgds,
                Mike.

---

### Post by Bashing-om on 2012-10-17
rigidigital; Hi ! Welcome to the forum.

What you ask has no simple answer as a system is set up for the way an individual uses his system - specific questions may be answered simply.
Before you start you need to know the current configuration: GPT partitioning, MBR (bios) partitioning, UEFI a factor ? 
These links will provide the needed instruction:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://ubuntuforums.org/showthread.php?t=2064761](http://ubuntuforums.org/showthread.php?t=2064761)
[http://ubuntuforums.org/showthread.php?t=1974392](http://ubuntuforums.org/showthread.php?t=1974392)

I do not want you to think I am being overly curt or rude, reading is good for you !
when you are prepared to ask a specific question, you will receive an answer.
[INDENT]with knowledge all things are possible <==BDQ

[/INDENT]

---

### Post by rigidigital on 2012-10-17
Thank you for all those links. It's time I started doing some good reading and having a real go or real effort to understand these things. I think I'm in for a long weekend at it. but mthen I'll hopefully have a better question when stuck.

I used to run SUSE AND UBUNTU IN VIRTUALBOX and Mac as well..  I'd rather just run linux and sometimes boot into win 7.

talk later .  :popcorn:

---

### Post by Bashing-om on 2012-10-17
You have our full support, when ready -> but try to take in, in small bites for better comprehension.
It is a steep learning curve, but well worth the effort to be the master of your machine !

[INDENT]try'n to help <==BDQ

[/INDENT]

---

### Post by homecomputer@on.aibn.com on 2012-10-17
> **rigidigital said:**
> [COLOR=DarkOrchid]could anyone help with my partitioning of my drive. I want to instal ubuntu, and win 7 and have a small 3rd partition that both systems can access ?  Its dgoing to be dual boot of course. 

Ive not done this exact thing before and am a bit of a newb.  Is there likly some partitioning software needed ? I hope you fellas have an answer even if its not nice :)

thanks again,

           Rgds,
                Mike.[/COLOR]
I do this on a regular basis. I can tell you my process if you like.

This is the general steps

1 install windows
2 use Ubuntu cd to shrink your windows partition .... program to use is called gparted partition editor
3 you probably want to make  4 partitions here ... one is the windows you just shrunk, two is a ntfs partition for both to access, three is a  ext4 partition for the linux, and 4 is a swap partition (I do 5gb for swap)
4 Then you install the Ubuntu from the cd on the ext4 partition.

This is fairly general .... you will probably have some extra things to do

Charles

---

### Post by Cheesemill on 2012-10-18
> **homecomputer@on.aibn.com said:**
> 2 use Ubuntu cd to shrink your windows partition .... program to use is called gparted 

I wouldn't recommend this.

It's far better to use Windows' own tools to resize the Windows partition (Disk Management). Using Ubuntu to resize a Windows partition can occasionally end up breaking your Windows install.

---

