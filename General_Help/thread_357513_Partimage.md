---
title: "Partimage"
date: 2007-02-09
forum: General Help
---

### Post by ronbrooks on 2007-02-09
I went to the synaptic package manager and down loaded the partimage program.  When I run the program it tells me that drive /hda1 is mounted and that I should unmount it first.  I tried the umount / and it tells me it is busy.  Well that is the main drive and has all the programs on it and it will alway be busy.  If I do it from the /etc/fstab and comment it out and restart I am not to sure my computer would even start if I did that. So how would I back up that drive.  

if anyone can help please let me know.

---

### Post by taurus on 2007-02-09
Maybe this guide will explain it a little better.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by ronbrooks on 2007-02-09
OK I guess I will delete it from my hard drive and do it that way but I still don't know how I unmount /  without it coming back as busy.

---

### Post by taurus on 2007-02-09
You cannot unmount a partition that you are using.  Therefore, you probably need to do that from a LiveCD and save the image to your harddrive.

---

### Post by ronbrooks on 2007-02-09
OK I will try it and get back to you thanks

---

### Post by Kilz on 2007-02-09
You might want to look at this page. Its a linux livecd rescue cd that has a lot of utilities including partimage. [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by ronbrooks on 2007-02-09
Thanks for the suggestion but I don't think any live cd will work because I can't connect to the internet with a live cd because I am on dial up and my modem will not work until I load the drivers for it. I guess I will have to find some other way to do it.  The reason I want to make a copy of my system because if I have to reinstall the ubuntu again it takes me two days to get the updates for it on the dial up network. I was thinking if I had a back up I could just load the back up and not have to wait all day for the updates. 

If you have any other idea for me let me know.

---

### Post by dcstar on 2007-02-10
> **ronbrooks said:**
> 
......
 The reason I want to make a copy of my system because if I have to reinstall the ubuntu again it takes me two days to get the updates for it on the dial up network. I was thinking if I had a back up I could just load the back up and not have to wait all day for the updates. 

If you have any other idea for me let me know.

If you want to save any updates you have previously downloaded, then back up your APT cache directory (and later restore it.....).

---

### Post by ronbrooks on 2007-02-10
Thanks!  that is a step in the right direction.  I guess you mean the /etc/apt directory.  So I can just copy that whole directory to a CD and then copy it back will that do it?

---

