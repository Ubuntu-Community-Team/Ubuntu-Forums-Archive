---
title: "[SOLVED] USB drive won't mount"
date: 2013-06-19
forum: General Help
---

### Post by fredbird67 on 2013-06-19
OK, technically speaking, this isn't on Xubuntu.  Instead, I am trying to make my own Ubuntu-based distribution that uses the Xfce desktop environment.  However, since I can't stand Xubuntu's bloat, I'm doing things MY way, having started with the Ubuntu 12.04 Mini Remix as my base, and right now, I'm hung up on a problem that seems to defy solution, and I really need this not only for whoever uses this, but also to access some notes I've made to myself about what I want to be included in this project.

I'm trying to use my USB drive, but it won't mount.  It recognizes it, as it does appear on the desktop, but I can't mount it.  I've also tried seeing what happens with Thunar open, and when I insert it, it shows up in Thunar and even has the eject icon beside it.  But when I try to access said USB drive, it crashes Thunar.  I also tried opening a terminal and manually mounting it and got the following:

> username@pcname:~$ sudo mount /dev/sdf
mount: can't find /dev/sdf in /etc/fstab or /etc/mtab
username@pcname:~$ sudo mount /dev/sdf1
mount: /dev/sdf1 already mounted or /media/usb1 busy
mount: according to mtab, /dev/sdf1 is already mounted on /media/usb1
username@pcname:~$ 

Funny thing is, it says it's mounted in the terminal (is there a permissions issue to blame here?), yet I can't mount it by right-clicking on it and clicking "Mount".

What's more, I have pmount and halevt installed, plus I have gone into Xfce Settings --> Removable Drives and Media and checked "Mount removable drives when hot-plugged", "Mount removable media when inserted", and "Browse removable media when inserted".  I also went into System --> Users and Groups and checked EVERYTHING under my account to give myself permission to do everything in that list, including the use of removable drives.  But in spite of ALL of that, I STILL can't mount the blasted thing.

Any ideas?

Thanx in advance,
Fred in St. Louis

PS -- what I'd like to ideally do here is have the system automatically mount it and have Thunar automatically open to show the contents of the USB stick.

---

### Post by carl4926 on 2013-06-19
So the thumb drive has some data on it, otherwise it has no relevance to your project?
Does Gparted see it?

---

### Post by fredbird67 on 2013-06-19
Haven't tried that, although I do have GParted installed on said machine.  But I would expect that it can see it, because whenever I plug it in, it DOES show up on the desktop, so I think we can safely assume that yes, GParted would see it.  But the reason I'm guessing is because I'm at work right now and this computer, of course, is at home.

---

### Post by carl4926 on 2013-06-19
If it appears on the Desktop... Isn't it mounted?

---

### Post by fredbird67 on 2013-06-20
Carl4926, not necessarily.

I do, however, have a bit of good news.  I'm gaining on it and I'm ALMOST where I wanna be with this -- but there's one slight problem.  The SanDisk drives are still presenting some issues.  While I can mount their "U3 System" folders, I can't mount their other folders -- namely, the ones where you store stuff.  Non-SanDisk drives work AOK, and I'm thankful to have gotten that far with this after a LOT (and I mean a LOT) of trial and error.

What I did was add a bunch of entries to /etc/fstab for this very purpose, along with the "auto" and "nouser,auto" commands, and that seems to have done the trick...as long as it's not a SanDisk USB...any ideas on how to finish off this very highly annoying problem as far as SanDisks are concerned?

> **carl4926 said:**
> If it appears on the Desktop... Isn't it mounted?

---

### Post by carl4926 on 2013-06-20
I have some SanDisk thumb drives. Is that what you are meaning. Mine came with a load of garbage on that I wiped away? Are you working with something like this or are we talking as in Bigger external USB?

Adding entries to fstab isn't necessary for USB drives. I have never had to do it.

---

### Post by fredbird67 on 2013-06-20
Well, if you read everything very carefully, you'll see that what I did was based this project on the Ubuntu Mini Remix and then added what I wanted with an Xfce desktop, since I can't stand how Canonical chose to add a LOT of bloat to Xubuntu and ruin Xfce's reputation for being lightweight.  In other words, I started out bare-bones on this and didn't start with a Xubuntu base.

---

### Post by carl4926 on 2013-06-20
Sorry
Have you looked at
[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

---

### Post by fredbird67 on 2013-06-20
Hey Carl, guess what -- it now turns out that I don't need to.  Like I said, I can't stand Xubuntu's bloat.  Anyways, consider this one SOLVED! (doing my happy dance)

In the very same room as the computer on which I'm building my distro idea, I have another computer that I'm on right now, where I'm running Linux Mint Maya Xfce edition (Ubuntu-based, BTW).  Late last night, at a time when I was tired and needed to go to bed, before I did so, I started thinking, since Mint does this perfectly, how about look inside Synaptic for whatever programs it has installed that have the word "mount" in their descriptions.  I did, and I took down a list of all installed programs with the word "mount" anywhere in their descriptions, and printed them out and placed them by the computer on which I'm building my distro.

I just got home from work about an hour and a half ago, and went and undid a couple of other unsuccessful changes and then installed those programs.  And now, it mounts and unmounts USBs like a charm, just the way they're supposed to! B-)

BTW, in case anybody's interested, here's what all you install:

```
sudo apt-get install busybox-initramfs busybox-static fuse gnome-disk-utility gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs initramfs-tools inputattach libblkid1 libfuse2 libgdu0 libmount1 libpolkit-qt-1-1 mount mountall mtools policykit-desktop-privileges samba smbclient udisks
```

So if you ever try to start with a bare-bones Ubuntu Mini Remix base and are wondering why your USBs won't mount, give the above programs a try. B-)

---

