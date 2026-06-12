---
title: "Error 15: Missing menu.lst"
date: 2008-04-30
forum: General Help
---

### Post by pmaconi on 2008-04-30
I had Wubi 8.04 installed and working for about a week. After a decent amount of messing around with Ubuntu, I had everything configured and running perfectly.

Today, I tried to boot up and it says that I am missing menu.lst. I haven't messed with the file in my Windows installation and I have no clue why it is missing. Is there any way to get another without doing a complete reinstall?

---

### Post by Diabolis on 2008-04-30
Try to reinstall grub, that is supposed to generate the menu.lst file again.

Steps to reinstall grub:
```

sudo grub
find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

So the output of the **find** command is the input of **root**.

If you can't boot, you can follow this steps from a live-cd.

---

### Post by tamoneya on 2008-04-30
hmm that is very odd.  I thought that wubi just modified NTLDR instead of installing grub.  Anyways lets try to sort this out. Can you possible burn a liveCD so that we can do some testing through command line.  Once you get into the live environment you should run```
ls -la /boot/grub
```

---

### Post by pmaconi on 2008-04-30
@Diabolis: find /boot/grub/stage1 yields file not found. The contents of my C:\ubuntu\install\boot are: initrd.gz and vmlimuz. C:\ubuntu\install\boot\grub is empty.

@tamoneya: I don't have access to a live cd. But from what I understand, Wubi modifies NTLDR to go to grub when you select Ubuntu. Otherwise grub does not appear.

---

### Post by ago on 2008-04-30
run chkdsk /r from windows

---

### Post by pmaconi on 2008-04-30
chkdsk /r didn't fix it. But I may have found the problem. My entire /disks folder is empty. I'm attempting to restore it to a previous version (even though I have no idea why it disappeared). I've got about 15 more minutes before its done.

---

### Post by ago on 2008-04-30
Look for hidden files called found.000 in C:\ or C:\ubuntu (to see the hidden files set the folder options)

---

### Post by pmaconi on 2008-04-30
No such luck. Grub works now, but Ubuntu does not. I guess I'll reinstall.

---

### Post by ohCanada on 2008-08-23
I have this problem running Xbuntu from a wubi install inside Vista home basic....I also have one "found.000" file in the windows /ubuntu directory so I am wondering what this could indicate...
To be more precise I am getting forced into the grub4dos menu (CodeEnd 0x41a38 ) and none of the files can be found, nor can I find anything useful via google or these forums. 

Any ideas would be much appreciated, I also had things working just as I liked them and am not enjoying being back in Vista full time. Thanks in advance,
-A

---

