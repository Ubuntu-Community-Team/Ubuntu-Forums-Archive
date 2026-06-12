---
title: "Dual Boot Problem after using chown on windows partition"
date: 2013-07-07
forum: General Help
---

### Post by super279 on 2013-07-07
[SIZE=3]I [FONT=UbuntuRegular] was following this: [/FONT][Mount NTFS partition at startup, with non-root user as owner]("http://askubuntu.com/questions/92863/mount-ntfs-partition-at-startup-with-non-root-user-as-owner")[FONT=UbuntuRegular] to be able to use permissions with my NTFS partitions without having to change owner to "root". I did what the (accepted) first answer said with all my NTFS partitions. Unfortunately, this also includes the partition on which I have windows installed.The problem now is that windows doesn't load, it just shows a black screen with a cursor, after the "Starting Windows" screen. Safe mode does the same. However, the windows partition mounts normally on Ubuntu. How can I fix this ?
[/FONT]

[FONT=UbuntuRegular]**Additional Info:**[/FONT]
[/SIZE]
[LIST]
[*][SIZE=3]I have Ubuntu 12.04 LTS installed along with Windows 7, (both 64-bit).[/SIZE]
[*][SIZE=3]I don't have an Installation CD for Windows, I only have the recovery DVDs I created earlier. These will format the entire hard drive if used, and I really, really don't want to do that.[/SIZE]
[*][SIZE=3]Just before using chown and chmod on the Windows partition, Windows was working fine.[/SIZE]
[*][SIZE=3]I removed the lines I added to /etc/fstab and the problem still exists.[/SIZE]
[*][SIZE=3]This is my Boot-Info in case you need it:
[http://paste.ubuntu.com/5717589/](http://paste.ubuntu.com/5717589/)[/SIZE]
[/LIST]

---

### Post by Penguenci on 2013-07-07
If you see the starting orb and THEN the blinking cursor on top left, it might not be a problem with Linux or the auto-mount settings. It sounds more like a problem with the partition itself. If at all possible, try booting from a different MBR and booting directly into Windows using a Windows Loader without getting any Linux or GRUB involved. Whether your Windows successfully boots that way, can be a very important detail to find out in your case. If it boots fine like that, it's time to look into your GRUB and Auto-Mount configuration details. If it doesn't, the problem lies within Windows, even if caused by Linux somehow.

In that case:

Try using your Win7 setup disc to solve the boot problem (it'll walk you through) and see if it does you any good. It could simply be a file system issue, or something more complicated, hard to say with this much information. If the Win7 disc doesn't do it for you, you may need to use a little tool called TestDisk to play around with the boot sector and that.
 
On another note, if you have no intentions to auto-mount an ext4 partition (such as another Linux installation) and just want your NTFS partition auto-mounted, I recommend doing it through the Disks application in the future. Very simple GUI, and hardly ever causes trouble if you know what you're doing. Unfortunately doesn't work (though it's supposed to) for Linux partitions though.

[http://askubuntu.com/questions/300423/howto-auto-mount-ntfs-part-disks-in-ubuntu13-04-with-a-gui-tool](http://askubuntu.com/questions/300423/howto-auto-mount-ntfs-part-disks-in-ubuntu13-04-with-a-gui-tool)

---

### Post by super279 on 2013-07-07
> **Penguenci said:**
> If you see the starting orb and THEN the blinking cursor on top left, it might not be a problem with Linux or the auto-mount settings. 

The Blinking cursor on top left appeared first, then the starting orb. I don't know how to boot from a different MBR. Could you explain ?

---

### Post by Penguenci on 2013-07-07
> **super279 said:**
> The Blinking cursor on top left appeared first, then the starting orb. I don't know how to boot from a different MBR. Could you explain ?

I'm confused now. If the cursor appears first, what do you get after the starting orb then? BSOD? That information may also come in handy for diagnosis. For instance, if you see one of those typical BCD error messages written on white on a black background, it's quite likely to have to do with your Windows partition or the BCD on it.

You can use EasyBCD to install an MBR on a HDD. Install EasyBCD (freeware in most cases) on your Windows and use its GUI to install MBR on a different disk. I'm not sure about your level of computer knowledge, but most people knowledgeable enough to dare to install Linux, will be able to pull this off. The only caveat is that, you can only install MBR on a different DISK, not a partition. So if you have only one HDD, doing this would overwrite your GRUB. Even if you have a data drive, you can still install an MBR on it, but it does have to be a separate HDD.

Note that, if you install MBR on a separate HDD, you'll have to go to your BIOS and adjust it so that your computer will boot from that HDD instead. Otherwise you'll still face GRUB.

You could also try **[COLOR=#008000]SuperGRUB [/COLOR]**to circumvent the regular GRUB: [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/). If this boots into your Windows without problems, your problem may be as simple as a drive mapping error.

---

### Post by Impavidus on 2013-07-08
> **Penguenci said:**
> 
You can use EasyBCD to install an MBR on a HDD. Install EasyBCD (freeware in most cases) on your Windows and use its GUI to install MBR on a different disk. I'm not sure about your level of computer knowledge, **but most people knowledgeable enough to dare to install Linux, will be able to pull this off.** The only caveat is that, you can only install MBR on a different DISK, not a partition. So if you have only one HDD, doing this would overwrite your GRUB. Even if you have a data drive, you can still install an MBR on it, but it does have to be a separate HDD.

I doubt it. You don't really need any computer knowledge to dare to install Linux. Besides, from the boot info summary follows that OP only has a single hard drive.

Using the "permissions" option probably messed up the ntfs permissions on the Windows C partition, as a result of which Windows crashes during boot. Best practice is to mount /dev/sda2 (the windows C partition) read-only, so make sure you do it that way next time. The partitions can be mounted in Linux, so the file system is probably not damaged. I also don't think that the boot loader is the cause of the problem.

I don't know much about Windows, but to fix this issue you probably need a windows installation disk, which you don't have. I read that you can download a genuine one for free, provided you have a valid product key. I can't say exactly how. Else make backups of everything and use your recovery dvds.

---

