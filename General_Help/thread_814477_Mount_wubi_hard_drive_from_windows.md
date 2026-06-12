---
title: "Mount wubi hard drive from windows"
date: 2008-05-31
forum: General Help
---

### Post by designflaw on 2008-05-31
Hello,

I tried to search for figuring out a way to mount the wubi hard drive (I believe it is root.disk) from windows but most of the posts were the other way around so couldn't get to it. Is there a way to mount the wubi hard drive from windows xp? If yes, how do you go around doing it. I would guess that something similar to daemon tools exist that simply mounts the .disk into a virtual hard drive?

Incase you are interested in why I am doing this, I have a work laptop and the security is tightly locked on the xp installation. Rather then asking them to get me administrator rights, I installed wubi and am able to use to laptop for personal use whenever. Now, the thing is, since I am in ubuntu saving files, I need to access them from the windows installation and unless I boot into ubuntu, copy over the files on the ntfs partition, I wont be able to get to them. 

Has anyone encountered something like this before?

Thanks in advance.

---

### Post by abn91c on 2008-05-31
you can save your files to a windows folder instead of a ubuntu folder

---

### Post by designflaw on 2008-05-31
Yeah, thats the only way I am dealing with this right now. I am sure there has to be a way around it though.

---

### Post by unicorn_2003_1 on 2008-06-01
Of course you can, search for 'ext3' at Wikipedia, on that (the external links section) you have a list of tools to mount, read, write (safely) linux filesystems (ext2, ext3) on Windows. For example, [http://www.fs-driver.org/](http://www.fs-driver.org/), this one treats your linux partition (in this case, a loop disk) just as if it was a fat32, ntfs, cdfs, udf filesystem, etc.

---

### Post by designflaw on 2008-06-01
Thanks unicorn, I got it to work. I read through fs-driver but that seemed a bit too much of work. Settled for explore2fs ([http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)). Works great!

---

### Post by JasonSilver on 2010-07-02
> **designflaw said:**
> Thanks unicorn, I got it to work. I read through fs-driver but that seemed a bit too much of work. Settled for explore2fs ([http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)). Works great!
How does explore2fs work? I tried it, and it doesn't seem to show .disk contents at all.

Was there some special thing you needed to do to get it to work?

Jason

---

### Post by JasonSilver on 2010-07-02
From the WubiGuide: ([https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide))

> How can I access my Wubi install and repair my install if it won't boot?
Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:


sudo mkdir /win
sudo mount /dev/sda1 /win
Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein


sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

To check the filesystem you can use:


sudo fsck /win/ubuntu/disks/root.disk

---

### Post by nekosune on 2011-04-15
> **JasonSilver said:**
> From the WubiGuide: ([https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide))

And this has NOTHING to do with what OP wanted, they, like I wanted to be able to access it from Windows, not another ubuntu installation or anything like that.

---

### Post by howefield on 2011-04-15
Thread closed.

If you need help, please post a fresh thread in the appropriate forum.

Thanks.

---

