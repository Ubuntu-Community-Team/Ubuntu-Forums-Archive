---
title: "Command line question"
date: 2008-01-18
forum: General Help
---

### Post by the_tech_monk on 2008-01-18
I'm newish to Linux, I'm installing Mint as a dual-boot on a system w/ XP on a SATA drive, and DOS files on an IDE drive. 
I've been using terminal commands to examine directories in order to troubleshoot some startup issues, but I cannot seem to find a way to navigate from one mounted partition to another in the filesystem. In DOS I would use "d:" at the command prompt to switch to the root directory of the D: drive.

I can see my devices with fdisk, and I can browse them using the GNOME desktop tools. But how do I browse them in the terminal?

Thanks!
-techmonk

---

### Post by carlinuxlearner on 2008-01-18
cd thepathwherethedriveismounted

(example)
cd /media/winxp/

So where ever partition/drive is being mounted thats the directory you go to.

C@RL

---

### Post by the_tech_monk on 2008-01-19
OK, follow-on question: How can I find out where exactly the drives are mounted? Under /proc/mounts there's nothing, also /mnt is empty. If I try ' cd /dev/sda1/ ' for example, I get told it's not a directory. What am I missing?

---

### Post by the_tech_monk on 2008-01-19
C@RL, thanks for the reply, that did it for me... 
When I first read it I thought I saw "/mnt/device" and missed the important word "media". Oops.

---

### Post by HermanAB on 2008-01-19
Just type:
$ mount

to get a list of mounted drives and 

$ df

will tell you how free space they have.

Cheers,

Herman

---

