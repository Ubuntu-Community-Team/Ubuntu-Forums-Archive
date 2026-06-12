---
title: "Help save n00bs laptop"
date: 2015-03-23
forum: General Help
---

### Post by neo99002 on 2015-03-23
So my friend tried to load Ubuntu and now his bios is stuck on grub rescue. I have experience with Microsoft and android but don't know much about Ubuntu so please excuse me if I seem lost. I would like to try to fix this for my buddy.

Here is what he sent me:

1)      Installed Linux 7 successfully.

2)      Forgot to check the installation option that provides the front end that allows Ubuntu software.

3)      Attempted to change this installation to allow the Ubuntu front end.

4)      Apparent crash of BIOS.  Current screen on boot (grub>).

5)      Attempted to reinstall Window 7 with CD. Does not read drive.

6)      Attempted to find command for grub> to fix. No luck

If you guys need any other details please let me know. I preferably want to get it back to stock bios and windows 7 if thats possible. If not, its useless right now so if there is a way to at least get Ubuntu working that would be great as well. 

Any help would be greatly appreciated.

---

### Post by oldos2er on 2015-03-23
grub rescue> has nothing to do with BIOS, which has already handed over control to the boot loader by that point. Grub can't find any OS where it expects to see one, which is why your friend sees grub rescue>.

What do you mean by "Linux 7"? Also I don't understand points number 1 and 2.

If your friend can run the [bootinfo script ]("http://sourceforge.net/projects/bootinfoscript/")and post the results, it would help us to see exactly what's going on.

---

### Post by neo99002 on 2015-03-24
> **oldos2er said:**
> grub rescue> has nothing to do with BIOS, which has already handed over control to the boot loader by that point. Grub can't find any OS where it expects to see one, which is why your friend sees grub rescue>.

What do you mean by "Linux 7"? Also I don't understand points number 1 and 2.

If your friend can run the [bootinfo script ]("http://sourceforge.net/projects/bootinfoscript/")and post the results, it would help us to see exactly what's going on.

Thank you for the quick help. I looked at bootinfo script but got confused. I thought about it and bootloader is on the SSD so I took it out and formated in windows. When I went to install win7 it gave an error. Took it back out and low level formatted it. Its installing win7 as we speak :popcorn:

---

