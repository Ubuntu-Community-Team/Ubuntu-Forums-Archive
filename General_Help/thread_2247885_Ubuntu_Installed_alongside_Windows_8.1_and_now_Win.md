---
title: "Ubuntu Installed alongside Windows 8.1 and now Windows wont boot and 400GB lost"
date: 2014-10-11
forum: General Help
---

### Post by nick152 on 2014-10-11
Hello,
The other day I installed Ubuntu alongside Windows 8.1, the installation went smoothly as far as I could tell and Ubuntu is working with no problem at all. However, When I try selecting Windows on the GRUB loader it displays the windows loading screen but says "Preparing system recoverry" then proceeds to say "Fixing hard drive errors" for a split second then reboots the computer and back to the GRUB screen. No matter how many times I select the windows OS it repeats this process and won't go any further. 

I allocated 100GB to Ubuntu and kept 400GB to Windows. The 400GB is displaying as an external drive (as expected) in my Ubuntu workspace but when I click it I get the following:

> "Unable to access"400GB Volume""

Error mounting /dev/sda2 at /media/nick/768CBDD78CBD925B: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/nick/768CBDD78CBD925B"' exited with non-zero exit status 18: Failed to open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sda2': No such file or directory

Could the Ubuntu installation corrupted my Hard drive? I used the suggested linux USB installer program on the Ubuntu install page. 

If you need any more details I can certainly let you know.

Thanks,
Nick

---

### Post by ecophobia on 2014-10-11
Looks like you screwed up the boot manager.  Try to access UEFI boot settings and disable secure boot (I assume you 've installed ubuntu 64bit with UEFI). Otherwise get Windows Live CD [http://www.ubcd4win.org/](http://www.ubcd4win.org/) and try to fix or recovery files from you Win partition and reinstall Windows. If you still want dual boot, you probably be better off installing it via Wubi, which is going to be much safer [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Forgot to mention, try **/dev/sda1 (or whatever partiton you need) ** /media/tmp ntfs-3g remove_hiberfile

---

### Post by nick152 on 2014-10-11
Hey Ecophobia, thanks for the reply! 
How would I go about accessing the UEFI boot settings? 

Would this solution require me to remove my current Ubuntu install? 

Also, could you expand upon 
> Forgot to mention, try **/dev/sda1 (or whatever partiton you need) ** /media/tmp ntfs-3g remove_hiberfile

Thanks,
Nick

---

### Post by nick152 on 2014-10-11
I tried entering it into the terminal and it says no such directory found

---

### Post by yancek on 2014-10-11
> "Preparing system recoverry"

That would indicate it is booting your recovery partition rather than the actual windows system partitions.  Try running:  sudo os-prober from a terminal in Ubuntu and then run:  sudo update-grub.

You access EFI settings in your BIOS.  When you boot the computer you should see a message telling you which key to press to "enter setup".
While you are in the terminal, enter the two following commands separately, hit the Enter key after each and post the output.  It is a lower case Letter L in both commands:

```
sudo fdisk -l
          parted -l
```

---

### Post by nick152 on 2014-10-11
After sudo fdisk -l :
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x32430816

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   781988720   390634936+   7  HPFS/NTFS/exFAT
/dev/sda3       781989886   976771071    97390593    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       781989888   968491007    93250560   83  Linux
/dev/sda6       968493056   976771071     4139008   82  Linux swap / Solaris



after parted -l :
> Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368MB  367MB   primary   ntfs            boot
 2      368MB   400GB  400GB   primary   ntfs
 3      400GB   500GB  99.7GB  extended
 5      400GB   496GB  95.5GB  logical   ext4
 6 


I'll run the grub update now :) 

Thanks for the reply!

EDIT:

After sudo os-prober : 

> /dev/sda1:Windows 8 (loader):Windows:chain



And its just finished updating grub I shall try rebooting now.

---

### Post by nick152 on 2014-10-11
Nope it didn't work :(

---

### Post by oldfred on 2014-10-11
It looks like a BIOS install not the new UEFI, but if Ubuntu cannot mount it, you may have left Windows hibernated.
Windows 8 is always hibernated as that is what it calls fast boot. And you have to go thru some effort to turn off fast boot.

       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

### Post by stanwil2 on 2015-03-01
I had mostly  only used Linux for many years until I bought a New computer in July. It had Windows  8.1 ® and I wanted to keep that install to play with. So after Ubuntu could not mount  windows  because it was hibernated, I ***finally*** figured out how to turn off hibernate . :-o
 I found to  go to search, **move mouse cursor to top right area of your screen until you see the search Icon**, then, **click the search icon**  and type in    the letters **CMD ** when command prompt shows, **right click on  Command Prompt** and** run as administrator**.
 Then in the command prompt type:  **powercfg.exe /hibernate off **   and then press** Enter**.  It will give no notice if that succeeded or not but it should have , but to verify in the command prompt, type ** powercfg.exe /A**  and press** Enter**  and  It should say down there in one line:
 **Hibernate: Hibernate has not been enabled**.
 I hope this helps someone.
Too late I see that I logged in with the wrong open ID, oh well.

---

