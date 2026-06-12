---
title: "Seeking help to fix duplicated boot + bad kernel update + unable to login"
date: 2019-02-23
forum: General Help
---

### Post by usernamoi on 2019-02-23
i have been reading a bit, and searching possible ways to solve this, and i think will some help i should be able to fix my problem(s) and recover the system. 

laptop 
i7 3630qm
16gb ram
Ubuntu-studio 16.04
plasma desktop

BACKGROUND 
ill try to make a long story shorter:
i was trying to change the kernel (from 4.15) to use a more recent one (4.16), but i couldn't install it because a library ssl1.1 file wasnt compatible with my version of Ubuntu (Ubuntu studio 16.04, running with plasma desktop; i ignored that only the previous version of that library, ssl1.0, exists for Ubuntu 16.04 even if i found the library for debian) and headers wouldn't install (from the missing dependencies).
  
i forgot i couldn't install the headers, and until i noticed (after becoming unable to resintall the 4.16 kernel, and trying to reinstall the 4.15), i understood why i wasn't able to use the nvidia drivers properly (openglx problem when trying to start steam). 

then i tried to reinstall the previous kernel that was working (4.15), and try to set again the NVIDIA driver i was using (before the failed update, i was trying to upgrade the NVIDIA driver, from NVIDIA open source 396.54 to 410.78, which i why i tried to also use a more recent kernel)
the previous problem with NVIDIA is a "bonus"; my main problems are two, which i think are actually the same: im unable to reach login screen ( **[https://streamable.com/j3g07](https://streamable.com/j3g07)** ), because i attempted to reinstall the kernel, but it seems to became cloned somehow, or installed where it shouldn't.

DESCRIPTION
when i turn on the laptop, the first thing that happens is that the kernel (4.15) loads twice
[https://streamable.com/6mmg0](https://streamable.com/6mmg0)

and if i check boot options, i can see two boot options for ubuntu (without inserting any additional os, like a live usb).
[IMG]https://i.ibb.co/G0fvKK7/00-duplicated-Boot-Option.jpg[/IMG]

if i try to select "advanced options" in grub, rather than the list of alternative kernels i had, many things begin to load in a command line and then stop in "initramfs", allowing me to write.
[https://streamable.com/39wau](https://streamable.com/39wau)

ADDITIONAL INFO
Im able to boot with a live usb, and can use a tablet as backup to search answers.

To be able to try to change or remove the kernel(s) from my laptop, i will need to mount my home folder which is encrypted; im still not sure which is the best way to find how the kernel became cloned, and how to remove the kernels, in order to reinstall at least the one that was working properly. I would like to know the proper way to do it from liveusb.

 Im unable to remember if i still have a copy or not of the passphrase, but i dont think the files in home folder or the disk are corrupted, so i should be able to mount it with my login and username. Ive found a few articles that describe different ways to do so, but i would like someone to guide me a bit so i can reduce chances of changing something i should leave alone so i can backup things, but also recover my system, and avoid having to reinstall or trying to find again many programs and configurations i made.

PASTEBIN
i have two pastebins: one from a few days ago, and other more current. The reason im posting both is that it could be useful to notice any additional changes
ie i dont know why this appeared:  "=> FreeDOS (eXtended FDisk) is installed in the MBR of /dev/sdd."
old pastebin
[http://paste.ubuntu.com/p/bnpHZKFr52/](http://paste.ubuntu.com/p/bnpHZKFr52/)

new pastebin
[http://paste.ubuntu.com/p/MYTMwk93zQ/](http://paste.ubuntu.com/p/MYTMwk93zQ/)


UNRELATED REQUEST

How i can remove an entry from the folder in "mount" that no longer exists (ie a partition that was deleted, but which name still appears in mount folder along active partitions)? lets call that "ghost partition" oldName: oldName appears in the "mount" folder, but it no longers point to any partition, since it was deleted.

Also, i would like if theres a guide to change other distros to work like ubuntu-studio, because i think i read once that ubuntu-studio has a special "pre-wired" way to manage jack and pulse audio; if possible, then i would like to know if theres a way to install all software included in ubuntu studio from a ppa to use individual packages (i would like to manage most video and graphics related programs with appimages). what im interested from ubuntu-studio is to test and learn a bit from the audio programs and tools included, but im not a big fan of the ui and desktop included (currently i like more plasma and dolphin file manager).

---

### Post by meheezen on 2019-03-04
o/ 
decided to respond on the Steam topic you made (i'm more comfortable with that), do take a look
[https://steamcommunity.com/app/221410/discussions/0/3247562523080888885/](https://steamcommunity.com/app/221410/discussions/0/3247562523080888885/)

---

### Post by usernamoi on 2019-03-06
Thanks for your reply.

---

