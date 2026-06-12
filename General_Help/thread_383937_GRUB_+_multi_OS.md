---
title: "GRUB + multi OS"
date: 2007-03-13
forum: General Help
---

### Post by flimflam on 2007-03-13
OK here goes!  I have been having issues with GRUB and Ubuntu.

Here is my setup (all sata drives)

150 gb RaptorX (sda /scsi 1) Vista (entire disk)
200gb Maxtor (sdb /scsi 2) Mandriva (entire disk)
250 gb WD Caviar (sdc /scsi 3) XP, 1st part / Ubuntu, 2nd part / swap, 3rd part
400 gb Seagate (sdd / scsi 4) Data
500 gb WD Caviar (sdec / scsi 5) Media

BIOS for Vista/Mandriva

#1 - scsi2 Mandriva
#2 - scsi1 Vista
#3 - scsi3

BIOS for XP/Ubuntu (hopeful)

#1 - scsi3 XP/Ubuntu
#2 - scsi1
#3 - scsi2

When I want to boot into Vista or Mandriva I set the Maxtor to disk#2 in the bios, and I can get into the OS Vista or Mandriva fine from the Mandriva GRUB; although I am not sure if it is on the MBR of Vista or not.  Vista uses a Boot Manager and not NTLDR anymore, so I try not to mess with it too much until I gain more knowledge into the Vista boot process.

It would be nice to be able to switch the order of HDs in the BIOS and make sdc the first drive so I can get into XP or Ubuntu.  I tried with GRUB from Ubuntu for all OSes but I think it is too complex and not robust enough to hinge getting into each OS from the Ubuntu GRUB, so I would like to split it into two:  Mandriva/Vista + Xp/Ubuntu.  

If I let Ubuntu install GRUB to the MBR with sdc as #1 I cannot get in.  If I try to specify sdc as the Grub install, I cannot get in.  No matter what I get an error 22: partition doesn't exist.

Any advice or suggestions?

Thanks!:)

---

### Post by Duggeek on 2007-03-13
> **flimflam said:**
> 
150 gb RaptorX (sda /scsi 1) Vista (entire disk)
200gb Maxtor (sdb /scsi 2) Mandriva (entire disk)
250 gb WD Caviar (sdc /scsi 3) XP, 1st part / Ubuntu, 2nd part / swap, 3rd part
400 gb Seagate (sdd / scsi 4) Data
500 gb WD Caviar (sdec / scsi 5) Media


**Egads!** That's a bunch of drives. It only takes three of those drives to hit the 1TB mark for one system, but five? It can be done, I'm sure.

What I'm not sure about is Vista; there's stuff even the ubuntu experts haven't found yet. I *do* know about the new bootloader, but I also know that there's a kaboodle of coders working around that right now. (it may take a while, tho') :( 

I think I heard of a way that Grub (maybe LILO?) can chain to another physical drive at boot. It would be about the same as multi-boot on the same drive, and another plus is that you're not mucking around in the BIOS every time you want to switch.

I'm pretty sure Vista wants to be "first in line" (read: installed as /sda) like other Windows platforms, but Grub/LILO would have to execute first. Maybe this is where your ultra-versatile BIOS comes in handy.

Set-up the drives as:  sda=Vista, sdb=Ubuntu, etc (chained with Vista first)

When you set-up ubuntu, make sure it installs Grub on sdb. Set your BIOS to always boot from /sdb first, then Grub gets to take over. For the Windows Grub-listing, have it boot straight to /sda (not /sda1)

My best guess, to be sure. Anyone else?

---

### Post by flimflam on 2007-03-13
Heh, i didn't even tell you about the 3 74gb Raptors I have on a Netcell RAID card.

Mandriva and Vista are fine through Mandirva's GRUB.  I would like to have Ubuntu and XP go through Ubuntu's GRUB without even involving other physical drives.  So my goal is to just change the drive order and put the XP/Ubuntu drive first in the BIOS, and be able to boot only into Ubuntu or XP - again, Vista and Mandriva are fine and do not even have to be put into the equation.  However, I did mention them to give everyone a full scenario of what is going on in my system.

I have tried thi to no avail thusfar.:confused:

---

### Post by Duggeek on 2007-03-13
Hrm... forgot about the XP part. I think here is where we get to the real problem. 

Obviously, Vista is OK with being "first in line", (/sda) however I'm sure XP is the same way. Aye, there's the rub. How do you make both Windows' boot from the "first" drive?

You're off on the right foot, to be sure. Vista is on first, Mandriva on 2nd, and XP/Ubuntu rounding-up third. (with swap as last partition; as it should be.

Mandriva Grub isn't all that different from Ubuntu, you can chain it pretty easily by adding to Grub menu. 

So long as XP hasn't been rubbed-out with any harsh utilities, you can chain it from there as well without any change in BIOS. (Windows Setup isn't friendly with installing to a secondary drive, but once it is installed, you can put it just about any order)

The only thing I would stick to is having the BIOS point to the drive with Grub; from there, it can pass the bootstrap to any physical drive.

Can your computer run [OpenBIOS]("http://www.openbios.org")?

Since Vista is running its own bootloader, maybe it can be configured into "seeing" the XP partition as well? Then it becomes a "decision tree" at boot time (first choice; opensource or Microsoft, if Microsoft; Vista or XP?, if opensource; Mandriva or Ubuntu?)

It's just an idea of mine, but I'd love to hear how it turns out!

---

### Post by flimflam on 2007-03-14
Thanks for the help  I have to look into openBIOS.  I will definitely report my findings.  It has just been frustrating thas far since I have messed with Fedora on this rig too.  What compounds all of this too is the fact that it is an Intel Core 2 Duo, Aus p5n32-e mobo, and an Evga 8800 GTX.  Because it is such new hardware I have to mess with the xorg.conf, recompile the kernel, install Nvidia drivers, install ALSA drivers, do a forcedeth change to the modprobe, etc just to be able to get X running and for internet for updates.  Heh.

---

