---
title: "&quot;Cannot mount volume&quot; ?"
date: 2007-12-12
forum: General Help
---

### Post by petitevache on 2007-12-12
Hi, 

I looked through similar threads concerning this problem but it didn't really help... 

I'm using Ubuntu to get my files off my computer (Windows just won't start so I want to reinstall it). When in Ubuntu, I go to "Computer" where there is the disc drive, "File System" and "74.5 GB Volume", which I want to access. However, when I try to, I get the error "Cannout mount volume", and under details: 

"$LogFile indicates unclean shutdown (0, 1) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have Windows then disconnect the external devices by clicking on the "Safely Remove Hardware" icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own reponsibility. For example type on command the: mount -t ntfs-3g /dev/sda1 /media/disk -o force . Or add the option to the relevant row in the /etc/ fstab file: /dev/sda1/media/disk ntfs-3g defaults, force 0 0"

Can anyone tell me what this means? And I'm afraid you're going to have to be as simple and detailed as possible because I'm pretty much an idiot when it comes to computers. 

Thanks loads in advance! 

(Alternatively, if anyone knows of a simpler way of getting my files off my computer without being able to access Windows, that'd be much appreciated as well.)

---

### Post by kpkeerthi on 2007-12-12
For some reason, ubuntu is unable to read from that partition as it is marked as being in use. Since you mention that you are unable to boot into windows, we can force mount this partition. 
Open terminal and type
```

sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force

```
to mount this partition.

---

### Post by kpkeerthi on 2007-12-12
If the partion fails to mount again after reboot.

1. Open /etc/fstab
```

gksudo gedit /etc/fstab

```

2. And change the line 
```

/dev/sda1 /media/disk ntfs-3g defaults 0 0

```
to
```

/dev/sda1 /media/disk ntfs-3g defaults, force 0 0

```
3. Save and exit
4. Type
```

sudo mount -a

```

---

### Post by petitevache on 2007-12-12
I tried the first code you gave and I get: 

$LogFile indicates unclean shutdown (0, 1)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda1 ( )

...?

---

### Post by petitevache on 2007-12-12
When I open etc/fstab to edit it, I get: 

unionfs / unionfs rw 0 0 
tmpfs /tmp tmpfs nosuid,nodev 0 0 


[actually the 0's are not 0 but something that looks like a 0 with a dot inside in the middle]

---

### Post by petitevache on 2007-12-12
It worked, I can access my files, THANK YOU! : ))))

---

### Post by petitevache on 2007-12-12
Neverending problems... any particular reason why (still on Ubuntu) the computer will detect and let me use a 1GB mp3player but won't detect a 300GB external harddive? (which works fine on another computer, so it's not the harddrive itself that's problematic.)

---

### Post by readyartbrut on 2008-04-05
Thanks for the help kpkeerthi, had the same problem and your instruction sorted it first time.

---

