---
title: "Installing windows after Ubuntu"
date: 2008-06-29
forum: General Help
---

### Post by chris.tkd on 2008-06-29
Hello, 

I have ubuntu/xp dual boot on my machine, i use xp to play windows games. I want to re-install windows in the windows partition without effecting my ubuntu install. I think that when i reinstall windows the NTloader will wipe out GRUB and i wont be able to logon to the ubuntu partition any more?

Is there a way to install windows without installing ntloader? or is there another way to do what im after?

---

### Post by ajgreeny on 2008-06-29
Use the ubuntu live CD to reinstall grub and you're all there.
Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
   ```
 root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

---

