---
title: "Using Ubuntu To Delete hiberfil.sys From Unbootable Win 8.1"
date: 2014-06-03
forum: General Help
---

### Post by d.riess on 2014-06-03
I have a Windows 8.1 install which won&#8217;t boot at all after a crash. No recovery disks or USB&#8217;s will boot either. The only things that boot are Linux based media and I have managed to run Ubuntu 14.04 from a live USB stick. I am trying to use it to repair Windows.

When I click the Windows partition on the hard drive I get the following message,

> Error mounting /dev/sda4 at /media/ubuntu/Windows: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda4" "/media/ubuntu/Windows"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0). Metadata kept in Windows cache, refused to mount. Failed to mount '/dev/sda4': Operation not permitted The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option.

Windows 8.1 hybrid shutdown and fast boot means the drives appear to be in a suspended state. I think because of the crash when I power on it&#8217;s trying to resume something corrupted which is why it won&#8217;t boot. I wanted to delete the hiberfil.sys file (what I read was the thing to do) in Ubuntu hoping that it will act like a full shut down and Windows will start again but I don&#8217;t know if this is the correct route to take. Is there anything someone can suggest?

Thanks

---

### Post by oldfred on 2014-06-03
I saved these links, but have never tried it. (My last Windows was XP.)

 Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

### Post by d.riess on 2014-06-04
Thanks for the reply,

I followed the instructions in the first link but it didn't work, using the command *,remove_hiberfile* didn't not mount the drive read/write.

So I changed the mount options field to ***,ro*** instead of** *,remove_hiberfile* **and now I have access to the drive in file manager but obviously its read only.

I can see the hiberfil.sys file in the Windows partition but I still cannot remove it. How do I get the drive writeable to remove it? Or is there any way to unflag the partition as suspended?

---

### Post by oldfred on 2014-06-04
The remove_hiberfile is a ntfs-3g command.
see:
man ntfs-3g

It also has recover which replaces the old force command which I was about to suggest. It does say recover is default but perhaps including it?

---

### Post by d.riess on 2014-06-04
> **oldfred said:**
> The remove_hiberfile is a ntfs-3g command.
see:
man ntfs-3g

It also has recover which replaces the old force command which I was about to suggest. It does say recover is default but perhaps including it?

Thanks for the reply,

I'm kinda new to Ubuntu and most of the tutorials on the net are out of date with Ubutu's new disk manager. I tried using the command *sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda4 *in terminal and it didn't work. I need to know what is the correct command to write or do I fill in something in the 'mount options' screen?

---

### Post by oldfred on 2014-06-04
Generally you do not want to mount the Windows system partition, you mount it read only or hidden so you do not accidentally damage it. The NTFS driver shows all files & folders where Windows standard setting has many system files hidden.

If not mounted elsewhere, see manual mount or fstab entries:

[http://linux.die.net/man/8/mount.ntfs-3g](http://linux.die.net/man/8/mount.ntfs-3g)
> Mount /dev/sda1 to /mnt/windows: 

ntfs-3g /dev/sda1 /mnt/windows 
or 
mount -t ntfs-3g /dev/sda1 /mnt/windows 
Mount the ntfs data partition /dev/sda3 to /mnt/data with standard Linux permissions applied : 
ntfs-3g -o permissions /dev/sda3 /mnt/data 
or 
mount -t ntfs-3g -o permissions /dev/sda3 /mnt/data 
Read-only mount /dev/sda5 to /home/user/mnt and make user with uid 1000 to be the owner of all files: 
ntfs-3g /dev/sda5 /home/user/mnt -o ro,uid=1000 
/etc/fstab entry for the above:
 /dev/sda5 /home/user/mnt ntfs-3g ro,uid=1000 0 0 
Unmount /mnt/windows: 
umount /mnt/windows 
 

All of the examples assume it is not mounted and that you have created a mount point like:
       sudo mkdir /mnt/windows

---

### Post by d.riess on 2014-06-13
I have tried all commands and all of them come back with the drive is in an unclean state etc etc...

I don't mind if it totally mess up the Windows partition, I need to force mount it read write.

Also "ntfs-3g -o force,rw" based commands no longer work, same error message. Apparently they are now obsolete in the current version of ntfs-3g

Is it true then that no program in current Unbuntu can force mount a Windows drive? If so thats madness.

Is there nothing I can try?

---

### Post by dragonfly41 on 2014-06-13
I have a dual boot configuration.

MountManager (installed from Ubuntu Software Centre) can recognise and mount/unmount NTFS partitions.

---

### Post by oldfred on 2014-06-13
You cannot run all or even most repairs to Windows from Linux. You have to use the Windows repair CD or flash drive that you should have made. You can make it yourself for free, but the source charges $10 or $20 where you used to be able to download from them for free. So we do not suggest them. If you have a friend or work computer with Windows 8.1 make it now.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by d.riess on 2014-06-13
I have tried every Windows piece of media out there including 8.0 and 8.1 DVD's and USB's as well as Windows recovery USB's all correctly formated for Fat32, UEFI and GPT. I have also tried all third party WinPE recovery media and even made my own DaRT bootable USB will all the drivers. Absolutely none will boot, the furthest some get is to a black screen with mouse.

Thats why I just want to either gain access to the disk even if it's just to wipe it of my personal data. The hard drive cannot be removed because its a sealed in SSD.

---

### Post by d.riess on 2014-06-13
So basically it is not possible to force read/write mount a Windows 8 partition in Ubuntu.... without first going into Windows to disable hybrid shutdown.

I am very very surprised that Ubuntu cannot do this and disappointed there is so much misinformation out there suggesting that it can be done.

Can I at least format the partition or something using Gparted? Just to wipe the data?

---

### Post by oldfred on 2014-06-13
Not sure if it makes a difference over the syntax you used. But this was suggested.

ntfs-3g /dev/sda2 /mnt/f -o remove_hiberfile

And this use said he changed boot flag, but that had to be a BIOS boot system.
[http://askubuntu.com/questions/384429/cannot-remove-hiberfile-on-ntfs-partition](http://askubuntu.com/questions/384429/cannot-remove-hiberfile-on-ntfs-partition)

---

### Post by d.riess on 2014-06-14
It gives the same message.... refused to mount, resume and shutdown windows etc etc

---

### Post by Balz_Mller on 2014-06-14
Here I am with the same problem ;-) 
 Boot from ubuntu-partition works, all other options fail (even external Linux-based bootable media)   ntfs-3g -o ro ... works, I can see the the hiberfil.  

  when I want to remove the hiberfile I get the following output: 
  ~$ sudo  ntfs-3g -o remove_hiberfile /dev/sda4 /media/  
  [sudo] password :   
  The disk contains an unclean file system (0, 0). Metadata kept in Windows cache, refused to mount. Failed to mount '/dev/sda4': Die Operation ist nicht erlaubt The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option.

---

### Post by Balz_Mller on 2014-06-17
can't believe we are the only ones to hit this problem..:confused:

By the way: I could not even boot the laptop from a bootable Medium (desinfec't)

---

### Post by Balz_Mller on 2014-07-20
Finally, I could find a solution :p
many thanks to ct' hotline for patient q-a-conversation!

here how it worked for me - maybe there is a better way... comments are welcome ;-)
But as there was no reply nor solution in this forum this is probably it.

**Problem description**
Let me sum up how it all began:

1. Get Laptop with pre-installded Win8
2. Get bored with all the Win-stuff ;-)
3. Create partition for later installation of Linux

--> here I missed the point of deactivating fastboot by:
- open cmd (as administrator)
- type [COLOR=#0000ff][FONT=lucida console]powercfg /h off[/FONT][/COLOR]
(such a small thing causing such a lot of trouble ^_^)

I don't exactly remember all the steps I did, but it should be like this:
- Install Linux from a bootable Medium (for this choose something like "control panel > general > extended boot > reboot pc" etc.)
- I played around with UEFI (reachable somewhere in the above "extended boot" menus) in order to have a menu when booting. If you do not do this you will still boot to Win.
- for some time I could start from Win or Linux
- at a certain point **booting from Win was not possible** anymore: just this dark grey screen and the mouse pointer.

While searching I found a lot of information about Win fast boot etc.
I used ntfs-3g to investigate the Win-Partition.
Manpage of ntfs-3g: [URL="http://manpages.ubuntu.com/manpages/trusty/man8/lowntfs-3g.8.html"]http://manpages.ubuntu.com/manpages/trusty/man8/lowntfs-3g.8.html
[/URL]
For some reason I could not delete the famous hiberfil.sys using ntfs-3g
(boot under linux, install and launch ntfs-3g from shell):

[COLOR=#0000ff][FONT=lucida console]Aspire-E1-522:~$ sudo  ntfs-3g -o remove_hiberfile /dev/sda4 /media
[sudo] password: 
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Die Operation ist nicht erlaubt
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
Aspire-E1-522:~$ [/FONT][/COLOR]

So I should remove a file I could not access :confused:

**Solution**
Here is how I got out of this blocked situation:

**get a bootable Medium with Win8. **
either you made a bootable Medium from your running Win installation 

or you have any other bootable Medium. It has to be Windows-based I think.
I got it from here: [http://www.heise.de/download/windows-8.1-1192088.html](http://www.heise.de/download/windows-8.1-1192088.html) (thanks to ct' editorial staff for the hint!)
registration? yes, just enter something.

**Boot from this Medium**
- during boot in the menu choose "Troubleshoot"
- next: "Advanced Options"
- then: "**System Restore**" (I tried "startup repair" too: it did not work)
- now you get a menu with all the restore points that were made when Win was running.
- choose the one you trust most and follow the restore wizard.
[COLOR=#ff0000]**FIRST THING TO DO NOW: disable fastboot!**[/COLOR]
- open cmd as administrator (Win-key, type "cmd", right mouse button on result and choose "run as administrator"
- type [FONT=lucida console][COLOR=#0000FF]powercfg /h off[/COLOR][/FONT]
- no feedback, no error message just: that's it
There is certainly a way to to this in the Windows settings but this seemed to be the easiest.

---

### Post by bohmto on 2014-07-20
Hi have you tried to disable secureboot in bios or the new ufei boot for windows 8 you wont be able to dualboot but i think that you can edit in windows disk i had a soulution to a similar problem with windows 7 and uesd ubuntu live usb to schrink down the windows partion with 70% and then rebooted in to windows and that triggerd the self repair on upstart.
after that i rezised the disk from ubuntu liveusb and rebooted to windows and it worked.

best reguards 
Tommy

---

### Post by pohancenik-martin on 2015-05-25
Hey guys, I finally found a solution that should work for you as well.
I had the same problem.. When I was going to install Ubuntu, I didn't power off Windows properly, instead I accidentally clicked restart and once I realised it I killed it by long pressing the power button (I am a PC murderer, I know...)
Anyway, even though I had fastboot disabled, Windows was still trying to save something in the hibernation file.

When I installed Ubuntu, I was not able to mount the Windows partition for writing ... It gave me the same "unclean partition, hibernation etc." error.

Ubuntu was not able to recognize the contents of the partition, making grub install Ubuntu as the only entry in grub menu (even fixing through Boot-Repair didn't help). The question was then how to erase the
hibernation file when you can't mount a partition for writing.

After a few hours of search I came across this command:

```
ntfsfix /dev/sda3
```

NTFSFIX is a utility available through the ntfs-3g package, so don't forget to install it :)

After this I was finally able to remove the hibernation file and mount the windows partition (sda2 in my case) for writing.

```
ntfs-3g /dev/sda2 /mnt/f -o remove_hiberfile
```

The last thing that remained was to add the windows option to grub menu. Run:

```
sudo grub-update
```

It is possible that a reboot might be necessary between the steps, so best of luck to you :)

Cheers!

---

