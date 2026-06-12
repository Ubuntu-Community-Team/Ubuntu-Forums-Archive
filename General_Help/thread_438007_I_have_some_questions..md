---
title: "I have some questions."
date: 2007-05-09
forum: General Help
---

### Post by Crafty Kisses on 2007-05-09
So I went into the IRC chat rooms last night, and I don't really think they understood my problem, but I'll shoot at the Ubuntu Forums.

I'm currently running Ubuntu off of a LiveCD, and it seems I can't access my C Files from my harddrive, the thing is I could access my files with the Knoppix Distro.

Basically what I'm asking is, is there anyway I can access my files on my harddrive from Ubuntu without installing the whole thing.

Thanks in advance. --- Codename

---

### Post by aysiu on 2007-05-09
Sure. Paste this code into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo fdisk -l
``` Look for the drive in question. Let's just say, for the sake of this example, that it's /dev/hda1 and NTFS (if it's something else, post it back here, and I or someone else will help you modify the appropriate command). Then paste these commands into the terminal: ```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
``` Launch up the file browser and browse the /media/windows directory, and you should see all your files. There is probably a GUI way to do this, too, but it depends greatly on what version of Ubuntu you're using... or if you're using Kubuntu or Xubuntu.

---

### Post by Crafty Kisses on 2007-05-09
Thanks man I appreciate it, I will get that to you ASAP.

---

### Post by aysiu on 2007-05-09
Just remember that pasting is easier and more accurate than retyping. Paste whenever possible. And if you run into problems, copy and paste the errors back here.

---

### Post by Crafty Kisses on 2007-05-09
> **aysiu said:**
> Just remember that pasting is easier and more accurate than retyping. Paste whenever possible. And if you run into problems, copy and paste the errors back here.

Thanks man, It's people like you that really make the Linux experience enjoyable for me, I'm trying the code right now, if I run into any problems I will be sure to tell you. Thanks Man. :D

---

