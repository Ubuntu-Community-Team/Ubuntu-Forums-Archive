---
title: "No boot. 0 bytes available"
date: 2024-04-01
forum: General Help
---

### Post by wwdwgs on 2024-04-01
Hello, everyone.
today I couldn't start my Ubuntu Studio, after showing up ubuntu logo, the screen went black.
I used Ubuntu 18. CD and opened up my "troubled" drive. It shows 0 bytes available (out of 240 GB).
I ran these:

ubuntu@ubuntu:~$  dpkg --get-selections | grep "linux-image-[[:digit:]].*" | tr "\t" ";" | cut -d ";" -f1
linux-image-5.4.0-42-generic

I have no idea if this linux image belongs to the HD or CD.

I also ran: 

ubuntu@ubuntu:~$ dpkg -l | grep linux-image-
ii  linux-image-5.4.0-42-generic               5.4.0-42.46~18.04.1                              amd64        Signed kernel image generic
ii  linux-image-generic-hwe-18.04              5.4.0.42.46~18.04.35                             amd64        Generic Linux kernel image

Again, I don't see which image belongs to either HD or CD.
then I checked troubled HD, opened up media folder and found [computer's name] with 0 bytes and it's folder has an X mark.
Also, I can't delete any folders and files from troubled HD. nor move them to other available HD (back-up) in order to free some space.

That media filter take about 235GB and my HD is about 240GB.
Then, I ran: 

root@ubuntu:/# du -sh *
16M    bin
7.5M    boot
2.1G    cdrom
0    dev
5.9M    etc
83M    home
0    initrd.img
0    initrd.img.old
613M    lib
0    lib64
265G    media
0    mnt
0    opt
du: cannot read directory 'proc/3986/task/3986/net': Invalid argument
du: cannot read directory 'proc/3986/net': Invalid argument
du: cannot access 'proc/6377/task/7658': No such file or directory
du: cannot access 'proc/7661/task/7661/fd/4': No such file or directory
du: cannot access 'proc/7661/task/7661/fdinfo/4': No such file or directory
du: cannot access 'proc/7661/fd/3': No such file or directory
du: cannot access 'proc/7661/fdinfo/3': No such file or directory
0    proc
4.5G    rofs
120K    root
du: cannot access 'run/user/999/gvfs': Permission denied
1.9M    run
17M    sbin
1.6G    snap
0    srv
0    sys
500K    tmp
3.4G    usr
571M    var
0    vmlinuz
0    vmlinuz.old

At this point I don't know how to free up space form troubled HD. I have two physical HD's - one with Ubuntu Studio (that has 0 bytes) and another HD for a back up (formatted for linux, but w/o any OP).
What do I do now?
I can see only one solution - to copy every file from troubled HD to back-up HD and, then, reinstall Ubuntu Studio.
I also need to know what caused this problem and how to avoid it in a future.

I need your help and instructions.
TIA.

---

### Post by Impavidus on 2024-04-01
You mentioned your Ubuntu 18.something live disk. Both 18.04 and 18.10 are dead, but for emergency use of a live disk this is acceptable.

All commands you ran gave you information about the currently running system, so that's the live system, not the installed system. The user of the live system has no permission to write/delete on the installed system. You can use sudo though, which will give you that permission.

Try to find out what files have filled the filesystem of your installed system. 240GB or thereabouts should be plenty for an Ubuntu system, so either you collected a lot of big files (media files?) or you had some rogue process filling your hardive with junk.

---

### Post by wwdwgs on 2024-04-01
That's what I also thought about aforementioned commands - they return information about the running system.
All media (like files, videos, etc) don't take that much.
So, as I see it now, the only remedy is to back up all files from trouble HD, and re-install Ubuntu Studio.
At the least, the re-installation is much easier than Windows-based system...
by the way, linux live cds save my computers a few times, by allowing me to access "dead" HD and downloading/copying files before re-installation.

For the possible future problems - is there anything like "restore point" (that's used in Windows) available for Ubuntu to help to revert the system to the last know stable state?

---

### Post by ActionParsnip on 2024-04-01
If you boot the older kernel, does it boot OK. You may need to clear space (from the error). You can use a chroot from live CD/USB

---

### Post by Impavidus on 2024-04-02
> **wwdwgs said:**
> 
So, as I see it now, the only remedy is to back up all files from trouble HD, and re-install Ubuntu Studio.You're free to do so, but don't you want to know what went wrong, so you can prevent it from happening again?
> For the possible future problems - is there anything like "restore point" (that's used in Windows) available for Ubuntu to help to revert the system to the last know stable state?
You can make backups of your system and of your documents, but there's no magical tool that restores everything to the state you liked. Many (including I) make backups of their documents, but not of the OS. If that breaks, you just reinstall. Never happened to me in 17 years of using Ubuntu. I may have been lucky.

---

### Post by psychohermit on 2024-04-02
Something definitely went wrong.  My system uses 12 gig with /home on it's own partition using 8.4 gig for a total of 20.4 gig.  Granted it's Debian instead of Ubuntu Studio but 20 gig sounds about right for a Linux system.  Ubuntu Studio shouldn't take much more.  For a restore point you should install timeshift, and back up your system to an external drive.

--glenn

---

### Post by deadflowr on 2024-04-02
> I ran these:

ubuntu@ubuntu:~$ dpkg --get-selections | grep "linux-image-[[:digit:]].*" | tr "\t" ";" | cut -d ";" -f1
linux-image-5.4.0-42-generic

I have no idea if this linux image belongs to the HD or CD.

That's the Live CD

> I also ran:

ubuntu@ubuntu:~$ dpkg -l | grep linux-image-
ii linux-image-5.4.0-42-generic 5.4.0-42.46~18.04.1 amd64 Signed kernel image generic
ii linux-image-generic-hwe-18.04 5.4.0.42.46~18.04.35 amd64 Generic Linux kernel image

Again, I don't see which image belongs to either HD or CD.

That's also the live cd

I'm confused about where this is coming from since it shows
265GB used in the media directory.
```
root@ubuntu:/# du -sh *
16M bin
7.5M boot
2.1G cdrom
0 dev
5.9M etc
83M home
0 initrd.img
0 initrd.img.old
613M lib
0 lib64
**265G media**
0 mnt
0 opt
du: cannot read directory 'proc/3986/task/3986/net': Invalid argument
du: cannot read directory 'proc/3986/net': Invalid argument
du: cannot access 'proc/6377/task/7658': No such file or directory
du: cannot access 'proc/7661/task/7661/fd/4': No such file or directory
du: cannot access 'proc/7661/task/7661/fdinfo/4': No such file or directory
du: cannot access 'proc/7661/fd/3': No such file or directory
du: cannot access 'proc/7661/fdinfo/3': No such file or directory
0 proc
4.5G rofs
120K root
du: cannot access 'run/user/999/gvfs': Permission denied
1.9M run
17M sbin
1.6G snap
0 srv
0 sys
500K tmp
3.4G usr
571M var
0 vmlinuz
0 vmlinuz.old
```
I'm assuming it's also the live cd since it has a listing item for rofs which is a live cd item.
And the gvfs item lists user 999 which is also a live cd thing.

If the broken system happened to be what is mounted on media, then try running the du command against the /media directory.
Maybe set it to --max-depth=1 or something so it digs deeper.

---

