---
title: "I/O error during Microsd Card Write"
date: 2016-10-10
forum: General Help
---

### Post by palmgrower on 2016-10-10
MIcro sd card: 64GB in LG phone. It's been working well.

While downloading offline GPS map for Here to the card, the card was rejected. It could not be cycled thru Settings>Memory>Erase and Format. So I pulled the card out, put in SD holder, connected to Windows 7. Format to exfat. Error message: Windows is unable to complete. Scanned the card. No virus. Moved the card over to Ubuntu 15.04 PC. Gparted > Delete Partition > I/O Error during Write. I tried different buttons in Gparted. Different error message: cannot delete old partition information. Remove card and reinsert. Restart Gparted. The card is read as exfat with a red warning label. Is the card corrupted?
Thank you.

PS: Sorry for the long post. IOW, how do I know for sure that a memory card is corrupted?

---

### Post by sudodus on 2016-10-10
Something is corrupted. We don't know yet if it is 'only' the file system or partition table, or the card itself (hardware or internal system).

!. Is it important to save what is stored in the card? I guess not, since you have already tried to erase and format.

2. **exfat** is not fully supported by default in linux. It is a proprietary Microsoft file system.

See this link to Ask Ubuntu, [How to get a drive formatted with exfat working?](https://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working), suggesting to install two program packages,

```
sudo apt-get install exfat-utils exfat-fuse
```

and this link to Sandisk, [SD/SDHC/SDXC Specifications and Compatibility](http://kb.sandisk.com/app/answers/detail/a_id/2520/~/sd%2Fsdhc%2Fsdxc-specifications-and-compatibility)

-o-

If 'only' the file system or partition table is damaged, it might help to wipe the first megabyte with ***mkusb***, and after that create a new file system. If you need exfat, you should create it in Windows. See this link and links from it,

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by palmgrower on 2016-10-20
Thank you, sudodus. I triend mkusb. The process wouldn't complete. I am now convinced that the card is corrupted beyond repair.

---

