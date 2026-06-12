---
title: "View Vista Files"
date: 2007-10-11
forum: General Help
---

### Post by Doyley on 2007-10-11
HI all,

I have Ubuntu on a dual boot with Vista.  My Vista has been locked out by Bill Gates as of yesterday for one reason or another and I have some files on my Vista partition that I need.
When I try to view them from file browser they don't show up, it just looks like an empty directory.  Can anybody offer any advice?
I found some similar topics which I tried with no success but they look like old topics.

Thanks!

---

### Post by Jorge on 2007-10-11
You have to install NTFS (NT - file system) support in Ubuntu. The easy way is to add it using "add/remove.." at the end of the Applications menu. Just search for NTFS and you will see it. Maybe you will need to restart your Ubuntu before having access to the Windows partition. I'm not sure, because I have the NTFS support installed but by another way.

I hope this helps you.

---

### Post by overlord.gaurav on 2007-10-11
Install NTFS-3g
```
sudo apt-get install ntfs-3g ntfs-config
```
Go to Applications>>System Tools>>NTFS Configuration Tools >> Check the desired options.
Now you'll be able to get read-write access on your NTFS drive as well.

PS: Feisty Fawn has default NTFS read support, you should be able to copy files without installing anything. Which distro are you using?

---

### Post by Doyley on 2007-10-12
Thanks for your replies.

I am using Feisty Fawn.  I tried your suggestion which has not helped unfortunately.
I can view the HDD and most of the folders/files, all apart from the one I need.  I need to get into Documents & Settings because the files I need are on my desktop.  When I click on the D&S folder there is just a blank page saying there are no files.  I assume that this is some permissions problem?

Thanks again!

---

### Post by Doyley on 2007-10-12
Never mind, I am a thick idiot.  Vista desktop isn't in Docs & Settings anymore, its in /Users.
Thanks for the advice guys and sorry to waste your time!

---

### Post by sstusick on 2007-10-12
If you need to get the files off the partition why do you want to edit them? All you need to do is drag them from your Vista partition to your Ubuntu partition.

---

