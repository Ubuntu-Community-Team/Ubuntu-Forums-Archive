---
title: "The Uninstall Feature..."
date: 2008-05-19
forum: General Help
---

### Post by ibuclaw on 2008-05-19
So Ubuntu really wasn't what you were expecting...

You got frightened/frustrated at your lack of understanding and you want out to return back to the laden laggard we all know as Windows.

So, what do you do? How do you uninstall Ubuntu?

You could reformat the Ubuntu partition, but that will just leave you with an unbootable PC.

You search the forums, but all the advice is about inserting you Windows CD and selecting "Recovery Mode" in the option menu.

But say you are using an OEM version that doesn't allow you to do this, how would you go about re-inserting the Windows MBR?

Backup everything and do a clean install? That will certainly get rid of that virus that refused to go. But it will most definitely hamper you're productivity as you are forced to tweak everything once again and re-install all your software.

So here is one I propose, it's clean, short and simple...
```

sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```
Replace sda with the **hard-drive** that your MBR is on. (ie: **sda** and **sdb** is OK! sda1 and sdb1 is not...)
Reboot, and you'll instantly boot straight into Windows, no GRUB!

If you are happy with, all you simply do now is re-insert your Ubuntu CD and re-format your ext3 partition to a FAT32 one!

And thats it!
...
...
...
_____________________
Now, back on track...

If anyone knows how to reverse this, please let me know!!! :lolflag:
I found this how-to by accident, I was actually trying to make my USB stick bootable (What a huge surprise I found when it really didn't, but instead removed the GRUB bootloader)

The only way I can think of (as both installs are on separate Hard-disks) is to make the second hard-drive bootable, and then boot from it in the BIOS Boot Setup.

Any help is appreciated.

Regards
Iain

---

### Post by chewearn on 2008-05-19
I haven't use this myself, but a lot of people swear by it:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by ibuclaw on 2008-05-19
Hmm... can't seem to get it up right.

Aww well, I've just put an end on the Windows fiasco anyway!
I never use it, and I've been meaning to get 64Studio up and running on one of my desktops.

So I've gone off and Installed 64Studio over my last install of Windows!

I would of replied sooner, but I had NVIDIA problems with the 2.6.21 kernel (Had to constantly switch the xorg.conf file between "nvidia" and "vesa" before finally running the installer off the nvidia website (sigh).
Oh well, I have added a nice layer of digital vibrance that is pleasing to my eyes :D

I can now finally get started on some recording!
Sorry that you couldn't help, but thank's for all anyway!

I'll keep an eye supergrub in the future, it seems like an interesting project!

Regards
Iain

---

### Post by adrian15 on 2008-06-12
> **tinivole said:**
> 
So here is one I propose, it's clean, short and simple...
```

sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```


What's the mbr.bin size? **If it's 512 size you are LOOSING ALL THE PARTITION LAYOUT and probably ALL YOUR DATA**.

If it's 446 size then it is ok to run the command as you said.

So... What's mbr.bin size?

adrian15

---

### Post by ibuclaw on 2008-06-12
Dude... this thread is 3 weeks old :)

Still, a question is a question...

The output you are look for, I believe.

**du -ha /usr/lib/syslinux/mbr.bin**
```
**4.0K**	/usr/lib/syslinux/mbr.bin
```
**ls -lah /usr/lib/syslinux/mbr.bin**
```
-rw-r--r-- 1 root root **410** 2007-12-11 19:27 /usr/lib/syslinux/mbr.bin
```
And Nautilus says that it's **410 bytes**.

Regards
Iain

---

### Post by adrian15 on 2008-06-12
> **tinivole said:**
> 
And Nautilus says that it's **410 bytes**.

Regards
Iain

Ok. So there is no problem about the command then.

adrian15

---

