---
title: "Setting default boot - grub.cfg does not have all boot options"
date: 2014-08-08
forum: General Help
---

### Post by JimLS on 2014-08-08
Tried to add Ubuntu 14.04 to a 11.10 system.  Have some display driver issues to work out on the 14.04 and want to set the default boot to the old system.  Tried:

grep menuentry /boot/grub/grub.cfg

but it doesn't display all the options displayed at boot time.  The 3.5 kernel options seem to be missing.  I have mucked around with the grub file and 
sudo update-grub 
but I can't seem to change the boot except manually at boot time.  Seems like there is another boot loader that is controlling the boot or something like that.  If another copy of the bootloader is installed where do I find the config file for it?

---

### Post by Bashing-om on 2014-08-08
JimLS; Hi !

You are aware that release 11.10 is End_Of_Life, and no longer has support, yes ?
And yes, only one OS can control the booting process, in this case it will be 14.04 as 11.04 has no access to the software repository.
So, how to make sure it is 14.04's grub that is that entity ?
Boot up, what version of grub is displayed at the top of the screen in the grub menu ? 
terminal command:
```

sudo grub-probe -t device /boot/grub

```
will show the device that grub is booting ( like maybe sda1).
Terminal command:
```

uname -r

```
will show the kernel that is being booted.
Terminal commands:
```

sudo fdisk -lu ##to show all the partitions the system is aware of##
cat /etc/fstab ## too see what partitions the system is booting##
sudo blkid ##to verify the UUIDs assigned to the devises

```

Now to look at the boot config file menu entries:
```

grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0

```
----------------------------
Once known the partition containing the "root" file system for 14.04, then grub can be installed to the MBR of that hard drive to control the boot process.
Depending on the conditions depend on how.
No internet connection: will require a liveDVD(USB) of release 14.04 in order to pull the files off that medium.
Depending on what is required to replace in the instll:
maybe as simple as 
```

sudo grub-install /dev/sda

```
To as complex as a complete purge and reinstall of grub that will require internet access to obtain the required files - even this is not a big deal to do.
------------------

Probably more than you wanted to know, but you did ask.

[INDENT][INDENT]all in the process of learning
[/INDENT][/INDENT]

---

### Post by Dennis N on 2014-08-08
> Tried to add Ubuntu 14.04 to a 11.10 system...want to set the default boot to the old system.

I understand "set the default boot to the old system" to mean you wanted to continue to use the old grub menu you have in 11.10 with the 14.04 system added to it. If so,

(Assuming an MS DOS partition table) For this to work, when you installed Ubuntu 14.04, you needed to install grub to the 14.04 partition instead of the MBR (for example, install to sda3 instead of sda). Then, rebooting will still take you into 11.10 grub menu. Choose 11.10 to boot into, then run update-grub to add the new 14.04 OS to the 11.10 grub menu and finally reboot again to see the new entries (which may look a little odd in the grub menu).

---

### Post by JimLS on 2014-08-09
I think I understand.  The grub entries I have been editing are associated with 11.10 and are not the ones used at boot time (the 14.4 grub is used).  I have been manually selecting 11.10 at boot and then editing grub, which is the wrong grub.

When booting grub displays this at the top of the screen:
GNU GRUB version 1.99-21ubuntu 3.9

Part of the issue is that this box has an old Nvidia 5200(?) card that doesn't work (at least on the output I am using) without some adjustment of the drivers and I haven't figured out exactly what to do about that in 14.4.  It's a mythtv box that is used with a TV.  Sounds like I need to use a regular vga display to boot into 14.4 and make the grub adjustments.  

I know 11.10 is end of life but the system works well.  Some time ago I figured it was time to update the OS so I installed 14.4 alongside of 11.10.  When I ran into video issues I just wanted to use 11.10 until I had more time to sort things out.  Never got back to it but the boot issue causes problems when the power goes out.

I have a newer video card and need to setup MythTV with it in 14.4 but since the old system works fine (except for the boot issue) it hasn't been a priority...

---

### Post by Dennis N on 2014-08-09
> **JimLS said:**
> I think I understand.  The grub entries I have been editing are associated with 11.10 and are not the ones used at boot time (the 14.4 grub is used).  I have been manually selecting 11.10 at boot and then editing grub, which is the wrong grub.

When booting grub displays this at the top of the screen:
GNU GRUB version 1.99-21ubuntu 3.9


Well, this grub menu is not from your 14.04, because the grub version would be 2.02~beta2-9ubuntu1. Use Bashing-Om's command to double-check which OS (by showing the partition) the menu is coming from:

```
sudo grub-probe -t device /boot/grub
```

He has other good advice up there in his post.

You could have made a wrong choice during installation of 14.04 as to where to install grub - it you installed to a partition instead of the MBR, it won't use 14.04's menu since the MBR code would still point to 11.10.

Its better to use the 14.04 grub, since it makes much nicer menus. That menu will include the option to start up 11.10 of course. To use the 14.04 grub, grub has to be reinstalled correctly.

Should you decide to proceed:

You need to boot into the 14.04 OS, and from the terminal use two commands:

Assuming the disk is sda:
```
sudo grub-install /dev/sda
```
and when that completes, 
```
sudo update-grub
```
Important: in the first command, there should be no number with sda.
Finally, reboot to get the new grub menu.

---

### Post by JimLS on 2014-08-12
Attached VGA and got message to update about 500 things in the later OS (turns out it was 12.04 not 14.04).  Desktop didn't work until after update.  Once I had a working 12.04 I was able to update that grub to boot 11.10 as the default.

Still need to update but that's another issue...

---

### Post by Bashing-om on 2014-08-12
JimLS; Good deal ->

That you are now booting . "Still need to update but that's another issue..." you mean 11.10 release ? // It is End_Of_Life and no longer has ANY support //.

If the originating issue is now resolved, please close this thread (solved; top right of post -> thread tools) and 
yes
other issues; open additional thread(s).

[INDENT][INDENT]we do what we can
[/INDENT][/INDENT]

---

### Post by JimLS on 2014-08-12
Update 11.10?  Why would I want to do that?  :) It has complex configured programs that work ok.   I plan to update 12.04. 

But don't get too wound up.  Since I never did much with 12.04 I figure I should change it to 14.04 and set up programs.  Once that's running well I can drop 11.10.

Thread marked as solved.  Thanks!

---

