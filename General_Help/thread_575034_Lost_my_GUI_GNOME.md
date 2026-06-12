---
title: "Lost my GUI GNOME"
date: 2007-10-13
forum: General Help
---

### Post by reheat on 2007-10-13
**Lost my GNOME GUI in partition resizings**

My current configuration: Dual-boot
	Ubuntu 6.10, Edgy Eft kernel: 2.6.17-12-generic
	MS WinXP Home SP2
	
My ultimate goal: restore the awesome functionality of an Ubuntu installation.

My current objective: repair startup to GNOME desktop login.

My current OS: Ubuntu 6.10 LiveCD and WinXP Home SP2

My current state: 
When I login at the CLI login prompt, the following lines fill the screen:

	[FONT="System"]-bash: /dev/null: Permission denied
	-bash: /dev/null: Permission denied
	-bash: /dev/null: Permission denied
	-bash: /dev/null: Permission denied[/FONT]
until I enter Ctrl-c, which yields a command prompt:

	[FONT="System"]all4one4n@ubuntu:~$[/FONT]

    I can remove splash parameter from default GRUB entry, then boot, which results:

		[FONT="System"]No directory, logging in with HOME=/
		-bash: groups: command not found
		all4one4n@ubuntu:/$[/FONT]

Looks like something is missing location of, or path to [FONT="System"]/home[/FONT] :confused:

How I brought this once proud system to this state: 
	To make the story short; I resized a couple WinXP partitions with an app that suddenly froze, and caused a partition to be "corrupted". Upon reboot GRUB halted with 
	[FONT="System"]Error 15 Unable to find file...[/FONT] :mad:
	
I proceeded to follow the following threads and How To(s)

	Recovering Ubuntu after installing Windows 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

	How to restore Grub from a live Ubuntu cd
[URL="http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+restore"]http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+restore
[/URL]
	HOWTO: Restore GRUB (if your MBR is messed up)
[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")


Everything was running great, then I needed to work on (edit) some Adobe® Flash™ files, but was unable to find a FOSS/Libre software application equivalent, so I proceeded to boot WinXP, and use Partition Magic™ which suddenly froze while shrinking and caused that logical NTFS partition to be "corrupted". Upon reboot GRUB halted with 
	[FONT="System"]Error 15 Unable to find file...[/FONT] :(

I eventually learned to fix GRUB's root entries, which had somehow been changed to a non-bootable partition. 

[LIST]
[*]menu.lst
[*]fstab
[*]fdisk -l
[/LIST]

Ubuntu will now boot to command line login. So how do I get back into the GNOME desktop/GUI? Can I try [FONT="System"]startx[/FONT]?

---

### Post by reheat on 2007-10-13
bump

---

### Post by louieb on 2007-10-14
Did you try startx? Can't hurt
also try
```
sudo /etc/init.d/gdm

```

---

### Post by strabes on 2007-10-14
Can you boot up into windows? You had two separate partition managers crash **while resizing?** I'd say that your installations are toast.

---

### Post by reheat on 2007-11-30
Thanks for your timely help. (Yes, no problem booting WinXP Home SP2).

I tried:
[FONT="System"]startx[/FONT]

The output:
[FONT="System"](EE)xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
No core pointer

Fatal server error:
failed to initialize core devices
(**) RADEON(0): RADEONLeaveVT
[/FONT]
followed by several more messages about the Radeon device, concluding with...

[FONT="System"](**) RADEON(0): Ok, leaving now...
XIO:fatal IO error 104[/FONT]

Then returned to the command prompt

I also tried:
[FONT="System"]sudo /etc/init.d/gdm start[/FONT]

The output:
[FONT="System"]* Starting GNOME Display Manager [ok][/FONT]

Then froze up.

After several weeks of getting my work done; using Edgy 6.10 Live CD, I did install Gutsy 7.10 - and am lovin' it! 
The best news (to me) is that FOSS/Libre software applications equivalent to Adobe® Flash CS3&#8482; exist - search for swf in Synaptic Package Manager.
Again, thank you for your support and encouragement when I really needed it.

---

