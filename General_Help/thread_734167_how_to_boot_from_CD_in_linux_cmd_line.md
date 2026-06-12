---
title: "how to boot from CD in linux cmd line"
date: 2008-03-24
forum: General Help
---

### Post by bfakefree on 2008-03-24
basically I put in RAM that appears to be faulty, after taking it out things went pear shape.

When it loads it has a fsck error, now I'm in the linux command line and have no idea what the hell is going on. I'm use to DOS, but don't know one command.

usually when on boot up with DOS, you can then choose to boot off the CD drive from the bios, but in ubuntu you do the same thing then you get a choice to boot off some recovery mode things, there is also a memtest, but none of these modes worked, all did the same thing (the memtest worked, but no use to me), can anyone tell me how to boot off the CD using the command line in Ubuntu linux, I dont mind starting again and formating hardrive and reloading Ubuntu, but need to know how to do this

---

### Post by jocko on 2008-03-24
> **bfakefree said:**
> ...can anyone tell me how to boot off the CD using the command line in Ubuntu linux...

What do you mean?
Once you have a command line you have already booted from the hard drive, there is no command to re-boot from a cd (not in linux, windows or dos).
You need to set your **bios** to boot from a cd instead of the hard drive.
Usually you get into the bios setup by pressing delete or F2 during the self tests that occur right after you power on the computer.

Once you have a command line you can try to start gnome by logging in and typing this command:
```
sudo gdm
```

---

### Post by pointone on 2008-03-24
There's probably a very simple fix that isn't so drastic. Please post the exact error message you see (fsck-related).

---

### Post by bfakefree on 2008-03-24
Hi there

The 1st poster kinda answered my question, usually u push del button and u get into bios setup, in this case it took me to some menu with recovery mode ubuntu versions to start, not knowing Linux at all I assumed there was no bios setup as it gives you like 1 sec to push the F11 key which then allows you to boot off the CD (F2 for bios), so the 1st poster made me realize there was a bios setup and had to just push the F11 key very quickly, so thank you. sudo gdm didn't work. (whats up with sudo, why not 'load GDM'

I re-installed Ubuntu off the CD and am back up and running, but out of interest wanted to know why it crashed, here is the error mess

/dev/hda1 contains a file system with errors, check forced
/dev/hda1:
Inode 228933 has illegal blocks
/dev/hda1: unexpected inconsistency; run fsck manually
fsck died with exit status 4

also in DOS if you wanted to get to the CD drive you just type in the directory, usually the D or what ever drive it is in, with the commands in linux how do you get to the CD drive so you can load whatever is on the CD.

---

### Post by pointone on 2008-03-24
Ubuntu runs an automatic filesystem check (fsck) occasionally during boot. In this case, fsck found errors that it was not able to correct automatically, and requested you run it manually. This allows it to provide a prompt and allow you to choose how to deal with the error. A manual fsck could be run by entering "fsck /dev/hda1" at the BusyBox prompt that is usually initiated after fsck fails.

Mounting the CD-ROM drive is usually as simple as typing "mount /cdrom". The files will then be available in /cdrom. If you have more than one drive, you'll need to choose the appropriate one in /media: /media/cdrom0, /media/cdrom1, etc.

---

### Post by bfakefree on 2008-03-24
thanks bro, i'll get the hang of these commands, i actually like it when these things crash, best way to learn commands, very diff to DOS.

---

