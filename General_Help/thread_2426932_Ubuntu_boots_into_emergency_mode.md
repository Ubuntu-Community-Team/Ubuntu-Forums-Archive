---
title: "Ubuntu boots into emergency mode"
date: 2019-09-15
forum: General Help
---

### Post by akky_66 on 2019-09-15
Hi

I have a laptop that I totally rebuilt (ASUS NV522VW)

I installed Ubuntu 18..04.3 LTS with Kubuntu ontop.

Having worked happiliy for a while. (Only rebooting every couple of weeks.)

I turned off my lappy as I was going away. Turned it back on an cannot get out of emergency mode.

Having doone a bit of research, the problem seems to be with fstab. However, nothing has changed.

On trying to read the file I currently have the following error in nano


Error reading lock file ./. fstab.swp Not enough data read.


I don't think this is the underylying issue, but cannot get to the file to even take a look and post what is in fstab.

Help appreciated

Steve

---

### Post by CatKiller on 2019-09-15
It's not a solution to your problem, but a useful diagnostic technique is to boot from the install image and use the framework of that for support. You'll have a browser, you can edit files, and you can use chroot if you need to run things as if you'd booted normally.

It might be enough to get you over the hump to figuring out what's going on.

---

### Post by yancek on 2019-09-16
> Error reading lock file ./. fstab.swp Not enough data read.

Do you have an /etc/fstab file currently?  A filename with a .swp extension is often the result of a failed attempt to access/modify that file.  If you have an /etc/fstab file exisiting (without the .swp extension and not a hidden file) you should be able to safely delete it.  If you google that error you will see numerous sites similar to the one below.

  [https://ubuntuforums.org/showthread.php?t=2371795](https://ubuntuforums.org/showthread.php?t=2371795)

---

### Post by akky_66 on 2019-09-16
Thanks for the repsonse. I'll give it a go. although it does seem strange that a 'change' has been made without doing anything.

---

### Post by akky_66 on 2019-09-16
Thanks for the response. I didn't notice it until I did a nano /etc/fstab and the file opended 'empty'.

---

### Post by akky_66 on 2019-09-16
So after sone researching I did a blkid and attempted to create an fstab manually. However, it has failed with errors somewhere.

I've attached a ss of the terminal output. Can anyone advise what the correct entry should be. Of course I'll add the UUID type and path details.
[ATTACH=CONFIG]284025[/ATTACH]

thx Steve

---

