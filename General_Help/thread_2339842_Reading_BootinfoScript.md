---
title: "Reading BootinfoScript"
date: 2016-10-13
forum: General Help
---

### Post by RobGoss on 2016-10-13
Hello everyone I was wondering is there any documentation that shows how to fully understand how to read the Bootinfoscript when people are having issues with their systems 

I would like to have a better understanding what is the most important section I need to be looking at to help trouble shoot other users issue's 

I know it tells you how your OS is installed and also what order but what a does the bootinfoscript really telling us when we review it

Example, Boot loader, Is your system UEFU, Are you dual booting, Boot order, Things like that what exactly do we need to be looking for when we read a Bootinfoscript

I came across this post doing a Google search
[https://ubuntuforums.org/showthread.php?t=1291280](https://ubuntuforums.org/showthread.php?t=1291280)

Thanks so much for any help much appreciated

---

### Post by yetimon_64 on 2016-10-13
> **RobGoss said:**
> ...
I did find this documentation when I searched boot script for Ubuntu would you say this explains how to read it
[http://manpages.ubuntu.com/manpages/trusty/man7/boot.7.html](http://manpages.ubuntu.com/manpages/trusty/man7/boot.7.html)
Thanks so much any help would be appreciated

The name of that linked is "boot-scripts", what I get the impression you are talking about for helping others is the "bootinfoscript". 
They are 2 very different things. The boot scripts you link to there are used during the booting sequence of the OS. The "bootinfoscript" that people run to gather information for posting is not the same.
> Things like that what exactly do we need to be looking for when we read a **Boot script**

In your partial quote above you would be better off to call it the bootinfoscript when searching for information about it.

[[COLOR=#0000ff]--Here--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=1291280") is a very old thread on the forum for the bootinfoscript that I dug up by googling "bootinfoscript Ubuntu". [[COLOR=#0000ff]--Sourceforge link for the script itself--[/COLOR]]("https://sourceforge.net/projects/bootinfoscript/")

I don't actually know where you would find the information you ask for about "how to read it" though, it is pretty in depth in what it reports. 

Regards, yeti.

---

### Post by RobGoss on 2016-10-13
Hello Yeti, yes you are correct Bootinfoscript 

I'll look at the link you posted and change the title for my OP

Thank you Yeti for your help and time

---

### Post by oldfred on 2016-10-13
There is bootinfoscript which is a terminal bash script that outputs lots of data on system.
It has not been maintained at main site, but a fork was created by a new programmer which will parse new grub2 in MBR.
 [https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript) 
Older version with instructions on how to use:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I still run the bootinfoscript as part of my rsync backup, just to document my system. 

But now Boot-Repair's Summary Report uses bootinfoscript & adds even more data. But it cannot be run just from command line.
      
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 
    
If you look at the code of bootinfoscript, you will find links to the old forum posts discussing development. 
Originally .meierfra and caljohnsmith were asking users to run multiple commands to see what errors were. Then then combined commands into one file. 


        [SOLVED] How to determine which Linux partition w/ Grub controls the MBR?  
    [https://ubuntuforums.org/showthread.php?t=837791](https://ubuntuforums.org/showthread.php?t=837791)

I think I started about at version 30, and other users posting noted I jumped in with a solution based only on users first post.
But users often do not understand system and bootinfoscript gives lots of detail.
So I went back and looked for solved posts with script and reviewed script to come up with my solution and then compared that to correct solution. 
Biggest issue that only experience can help is when required info is missing and that missing data is the error. As it is easy to miss that.

---

### Post by RobGoss on 2016-10-13
Wow Hi Fred that's a smart way to do it I can understand now why information you post is so useful. I'm trying to get a handle on how the bootinfoscript is used and what info it presents this way I can try to pinpoint problems when users are in need of help

Just trying to gather up helpful notes can be a job in its self because there's so much info you don't know we're to start. 

Thanks so much Fred for the tips much appreciated

---

### Post by oldfred on 2016-10-13
Some of the script parses MBR and PBR - partition boot sector. I am still impressed that those guys new details of MBR and could then convert that to something readable.
But a lot of the script is just the output of standard commands, fdisk, parted, df, cat listing of fstab, cat listing of grub, blkid of UUID (so you can check that UUIDs match in places where they must match), etc. Some is also Windows info.

I have tried reading script, but some I still do not understand.

---

### Post by RobGoss on 2016-10-13
> **oldfred said:**
> Some of the script parses MBR and PBR - partition boot sector. I am still impressed that those guys new details of MBR and could then convert that to something readable.
But a lot of the script is just the output of standard commands, fdisk, parted, df, cat listing of fstab, cat listing of grub, blkid of UUID (so you can check that UUIDs match in places where they must match), etc. Some is also Windows info.

I have tried reading script, but some I still do not understand.

Thanks Fred I will try to look at the bootinfoscript and maybe note down some key points to be looking at. I know it has some very detailed information and helpful in trouble shooting most systems

---

