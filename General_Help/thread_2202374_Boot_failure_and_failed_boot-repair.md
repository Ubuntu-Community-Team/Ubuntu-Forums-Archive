---
title: "Boot failure and failed boot-repair"
date: 2014-01-28
forum: General Help
---

### Post by ibates on 2014-01-28
After a couple of years, the "inevitable" seems to have happened.  A failure to boot Ubuntu 12.04 LTS updated.  GRUB works OK, but half way through the system loading process everything goes belly-up stuck on repeating a failed step.  I have regular daily backups, but restoring backups is a tedious and generally unrewarding exercise at the best of times.

I have updated boot-repair and run it.  It tells me that the boot error has been fixed and has given me a "paste" file which I will list here to assist with any technical advice.  I rather expect that there was never a problem with the boot, but for some reason (it's Wednesday for example), the boot partition has given up the ghost.  Please note; the Paste file makes reference to Windows XP which is installed on a completely separate HDD to Ubuntu, which itself on its own separate HDD.  It is booting from the GRUB menu and operating without fault.

[http://paste.ubuntu.com/6834676](http://paste.ubuntu.com/6834676)

But the second part of the query is that if, as the paste suggests, there is in fact a "broken" partition, and I suspect there is no practical way to repair a "broken" partition (is there?), if I need to re-install Ubuntu 12.04 LTS system, can this be done without losing the data structures existing on the HDD?  Or can the HDD partition itself be repaired *in situ* without loss of existing folders and files?

Or is this mere wishful thinking?

---

### Post by oldfred on 2014-01-29
If you get working grub menu, you usually are past the issues that Boot-Repair can fix.

I also do not like that Boot-Repair auto installs one grub to every MBR on multiple drive systems. I prefer each drive have a system and that system's boot loader be in that drive's MBR. Then you can boot any drive from MBR.
I would use Advanced tab in Boot-Repair and reinstall a Windows boot loader to sdc.

You may want to houseclean as you have a lot of kernels.

It also seems to have issues with sdb. It shows a UUID and format on the drive, as if it was not partitioned? Or is that an error? You should always have partitions otherwise it may be seen as a superfloppy and default mounts would not work.

But even with an error on mounting sdb, I would think you should be able to skip that and boot.

---

### Post by jeanjd63 on 2014-01-29
Hello

Your file /etc/default/grub is here :
> [COLOR=#008800]*# If you change this file, run 'update-grub' afterwards to update*[/COLOR][COLOR=#008800]*# /boot/grub/grub.cfg.*[/COLOR]
[COLOR=#008800]*# For full documentation of the options in this file, see:*[/COLOR]
[COLOR=#008800]*#   info -f grub -n 'Simple configuration'*[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR]0
[COLOR=#008800]*#GRUB_HIDDEN_TIMEOUT=0*[/COLOR]
[COLOR=#B8860B]GRUB_HIDDEN_TIMEOUT_QUIET[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s 2> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo [/COLOR]Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#008800]*#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  This line replaced by*[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash no modeset video=uvesafb:mode_option=1600x1200-24,mtrr=3,scroll=ywrap"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]

[COLOR=#008800]*# Uncomment to enable BadRAM filtering, modify to suit your needs*[/COLOR]
[COLOR=#008800]*# This works with Linux (no patch required) and with any kernel that obtains*[/COLOR]
[COLOR=#008800]*# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)*[/COLOR]
[COLOR=#008800]*#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"*[/COLOR]

[COLOR=#008800]*# Uncomment to disable graphical terminal (grub-pc only)*[/COLOR]
[COLOR=#008800]*#GRUB_TERMINAL=console*[/COLOR]

[COLOR=#008800]*# The resolution used on graphical terminal*[/COLOR]
[COLOR=#008800]*# note that you can use only modes which your graphic card supports via VBE*[/COLOR]
[COLOR=#008800]*# you can see them in real GRUB with the command `vbeinfo'*[/COLOR]
[COLOR=#008800]*#GRUB_GFXMODE=640x480  Changed to*[/COLOR]
[COLOR=#B8860B]GRUB_GFXMODE[/COLOR][COLOR=#666666]=[/COLOR]1600X1200-24
[COLOR=#008800]*#GRUB_GFXPAYLOAD_LINUX=1280x1024x32 Earlier modification*[/COLOR]

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]
[COLOR=#008800][I]
[/I][/COLOR]



This line seems bad :
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash no modeset video=uvesafb:mode_option=1600x1200-24,mtrr=3,scroll=ywrap"
[/COLOR]i prefer :

[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash **nomodeset** video=uvesafb:mode_option=1600x1200-24,mtrr=3,scroll=ywrap"

[/COLOR]Can you first correct this :
**sudo  gedit  /etc/default/grub**
and after saving this do a
[B]sudo  update-grub

[/B]Bye[COLOR=#BB4444][/COLOR][COLOR=#BB4444][/COLOR]

---

### Post by ibates on 2014-01-29
Thanks for that Fred.  It does not seem as though it is apparent from what you have written, but I believe that Windows is booted from its own MBR (on its own drive), and Ubuntu was booted from its own MBR (on its own drive).

And yes, you are absolutely correct about the house keeping.  Very sloppy on my part.

The drive showing an UUID is probably not partitioned.  It is a backups drive and is mounted independently of the other drives.  No need for a partition on that drive methinks.

Once again thanks.  Much appreciated.

---

### Post by ibates on 2014-01-29
Reply to JeanJD63:

Many thanks for that advice.  I am having difficulty working out just how I should about editing the GRUB file on the HDD from which I can't boot when I can only get into that drive by booting from the LiveCD.  The terminal I get then does not give me access to the HDD I cannot boot from, thus I cannot edit the GRUB.

I assume therefore that I would not be able to update the GRUB either.

Any suggestions.  (Apologies if that doesn't sound very smart, but technically, I am not - very smart that is).

---

### Post by jeanjd63 on 2014-01-30
You can do this in dynamics method.
When you have the menu grub, on the first line, you press "e" like "Edit" and you will have some lines:
you go to the line :
[COLOR=#000000]linux    /boot/vmlinuz-3.2.0-58-generic-pae [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#000000]f611205f-0359-4f8d-8a74-fdcd2d04239c ro   quiet splash **no modeset **.........
[/COLOR][COLOR=#000000]and you changes [/COLOR]**no modeset**[COLOR=#000000] by [/COLOR]**nomodeset**[FONT=Verdana]Then you valid doing CTRL+X or F10.
If your computer boot, you do commands of post #3[/FONT]

---

### Post by ibates on 2014-02-01
Firstly, for jeanjd63; I tried the suggestions you made, but nothing changed.

It is now completely obvious that the problem is not with GRUB, it is doing exactly what it is supposed to do.  The problem is much more sinister and clearly lies with the loading of Linux and its required files.

My question now is - are there any logs which could have been created, or which could be created, to list the step by step process of the loading up until the point at which it stops?  There are hundreds, if not thousands of lines, which flash down the page when I attempt to load *Linux ...... -generic-pae (recovery mode)*, but because the system has not loaded, I cannot print the list nor can I save it.  The same stopping point is reached even when not booting in *Recovery mode*.  There are no problems booting from the LiveCD.

Once booted from the liveCD, I can access all my files on the HDD, but cannot run any applications.  Even Terminal opens only those files which were created during the boot up from the LiveCD.

I have also attempted to boot up using *previous versions* but with the same results.

Anyone with further suggestions would be greatly appreciated.

---

### Post by jeanjd63 on 2014-02-02
You can try to boot on old kernel, you choose :
[COLOR=#BB4444]"Previous Linux versions"
[/COLOR][COLOR=#000000]and then
[/COLOR][COLOR=#000000]'[/COLOR][COLOR=#BB4444]Ubuntu, with Linux 3.2.0-57-generic-pae'
[/COLOR]or older kernels[COLOR=#BB4444][/COLOR]

---

### Post by oldfred on 2014-02-02
If you get grub menu then other boot parameters like nomodeset are required, Some computers need several and it often can be difficult to know unless you find someone else with a similar computer who found the correct boot parameters. You already had several, and at least one looked wrong. Did it boot before with that set of parameters?

There are many log files, but dmesg is the one with the same info as you see on screen. 

 From live DVD/Flash drive - Change example sda6 to your Ubuntu partition
sudo mount /dev/sda6 /mnt
gksudo gedit /mnt/var/log/dmesg

or if you can boot to a terminal.
sudo nano /var/log/dmesg

---

### Post by ibates on 2014-02-02
Reply to post #9.

Yes; it always has booted normally with this setup for some time now.  Certainly months, perhaps even a year or more.  There have been no changes (of which I am aware).

But there is one thing which I have noticed which may be of interest.  Immediately prior to the boot process stopping, the last few lines displayed refer to */opt/default/arkeia/....*  This is unusual, because although some time ago, probably a couple of years, I did download and install *Arkeia Enterprise Backup*, but having decided it was not appropriate for my requirements, it was *completely removed*.  As far as I was concerned it had gone.

But when booting from LiveCD, and looking at the */opt/default/* folder on the HDD, sure enough, there is a folder *arkeia* within which there are several other folders, all with contents.  They must have been there for years unknown to me, and just why the system would now be attempting to include *arkeia boot* in the overall booting process is beyond me.

I have attempted to remove that *arkeia* folder, but have been unsuccessful.  I have attempted it through booting from the HDD in *recovery mode* and then dropping to root level, but perhaps through my lack of understanding of how to remove those folders, I have been unable to do so.  Permissions is the issue it seems.

I will now attempt to locate and post those log files.

---

### Post by ibates on 2014-02-02
Attached is the dmesg file.[ATTACH]250038[/ATTACH]

---

### Post by oldfred on 2014-02-02
I this these, but do not know about many things going on in booting.

 sde: unknown partition table
EXT4-fs (sdd1): orphan cleanup on readonly fs

   init: lightdm main process (1436) killed by TERM signal

It looks like sde has some issues. and sdd1 has issues.

It does look like nvidia loaded ok, but then lightdm just does not want to start. 
How did you install nvidia, from nVidia or ppa or from Ubuntu repository?

---

### Post by ibates on 2014-02-03
Reply to Post #12.

The Device (HDD) sde is an independent 2 TB backup HDD, dedicated to only backups and nothing else.  It appeared to be operating well prior to the failure.  There is not too much on it so when things get straightened out, I can certainly put a single partition on it.

*EXT4-fs (sdd1): orphan cleanup on readonly fs*.  Now this is more interesting.  SDD1 is the Ubuntu 12.04 boot partition.  So it could be reasonable to assume that that is where the problem lies.

*init: lightdm main process (1436) killed by TERM signal*.  What can this mean?

Although issues with sde are not obvious at this point in time, there certainly does seem to be issues with sdd1 (see above).  But what can those issues be?  Device sde is actually a removable HDD (mounted in a removable chassis rack) and as such I will now remove it and try the boot again.  That will remove that issue from the process one way or another.

nVidia was installed from Synaptic as best I can remember.  It has not been changed for some weeks, or even months.

Are we getting any closer to a solution?  Anyone?

---

### Post by oldfred on 2014-02-03
I would try fsck on sdd1, change example below to sdd1.

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

That lightdm does not start usually a video driver issue, but if partition has corruption that may also be an issue.
AFter fsck, if it does not work, try recovery mode or adding nomodeset.

---

### Post by ibates on 2014-02-03
All fsck actions have been executed with no errors or warnings whatsoever.

I am now opening a new Thread on this topic since it is clear that there does not appear to be any problem with booting, but there is a problem with Start-up.  A FATAL error message has been detected during the start-up procedure and hopefully we can take it from there.

The new thread will be under an Ubuntu prefix, and entitled, Start-up failure Ubuntu 12.04.

Thanks for all the assistance so far.

---

### Post by oldfred on 2014-02-06
Closed: See this thread.
[http://ubuntuforums.org/showthread.php?t=2203962](http://ubuntuforums.org/showthread.php?t=2203962)

---

