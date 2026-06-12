---
title: "/bin/sh : can't acess tty/job control turned off || HELP !"
date: 2007-03-15
forum: General Help
---

### Post by Ephemeral on 2007-03-15
Well, hi again !
Basically, I have Kubuntu 6.10, and Windows, dual-boot, Grub.
One Linux boot I get this error :
```
BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```

Can anyone help ?
And plase don't just link me to another topic, it DOES NOT HELP !

---

### Post by peabody on 2007-03-15
Is this all the information you're getting?  Did Kubuntu used to work?

---

### Post by Ephemeral on 2007-03-16
Yes, Kubuntu worked before.
I think I installed the mozilla-mplayer package just before, but i'm not sure.
Any ideas ?

---

### Post by peabody on 2007-03-16
So, that's the only message you're getting?  You can't type anything at the prompt, and prior to this message, everything looks as though it's booting fine?

Can you boot the live CD?  We might be able to determine something from the logs of the installed system.

---

### Post by Ephemeral on 2007-03-16
Yeah, I can boot from a Live CD, no problem, now what ?
hellllllllllllllllllpppppppppppp !!!! :(

---

### Post by Ephemeral on 2007-03-16
bump

---

### Post by Ephemeral on 2007-03-16
Bump !

---

### Post by peabody on 2007-03-16
Do you know how to mount your Ubuntu partition from the LiveCD?

should be something like
sudo mount -t ext3 /dev/partitionname /mnt

If that's succussful, than /mnt will contain your filesystem.  Try looking at the end of /var/log/messages to see if there's anything interesting.

FYI, it would be nice if you could provide as much information as possible before the error occured.  What were you doing in Ubuntu, etc.

---

### Post by Ephemeral on 2007-03-16
Isn't it more like :
sudo mount /dev/sda3 /mnt ?
And yes, I think I ran an update, but I know I tried to install mozilla-player, realplayer and such, but failed.
Maybe the bad installation caused it !
Yeah, i'll go do that in the minute

---

### Post by Ephemeral on 2007-03-16
edited :
[http://www.flashspyre.com/messages.txt](http://www.flashspyre.com/messages.txt)

---

### Post by peabody on 2007-03-16
Well, there doesn't seem to be anything out of the ordinary in what you posted.  It's hard to say what could be causing the problem...the original message you posted has "(initramfs)" which may or may not say something about the initial ram disk for your kernel being corrupted.  When booting  from grub could you pull up the menu and see if you can boot from a previously installed kernel?

---

### Post by Ephemeral on 2007-03-16
I updated the message thing, it's got more in it now.
I have a Linux partition, so I can access my files, the kernels I have are :
```
title		Kubuntu 6.10, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Kubuntu 6.10, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Kubuntu 6.10, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Kubuntu 6.10, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Kubuntu 6.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot
```

How can I re-download those exact Kernels if they were corrupt ?
To clairfy : none of the kernels work

---

### Post by Ephemeral on 2007-03-17
bumpity bumpity bump

---

### Post by Ephemeral on 2007-03-17
bump !!!!!!!

---

### Post by peabody on 2007-03-17
> **Ephemeral said:**
> 
```
BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```


Are you sure there's no information that prints before this?  I can understand if there was that you wouldn't be able to copy-paste it, but any and all information would be helpful.

As for reinstalling the kernels, finding the relevant package at packages.ubuntu.com, downloading them into your /mnt, and then performing chroot into your mounted system and then a dpkg -i filename should do the trick.

---

### Post by Ephemeral on 2007-03-19
Booted with the live CD, overwrited the kernels with the CD kernels, still nothing
*sigh*
Please help ! :(

---

### Post by peabody on 2007-03-19
```

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

ARE YOU SURE THIS IS ALL YOU SEE WHEN YOU BOOT?  Have you pressed Alt+F1 the moment the ubuntu splash comes up to switch to text-based bootup messages?

I can't tell from any of your responses whether or not that's the case.  I'm not sure whether you think you answered that question indirectly, or whether you just forgot about it.  I'm not trying to be rude, but I'm having trouble believing that this is the only thing that comes up when you boot Ubuntu.  I can't help you unless I have all necessary information.

---

### Post by Ephemeral on 2007-03-20
Well, I'll try, but it seems it keeps repeating some error.
I'll try and write it down

---

