---
title: "boot problems"
date: 2008-05-03
forum: General Help
---

### Post by Immanuel_Black on 2008-05-03
Hello,

I am trying to intall Ubuntu 8.04. Now i'm using the windows installer that comes on the CD. It says it installs ok but when i go to boot into ubuntu at start-up it says that menu.lst is missing. Do i have to install ubuntu onto the same drive as windows, because at the moment i'm installing it on my second harddrive.

Thank you



Immanuel

---

### Post by ibuclaw on 2008-05-03
OK, it's been a while since I last used a windows machine, so bare with me a moment.

Bring up your boot.ini file information.
In the **run** command on the main programs menu type in "**msconfig**" and select the "**BOOT.INI**" tab in the newly opened window.

Just copy and paste the information on how your system boots up Wubi. And we'll decide together whether or not it should be edited.

[EDIT]
It should read something like this:
```
multi(0)disk(0)rdisk(0)partition(**2**)**\path\to\wubi**="Ubuntu Hardy 8.04"$
```

Regards
Iain

---

### Post by Immanuel_Black on 2008-05-03
Ok i looked at mine and it says:

C:\wubidr.mbr="Ubuntu"

Like i said i chose the windows install option "Install inside Windows".

---

### Post by ibuclaw on 2008-05-03
Sorry for the delay.

OK, can you open that file with a text editor?

If you can't see it in your C:\ directory, you'll have to open up the terminal to unhide it from view:

```

cd C:\
ATTRIB -H -S -R wubidr.mbr
notepad wubidr.mbr

```
If it is readable, (and small) paste the text of it up.
To re-hide the file:
```
ATTRIB +H +S +R wubidr.mbr
```

If you are wondering where I'm going here, I'm on a hunch that you've either moved the Ubuntu Filesystem block or something went wrong in the install and a pointer is pointing to the wrong filesystem

Regards
Iain

---

### Post by Immanuel_Black on 2008-05-03
i looked at the file it is unreadable. it all encrypted gibberish. there are a few english words here and there saying this:

Press space bar 
Press   to start GRUB, any other key to boot previous MBR ... 
Timeout :      
Invalid previous MBR. Press any key to start GRUB ... 
Cannot find GRLDR.  to hold the screen, any other key to boot previous MBR ... 
Error while reading MBR of  drive (hd0 )  
Invalid boot indicator in partition table of  
Invalid sectors_per_track in partition table of  
Invalid start_sector in partition table of  
Invalid end_sector in partition table of  
No boot signature in partition table of  
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart. 
Try (hd0,0 ) :  EXT2:  NTFS4:  NTFS5:  NTFS5p:  FAT32:  FAT16:  FAT12:  non-MS: skip  Extended:  invalid or null  This partition is NTFS but with unknown boot record. Please
install Microsoft NTFS boot sectors to this partition correctly, or create an
FAT12/16/32 partition and place the same copy of GRLDR and MENU.LST there

Thats all that is english.



PS. Sorry for my long delay. i got busy

---

### Post by Immanuel_Black on 2008-05-04
well i uninstalled it and reinstalled it on my system harddrive and everything is working a-ok now. i like to thank you for the help you gave me, even tho we did not get it working on my other harddrive.

---

### Post by ciarz3r on 2008-09-13
I have the same problem. I have a dual boot set up with Kubuntu 8.04.1 and windows xp. I recently updated windows xp to service pack 3 and since then I get the following error when trying to boot Kubuntu:

Try (hd0,0): non-MS: skip
Try (hd0,1): non-MS: skip
Try (hd0,2): non-MS: skip
Try (hd0,3): non-MS: skip
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart.

---

### Post by caljohnsmith on 2008-09-13
> **ciarz3r said:**
> I have the same problem. I have a dual boot set up with Kubuntu 8.04.1 and windows xp. I recently updated windows xp to service pack 3 and since then I get the following error when trying to boot Kubuntu:

Try (hd0,0): non-MS: skip
Try (hd0,1): non-MS: skip
Try (hd0,2): non-MS: skip
Try (hd0,3): non-MS: skip
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart.
Please boot a Live CD and post the output of:
```
sudo fdisk -lu
```
Did you do a Wubi install? Or does Kubuntu have its own partition?

---

