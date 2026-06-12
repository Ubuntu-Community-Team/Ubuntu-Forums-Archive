---
title: "Kubuntu 23.10 crashed, now I can't mount HDDs. How to fix?"
date: 2023-11-05
forum: General Help
---

### Post by ancapistan on 2023-11-05
I just did a fresh install of Kubuntu 23.10 on my computer using a bootable USB. The Kubuntu operating system is installed on an SSD (/dev/sdb), and the computer also has a couple of HDDs that are formatted in NTFS for use as data storage (/dev/sdc1 and /dev/sdd1). 

So I'm on the computer, watching videos on YouTube and copying some files from one of the HDDs to the SSD, when the computer suddenly freezes. It did that kind of hard freeze where everything becomes totally nonresponsive and a small snip of audio from YouTube is repeating over and over. Mouse cursor won't move. Keyboard commands do nothing. Not even the numlock key will toggle. I wanted to avoid pushing the hard reset button if at all possible, but nothing was responding. I even tried unplugging the keyboard and plugging it back in. The keyboard is backlit but it wouldn't even power on upon plugging back in. 

Reluctantly, I hit the hard reset button on the computer. It booted back up and I logged into Kubuntu as normal. I immediately opened Dolphin and checked the drives. The SSD mounted just fine. But when I try to mount the HDDs or look at them in Dolphin, both of them throw an error that says, 

**"An error occurred while accessing [HDD], the system responded: The requested operation has failed: Error mounting [/dev/sdc1 or /dev/sdd1] at [/media/ancapistan/HDD]: wrong fs type, bad option, bad superblock on [/dev/sdc1 or /dev/sdd1], missing codepage or helper program, or other error"**

The first thing I did was look around the help section on the Ubuntu website and I found this: 

[https://help.ubuntu.com/stable/ubuntu-help/disk-repair.html.en](https://help.ubuntu.com/stable/ubuntu-help/disk-repair.html.en)

But the page refers to a "Disks" tool in the "Activities" overview and I don't see anything like that on my Kubuntu installation. What tools can I use in Kubuntu to do these repairs? 

Next, I installed GSmartControl and did the short self test and it found no errors on either HDD. But they still won't mount. 

These HDDs are only a couple years old and have never given me any problem before. [COLOR=#000000]I think this system crash messed them up, but the data should still be there. [/COLOR]I can't lose the data on these drives. What can I do to repair them and get them to mount? I very much appreciate any help you can provide.

---

### Post by MAFoElffen on 2023-11-05
Let's get this clear first... The HHD's that you cannot mount are external USB or internal SATA drives? They were both mounted temporarily at /media/ancapistan/<device_name> ad you were in the process of copying files from it to your ssd right? So just reading from them... Not writing "to them" right?

Could you please post the output of these posted within CODE Tags?
```

lsblk --noheadings --bytes --pairs --output=ALIGNMENT,DISC-ALN,FSTYPE,FSUSE%,GROUP,KNAME,LABEL,MODE,MODEL,MOUNTPOINT,NAME,OWNER,PHY-SEC,SIZE,STATE,TYPE /dev/sd[c,d]

```

Is this machine a dual-boot with Windows?

---

### Post by ancapistan on 2023-11-05
The HDDs are both internal SATA drives. I think I was actually writing to one of the HDDs while I was also reading from another. So one of the HDDs was doing some writing. 


Yes the machine is a dual boot with Windows 10. The Windows OS resides on a separate physical SSD (/dev/sda). I can mount and see the Windows SSD in Dolphin just fine. However, the install of Kubuntu 23.10 caused the computer to be unable to boot to Windows. I think it might be a UEFI issue. I was planning to diagnose that issue but this crash and HDD mount thing happened in the meantime and I consider it more urgent. 


Below is the output of the commands you provided:


ALIGNMENT="0" DISC-ALN="0" FSTYPE="" FSUSE%="" GROUP="disk" KNAME="sdc" LABEL="" MODE="brw-rw----" MODEL="TOSHIBA HDWR180" MOUNTPOINT="" NAME="sdc" OWNER="root" PHY-SEC="4096" SIZE="8001563222016" STATE="running" TYPE="disk"
ALIGNMENT="0" DISC-ALN="0" FSTYPE="ntfs" FSUSE%="" GROUP="disk" KNAME="sdc1" LABEL="Storage2" MODE="brw-rw----" MODEL="" MOUNTPOINT="" NAME="sdc1" OWNER="root" PHY-SEC="4096" SIZE="8001558675456" STATE="" TYPE="part"
ALIGNMENT="0" DISC-ALN="0" FSTYPE="" FSUSE%="" GROUP="disk" KNAME="sdd" LABEL="" MODE="brw-rw----" MODEL="WDC WD2002FAEX-007BA0" MOUNTPOINT="" NAME="sdd" OWNER="root" PHY-SEC="512" SIZE="2000398934016" STATE="running" TYPE="disk"
ALIGNMENT="0" DISC-ALN="0" FSTYPE="ntfs" FSUSE%="" GROUP="disk" KNAME="sdd1" LABEL="Storage" MODE="brw-rw----" MODEL="" MOUNTPOINT="" NAME="sdd1" OWNER="root" PHY-SEC="512" SIZE="2000396746752" STATE="" TYPE="part"

---

### Post by MAFoElffen on 2023-11-05
Since it "is" a dual boot, I would run "chkdsk /f" on both of them from inside Windows. (from an Admin  Command prompt or from Powershell) NTFS is native to Windows and they deal with their own filesystem better, in ways that will keep the capability going.

After that, boot back over and try to mount them again...

---

### Post by ancapistan on 2023-11-05
Yeah I also thought that running chkdsk from Windows would be the safest way to go. But I currently cannot boot to Windows. I've been playing around with GRUB but cannot get it to recognize the Windows OS. Windows was set up as a legacy boot, and when I installed Kubuntu 23.10 I did it UEFI style with the boot loader installed on the Kubuntu SSD (/dev/sdb). The internet is telling me that GRUB won't detect legacy Windows if it's set up for UEFI. 

Running update-grub doesn't fix it, and running os-prober doesn't find the Windows OS.

Even if I set the Windows SSD as the first boot priority in the BIOS, it doesn't boot up.

---

### Post by MAFoElffen on 2023-11-05
So it has not booted since you installed Kubuntu right?

The other way to possibly do that would be to add a custom boot entry to your menu through manually adding it to /etc/grub.d/40_custom file as a 'chainload', sort of like this... You would have to figure out the disk info for it
```

menuentry 'Windows 7' {
insmod part_msdos
insmod ntfs
set root='(hd0,0)'
chainloader +1
}

```
That used to work, though I haven't done that in many years.

---

### Post by oldfred on 2023-11-06
UEFI & BIOS/Legacy/CSM are not compatible.
I do not think grub in UEFI mode can boot Windows in Legacy. You only can boot directly from UEFI boot menu and that should work. You may have to change default boot mode from UEFI to BIOS, but many systems just boot an entry in correct mode, now.

The rEFInd boot loader seems to be able to boot a BIOS install from UEFI. Some how it causes a reboot & switch to BIOS mode. Not sure how that works and grub (unless newest added it) does not do that.

If both installed on same drive, it is a bigger issue. Most drives can only have one boot flag. 
Boot flag is a Windows requirement on the partition with the boot files, not necessarily the main ( c: drive) partition.
But UEFI has boot,esp flags on ESP. Or you may have to move boot flag to Windows boot partition to boot Windows.
Then move it back to boot Ubuntu.
Best to always install in same boot mode, and really required if on same drive.
If system is UEFI, usually better to use UEFI boot for all installs. But Windows requires MBR for BIOS boot and gpt for UEFI boot.
Ubuntu allows UEFI install on MBR which it really should not. 
Conversion from MBR(msdos) to gpt totally erases a drive, so good backups required.

---

### Post by ancapistan on 2023-11-07
MAFoElffen and oldfred, thank you for the helpful replies. This gives me a good amount to go on. I'll play around with it and come back if I still need help.

Basically my game plan is to get Windows 10 to boot again by playing around with the boot/UEFI/BIOS settings, then run chkdsk on the HDDs.

---

### Post by MAFoElffen on 2023-11-07
Sounds like a good plan. Good luck.

---

