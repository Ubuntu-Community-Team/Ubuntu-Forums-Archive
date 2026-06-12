---
title: "Want to boot to BusyBox"
date: 2019-06-26
forum: General Help
---

### Post by DanPerecky on 2019-06-26
The good news: I found BusyBox along the way in the boot process... as my laptops file system was messed up and couldn't continue all the way. It stopped at BusyBox to rest. So there I ran fsck.. which fixed a lot of errors. Now my pc is running better and faster then before.

The bad news: So I have a second pc that I want to have the file system go through the fsck filter / process.... just in case there are small errors, etc...

How can I deliberately boot to BusyBox, so that I can run fsck explicitly?

I tried the sudo touch /forcefsck method. That's a clever way to run it... but AFAIK, there is no positive feedback that confirms what happened during the run. :???: I want to run fsck on all, and see the verbose results.

Thanks.
O:)

---

### Post by CatKiller on 2019-06-26
I think /forcefsck has been deprecated in favour of the native systemd service.

You can always run fsck from a live image if you want to see it doing its thing.

---

### Post by DanPerecky on 2019-06-27
Cat,
Maybe it has been deprecated.... I don't know (either)... One thing I know, that after running fsck -f /dev/sda1/.... my Linux system was A Lot faster ... once it was fixed.

My conclusion would be that: Whatever systemd is doing... it's not enough. This is why I'm trying to get to BusyBox... which when fsck is ran from there, it 'seems' to provide better results(?)

BTW... for me, the live image alternate is not really feasible... as I'm running Linux from Virtual Box. I worked a lot just to get the shared virtual disk to function... not easy.

---

### Post by kpatz on 2019-06-27
fsck is a program that checks and fixes errors in your file system.  It makes no difference whether you run it from bash, busybox, or whatever.  The only requirement is that the filesystem isn't mounted, which is why you have to boot into busybox, recovery mode, or a live DVD/USB to run it on the root or boot partition.

Boot into a recovery shell or a live DVD/USB and run fsck from there.  It will work the same way.

There's no guarantee it will speed up your system... it just fixes errors.  If the errors were causing the slowdowns, you'll see improvement.  If there's no errors, chances are you won't see a speed improvement either.

---

### Post by DanPerecky on 2019-06-29
kpatz..
Thank You for your suggestions. I was able to go to the Recovery Shell... and found the recovery menu. I tried to run fsck from there, but alas, it failed. The message said that /dev/sda1 was attached. I went into the root prompt and did a umount there.. but that didn't help fsck run any better. Another error message popped up. :(

The other thing that I tried was to increase the size of the virtual disk (for something else that I'm trying) The virtual disk size is at 15Gb, with an original maximum of 20Gb. After using VBoxManage, it was increased to 25Gb. I also did an "[COLOR=#000000]apt get-upgrade". [/COLOR]Somehow, Linux seems a lot faster now. :)    Why? I have no idea... but the response time is markedly better.

Thanks again..

---

### Post by deadflowr on 2019-06-29
Read this:
[https://askubuntu.com/a/1007323]("https://askubuntu.com/a/1007323")

Also per busybox I think you can add a kernel parameter argument like break=premount that should boot to a busybox shell.
[https://wiki.debian.org/InitramfsDebug]("https://wiki.debian.org/InitramfsDebug")

---

