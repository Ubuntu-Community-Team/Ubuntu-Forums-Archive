---
title: "OpenCV VideoWriter is saving files, but cannot save to USB drive"
date: 2024-05-23
forum: General Help
---

### Post by pinkevil15634 on 2024-05-23
Hi, I have image recognition software written with openCV on OrangePi5. I want to save files into USB drive from this software. So I used `sudo mount /dev/sda1 /path/to/recordings` and given the folder for recordings `chmod 744` to write and read and i can use any method either echo or python script to save in this folder anything i want. I however cannot save there my video recordings from image recognition software, eventhough I can save those videoclips anytwhere on device just fine.

Any advice?

---

### Post by TheFu on 2024-05-24
Lots of guesses. Check the easy things first.

Is the program a snap package?  Snap packages have mandated constraints, one of which is the location  in the file systems and which file systems can be accessed at all.

What file system does the USB have?  **chmod** doesn't work for non-Linux file systems like FAT32, exFAT, or NTFS.  It does nothing. Same for **chown**.  The only way to change permissions, owner and groups for those non-Linux file systems is with mount options, which it appears you didn't do from the command above. There are hundreds of guides for mounting non-Linux file systems in ways you want and where you want/need.  Mounting as above would make root:root the owner of all files and directories recursively.  Not very friendly.

Those are my initial guesses.

I know ZERO about OrangePi hardware or running Linux on it. Assuming linux is linux, which generally holds, those are my initial thoughts.

---

### Post by currentshaft on 2024-05-24
oi

---

