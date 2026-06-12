---
title: "I'm stuck in here with boot issue"
date: 2015-05-13
forum: General Help
---

### Post by Caspor on 2015-05-13
hey and thanks for hearing me first :p
so i'm not that old using ubuntu and i never installed through usb so i got stucked even i tried some of boot repair
and i can't boot windows i only see ubuntu as defalut OS
 i'm downloading the boot repair live version to make in usb but i wanna make sure is it gonna solve my problem or not!!!
here's the boot info my pc made
[http://paste.ubuntu.com/11117659/](http://paste.ubuntu.com/11117659/)
hope someone can help me ):P:KS

---

### Post by QDR06VV9 on 2015-05-13
While you are in (Logged in) ubuntu open a terminal and enter this.
```
sudo update-grub
```
Then Reboot should bring up option for windows.
Its not a good idea to put grub in MBR of windows though.
> sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1 
                       and looks at sector 948641688 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
Regards

---

