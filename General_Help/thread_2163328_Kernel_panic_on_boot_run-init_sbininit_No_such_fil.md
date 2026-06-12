---
title: "Kernel panic on boot: run-init: /sbin/init: No such file or directory"
date: 2013-07-18
forum: General Help
---

### Post by Penguenci on 2013-07-18
I have a relatively new Ubuntu 13.04 installation (couple of months old) on an Intel desktop, which I've been running along with 4 other operating systems with major and minor problems, most of which I've been able to solve one way or another. 

The most recent things I've done were:

- Auto-mounting my Ubuntu partition on OpenSUSE
- Attempting to do vice versa on Ubuntu but failing each attempt and finally reversing my Ubuntu fstab file to the original after all the failed attempts
- Installing a couple of plymouth splash screens with Super Boot Manager (I had absolutely no splash screen prior to doing so) 

Please note that, I've been able to successfully boot into my Ubuntu installation multiple times after doing everything listed above. But today, all of a sudden I get an  error message when I attempt to boot into my Ubuntu, and it doesn't let me do anything, I can't go into the system at all. The last "extraordinary" thing I did before this happened was to change the system time on my BIOS, though I don't see how that may be related to my issue. 

Here is the error message:

```
run-init: /sbin/init: No such file or directory
Kernel panic - not syncing: Attempted to kill init! exitcode-0000100
```

There is also a long number there, possibly related to the Kernel, but I don't remember it. I'll find out if it's going to help solve the issue.

I've been surfing the forums and the web in general to see how other people with the same problem have solved theirs, but nothing I've found helped me at all. I've tried:

- Booting from a different, earlier Kernel (duh!)
- Recovery Mode (gives me the exact same error and doesn't go any further)
- Editing my burg.cfg
- Unmounting my Ubuntu partition from my OpenSUSE, even though that seemed irrelevant
- Booting from a Live CD and running the fsck command

Another thing is, I had my data storage drive fail on me, and I repaired it to keep working as a temporary solution. In the meantime, all my Linux and Windows installations had trouble booting, but I have successfully booted into all of them after the temporary fix I've applied to my broken HDD. Yes, including Ubuntu. But now I'm stuck in this pickle all of a sudden. I'm wondering if it could have to do with the HDD problem at all? Seems unlikely but still...

Other useful information:

- The Kernel I'm currently on is 3.8.0-26-generic
- I seem to have all my Ubuntu system files intact (that I know of, any input on what to check exactly would be welcome)
- All other OS's boot up without any issues whatsoever
- The plymouth splash screen still loads, but the loading dots don't run and my caps lock and scroll lock start blinking once the splash screen shows up
- I had to install the proprieratary driver compatibility mode for the splash screens to work correctly, and started to boot into the most recent Kernel after that. It had worked without problems until today. Speaking of proprietary driver, my video card is an AMD Radeon HD 7850

Please help! I don't want to reinstall from scratch once again, I have a lot to lose this time :(

---

### Post by Penguenci on 2013-07-18
*bump*

Nobody to help a desperate man in need?

---

### Post by DeathByDenim on 2013-07-18
This may be a silly question, but when you mount the Ubuntu partition, does sbin/init exist? init is the number one process that starts everything else. If that's missing, then your system will not boot, no matter what.

Hard drive fails may corrupt seemingly random files, so it could be that it hit an essential file. Did you already try running fsck on the Ubuntu partition? If there is something amiss with the Ubuntu partition, then fsck will find and fix it.

---

### Post by Penguenci on 2013-07-18
> **DeathByDenim said:**
> This may be a silly question, but when you mount the Ubuntu partition, does sbin/init exist? init is the number one process that starts everything else. If that's missing, then your system will not boot, no matter what.

Hard drive fails may corrupt seemingly random files, so it could be that it hit an essential file. Did you already try running fsck on the Ubuntu partition? If there is something amiss with the Ubuntu partition, then fsck will find and fix it.

It's probably my fault for writing such a long op to describe the problem, so people don't read it all. But I already mentioned all that, actually. The system files that I know to be crucial (as I said, I'm open to input about what's crucial) are all there, certainly including the folder and file in question. The HDD is in perfect health too, and so is the partition. I've already tried fsck as well, to no avail. It found absolutely no errors whatsoever. I feel totally lost :confused:

---

### Post by DeathByDenim on 2013-07-18
Heh, I did read the entire post, but "Ubuntu system files" was a bit generic, so I thought I would ask specifically. :)
Anyway, another possibility is that one of the libraries that init depends on is missing. Could you mount your partition and then use chroot
```
chroot /mnt/ubuntu
```
where you need to replace /mnt/ubuntu with wherever you mounted your partition of course.
Then you can type
```
ldd /sbin/init
```
to see on which libraries init depends. If any are missing, ldd should report that.

---

### Post by Penguenci on 2013-07-18
Hmm... Thanks for the input. That's one of the things I didn't think about. I'll try that and report back a.s.a.p.

---

### Post by Penguenci on 2013-07-18
```
ubuntu@ubuntu:~$ sudo chroot /media/ubuntu/Ubuntu
chroot: failed to run command ‘/bin/bash’: No such file or directory

```

However...

I ran this anyway: ```
ldd /sbin/init
```

And got: ```
linux-vdso.so.1 =>  (0x00007ffffdffe000)
    libnih.so.1 => /lib/x86_64-linux-gnu/libnih.so.1 (0x00007f79afaa4000)
    libnih-dbus.so.1 => /lib/x86_64-linux-gnu/libnih-dbus.so.1 (0x00007f79af89a000)
    libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f79af655000)
    libjson.so.0 => /lib/x86_64-linux-gnu/libjson.so.0 (0x00007f79af44c000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f79af244000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f79aee7b000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f79aec5e000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f79aff0b000)
```

Since I couldn`t successfully change root (I wonder why?), it isn`t warning me about what`s missing. I have an empty lib64 folder without that file in it, so that looks like it could be the culprit. But I remember creating that lib64 folder myself anyway, while trying to install Blu-Ray support for VLC Player.

In other words, I`m stuck again! :frown:

---

### Post by DeathByDenim on 2013-07-18
Oh, that's odd. I must be forgetting something about the syntax for chroot.
In any case, I think you may be on to something. This is the output off ldd on my Kubuntu 13.04 64-bit:
```
jarno@weasel:~$ ldd /sbin/init
   linux-vdso.so.1 =>  (0x00007fff7c9ce000)
         libnih.so.1 => /lib/x86_64-linux-gnu/libnih.so.1 (0x00007f7beaa18000)
         libnih-dbus.so.1 => /lib/x86_64-linux-gnu/libnih-dbus.so.1 (0x00007f7bea80e000)
         libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f7bea5c9000)
         libjson.so.0 => /lib/x86_64-linux-gnu/libjson.so.0 (0x00007f7bea3c0000)
         librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f7bea1b8000)
         libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f7be9def000)
         libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f7be9bd2000)
         /lib64/ld-linux-x86-64.so.2 (0x00007f7beae8f000)
```

I also looked at my /lib64 and it is also empty, except for one thing. There is a symlink for ld-linux-x86-64.so.2 there. It links to "/lib/x86_64-linux-gnu/ld-2.17.so". So could you go to the lib64 in your terminal and try this:
```
ln -s /lib/x86_64-linux-gnu/ld-2.17.so ld-linux-x86-64.so.2
```

I'm assuming there is stuff in the lib/x86_64-linux-gnu, right?

---

### Post by Penguenci on 2013-07-19
Thanks a lot for the support. I've solved the problem. You're right, everything else was intact, except for that little file in the lib64 folder. I thought it was a naive idea to assume I'd copy that file from the LiveCD and my Ubuntu installation would overcome the Kernel Panic, but I tried it anyway, and it worked! 

I can boot into my Ubuntu again, and it's running as it did before the Kernel Panic. No software issues, no speed loss, no nothing! I cannot fathom how on earth it worked until now without that file, or else how that file was made and disappeared (as I clearly remember that lib64 folder wasn't present in my original setup and I made it myself!), but the system is up and running and that's what matters at the moment.

On another note, as a reference to noobs who'd come across this thread in the future, I've also solved the Linux partition automounting problem with ARiOS AutoMounter. Chroot is the only thing that still doesn't work, and I really care about it. No wait, I don't :P

---

### Post by DeathByDenim on 2013-07-19
Glad you got it working again! You might still want to consider the symlinking I mentioned above rather than copying the file from the live-CD. Otherwise future updates might fail and possibly silently.

---

