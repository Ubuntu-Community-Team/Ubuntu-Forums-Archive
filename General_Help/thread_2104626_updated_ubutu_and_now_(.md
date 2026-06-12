---
title: "updated ubutu and now :("
date: 2013-01-13
forum: General Help
---

### Post by 101kitty on 2013-01-13
I updated ubuntu and know it will not start up, it run but all i see is the CMOS telling me what usbs i have plugged in my computer, how do i fix this?

---

### Post by ivicks on 2013-01-13
It sounds like maybe the computer is trying to boot from usb instead of the HD. Try unpluging usb devices and see if that helps

---

### Post by 101kitty on 2013-01-13
it did not work

---

### Post by ivicks on 2013-01-13
You could try to forcing the computer to HD. On boot you will seen an option for "Boot Options" usually and F key or Del it will then ask where you want to boot from just arrow down key to the Hard Drive and hit enter.

If that doesnt work you many want to put the Ubuntu live disk back in and make sure you can see your hard drive. If you are able to see your drive I would make sure to backup your important files to a flash drive just encase you need to do a fresh install to the new version.

---

### Post by 101kitty on 2013-01-13
i installed ubuntu from windows becasue i didnt have a cd nor a usb drive.
what now?

---

### Post by ivicks on 2013-01-13
Ok I dont have any personal experience with Wubi but have heard of some issues with Wubi installs but I will need some more information

Is Ubuntu showing in the boot menu?
Are you still able to boot into Windows?
Did you happen to reinstall Grub2? (this can cause major issues)

---

### Post by 101kitty on 2013-01-13
Yes to all

---

### Post by ivicks on 2013-01-13
> Cannot boot into Ubuntu

Never try to correct Wubi boot problems by reinstalling Grub2. This will prevent Windows from booting and will not fix the Wubi install.

Ubuntu cannot be booted if Windows has not been shut down cleanly. If Wubi fails to start:

    boot into Windows, run chkdsk /r from Windows on the same drive where you installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again.
    if still not good, check that you have a C:\ubuntu\disks\root.disk file. If this file is missing, boot on Windows, open the Windows Explorer, set it to be able to see hidden folders, then look for a hidden folder called C:\found.000 or dir0000.chk . Move the files from found.000 to their original location inside the \ubuntu\disks directory. You may have to rename it into root.disk. 

Here is some info from WubiGuide off the Ubuntu Wiki

---

### Post by 101kitty on 2013-01-13
i need to run to the store but i will try this, check this post in about 45 mins, thank you.

---

### Post by 101kitty on 2013-01-13
i was able to find root.disk file, right know i'm running the chkdsk, hopfully it works.

---

### Post by 101kitty on 2013-01-13
This did not work for me, i'm going to see if i can replace the Root.disk

---

### Post by ivicks on 2013-01-13
Since I dont have any experience with Wubi you might want to close this thread and open a new one with a more specific title regarding Wubi. Sorry couldnt help out good luck.

---

### Post by 101kitty on 2013-01-13
After playing with it i was able to get ubuntu loaded, but i have to use a older grub loader, some something of that nature, every time i try to start linux in 2.00 grub or what ever its called it will not start, i need to use a older version.

Is there away to fix this?

---

