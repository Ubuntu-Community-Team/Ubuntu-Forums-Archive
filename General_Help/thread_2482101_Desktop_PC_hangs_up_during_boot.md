---
title: "Desktop PC hangs up during boot"
date: 2022-12-19
forum: General Help
---

### Post by Nosphky on 2022-12-19
For around the past three months, I have booted up my desktop every day [UbuntuStudio 2204.1 KDE Plasma] with no problem. I do a Shut Down every night and wait until all activity has ceased before powering off.

Previously, in August/September I had to re-install the OS 3 times because of repeated display problems. This was the subject of another thread in which the problem was explained to me as Wayland having difficulty in cohabiting with some Nvidea display cards. I had never heard of Wayland until that time but the problem was resolved by removing the Nvidea card and using the onboard integrated Intel graphics. The PC has booted using X11 with no further modifications required ever since, until yesterday.

Yesterday, the boot hung up. I saw a few lines of text in the top left of the screen which declared :
> You are in emergency mode. After logging in, type "journalctl -xb" to view
system logs, "systemctl reboot" to reboot, "system ctl default" to "exit"
to boot into default mode.
Press Enter for maintenance
(or press Control-D to continue):

I was in emergency mode. It also gave a few options for continuing: 'systemctl default' got me into a completed bootup.

Today, was worse. None of the options got the boot-up re-going after the hang-up. I used the PC reset button a couple of times and eventually took the boot menu from F12 on the motherboard. Selecting something like Ubuntu additional options got me into a recovery mode bootup with a warning partway that the graphics might be screwed and if so, at the login stage, go for a reboot.

Well, the graphics were really off. Having succeeded in booting up, I didn't dare go for a reboot. The display settings showed that I was in the only available option, 1024 x 768 (4:3) and 76Hz was the only refresh under 'this Wayland display'. So Wayland has again raised its (to me) ugly head again.

Examining the journalctl output gives indications of several issues but the ones which appear most relevant are these: 

On line 3: > Command line: BOOT_IMAGE=/boot/vmlinuz-5.15.0-56-lowlatency root=UUID=c44f59de-3197-4ad5-bae4-18f204488ee2 ro recovery nomodeset

and again on line 336: > Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.15.0-56-lowlatency root=UUID=c44f59de-3197-4ad5-bae4-18f204488ee2 ro recovery nomodeset

On line 337 it said - > You have booted with nomodeset. This means your GPU drivers are DISABLED. Any video related functionality will be severely degraded, and you may not even be able to suspend the system properly. Unless you actually understand what nomodeset does you should reboot without enabling it. Unknown kernel command line parameters "recovery BOOT_IMAGE=/boot/vmlinuz-5.15.0-56-lowlatency", will be passed to user space.

I have no idea what this mention of modes is nor what are the choices, or where one selects a choice. I do wonder if the nomodeset option is down to the use of recovery mode. If so, that could help explain the message warning that if there was a display problem, to reboot when at the login stage. But at the moment, I have a working system albeit with a crap graphics display and I hesitate to do a reboot in case I can't get back in at all.

I saved the content of the output of journalctl -xb, all 6000 lines of it, most of which means not a great deal to me.

Several times a week there are updates offered by the system which I install the same day. It occurs to me that there was some update to GRUB earlier this week. Could that have had something to do with this boot-up trouble? Why, when the hang-up occurred, was I in 'emergency mode'?

Suggestions for fixing this problem will be much appreciated.

---

### Post by MAFoElffen on 2022-12-19
Since you no longer have NVidia installed, you can remove "nomodeset" from the boot line of /etc/default/grub. Remember to rerun 'Update-grub" after that to pick up the change. Then it will use the Intel Graphics drivers in the kernel.

Tell me how that goes, and we'll go from there...

---

### Post by Nosphky on 2022-12-19
> **MAFoElffen said:**
> Since you no longer have NVidia installed, you can remove "nomodeset" from the boot line of /etc/default/grub. Remember to rerun 'Update-grub" after that to pick up the change. Then it will use the Intel Graphics drivers in the kernel.

Tell me how that goes, and we'll go from there...

Thanks for telling me where to look. I just opened /etc/default/grub and there is no mention of 'nomodeset'. These are the only lines that are uncommented:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

and in the other lines, all commented with #, there is no mention of 'nomodeset'. So this is being applied by something else in my attempts to get booted up. Perhaps the default or emergency target, whatever that is?

Just before shutting down for the night, I thought I would try giving the PC a restart - sure enough it hung up with the message I quoted in the first post. I used Control-D to continue, as per the last line of the message, and another warning line in red came up:
> Failed to start default target: Transaction for graphical.target/start is destructive (emergency.target has 'start' job queued, but 'stop' is included in transaction)

Despite waiting several minutes, nothing further happened, so I pressed the PC hardware reset button, used F12 to look at boot options, selected linux and then further linux options. Instead of taking the latest lowlatency version vmlinuz-5.15.0-56-lowlatency, I selected vmlinuz-5.15.0-53-lowlatency.  The boot carried on to completion with the screen graphics display back to what it should be.

So is that significant or chance?  Why when it hangs does the message say I am in 'emergency mode'?  How does one get into emergency mode, why and what does it mean ?  

Tomorrow's another day and I'll try and repeat what I did with vmlinuz-5.15.0-53 to see if it was chance.

---

### Post by MAFoElffen on 2022-12-19
What is your Cpu/Apu? Intel?

---

### Post by Nosphky on 2022-12-20
> **MAFoElffen said:**
> What is your Cpu/Apu? Intel?

The CPU is Intel [FONT=monospace][COLOR=#000000]Intel(R) Core(TM) i5-4440 CPU @ 3.10GHz[/COLOR]
x86-64 on a Gigabyte [FONT=monospace][COLOR=#000000]H97M-D3H[/COLOR] motherboard.

[/FONT][/FONT]

---

### Post by Nosphky on 2022-12-20
Today, I have been looking more closely at the boot possibilities. It would appear that my success yesterday in booting with an older version of vmlinuz was probably due to having changed more than one item in the boot selection.

When I use the PC reset button and hit F12 to see the boot choices, I'm presented with more choices than I expected:
> 1. UEFI ADATA 
2. UEFI OS (P4: WDC WD10EZRX-00A8LB0)
3. ubuntu  (P4: WDC WD10EZRX-00A8LB0)
4. ubuntu  (P4: WDC WD10EZRX-00A8LB0)

1. is an external usb disk used for data backup only and has never been bootable
2. is sdb a hard disk on which the system is installed
3. and 4. are two further options on the same sdb - I don't understand why they're there.

If I go into the BIOS setup and look at boot options and order, there are traces of previous lives: a Windows boot manager (this machine used to be a Windows7/Ubuntu dual boot around Ubuntu16.04 but has been uniquely Ubuntu since around 18.04), then there are the three options I see in the F12 boot menu, one of which is selected as the first option and that is either item 2 or item 3 in the F12 boot menu choice listed above. Since they both have the same name, I don't know which is which or why there are two.

I always use UbuntuStudio LTS versions. Each time I move up to the new one, it is with a clean install and from the warnings given in the install procedure, I understood that the hard disk would be formatted and all existing info destroyed. So I am surprised to see all those boot options. My Home file system is on a separate disk, sda, following suggestions from OldFred some years ago.

First time in the F12 boot menu, I selected item 2, UEFI OS (P4: WDC WD10EZRX-00A8LB0) - this proceeded to hang up with the previously noted messages.

Next, in the F12 boot menu, I selected item 3, one of the boot options labeled ubuntu. This produced a ubuntu boot menu with three choices: Ubuntu Lowlatency, Ubuntu advanced options, UEFI Firmware settings. While taking note of these options, a time-out caused the machine to continue the boot-up, using the first option I presume. This boot-up proceeded to hang up.

I used the reset and F12 again with item 3 but this time I selected Ubuntu advanced. This proceded to show me another dialog with four options: kernel 5.15.0-56-lowlatency and the same in recovery mode, kernel 5.15.0-53-lowlatency and the same in recovery mode.  I selected 5.15.0-56-lowlatency and the boot-up proceded until it hung up in the usual way.

I then reset and went back to the same place and selected the next option: 5.15.0-56-lowlatency recovery mode. This produced a dialog with around 6 choices among which I selected to repair any broken packages, and to repair the GRUB boot. No indication was given of success or failure but after a short time a warning came up that I had seen yesterday about the recovery mode may be screwing up the graphics and necessitating a reboot at login. This proceeded to completion with screwed-up graphics. I used the system (KDE PLasma) prompt to restart and all went well with graphics restored to normal.

So, I conclude that there is no problem inherent in kernel -56 or -53 versions and I seem to have a convoluted way of getting booted up but I still have the F12 menu item 4 to try and I still have not yet investigated the mysteries of the UEFI Firmware settings from the ubuntu boot choices. 

But I still do not know what change provoked the system to start in 'emergency mode' after several months of perfect daily boots.

---

### Post by MAFoElffen on 2022-12-20
me neither, especially the messages about 'nomodeset'... when it was not there(???). I'm not there looking at what is going on. I can only go off what you are describing.

To get rid of the bad entries, you could use 'efibootmgr'... Make sure you review [Ubuntu man efibootmgr]("https://manpages.ubuntu.com/manpages/jammy/man8/efibootmgr.8.html")

I might be able to assist if you posted the results of:
```

sudo efibootmgr -v

```

---

### Post by Nosphky on 2022-12-21
Before shutting down last night, I re-started a couple of times from the KDE Plasma prompt and all went well to completion with good graphics. Today, I have just started the pc normally (turned power on to pc and to screen, hit the start button) and it booted up like it never had a problem.

I can only imagine that the options I pressed during the startup in 'recovery mode' (repair any broken packages, repair Grub boot) must have achieved something although at the time there was no indication that anything was going on.

Although 'nomodeset' was NOT in the file /etc/default/grub,  it was definitely present in the command line as evidenced in the output of ' journalctl' from which I quote this line #336 :

> Dec 19 14:38:15 Osiris kernel: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.15.0-56-lowlatency root=UUID=c44f59de-3197-4ad5-bae4-18f204488ee2 ro recovery nomodeset

Since I had retried several times to boot on that first day, I must have been in recovery mode when that journalctl was logged. I imagine the 'nomodeset' option must have been created dynamically when in recovery mode.

I shall read up on efibootmgr, thanks for that.  In response to your request for the results of ```
sudo efibootmgr -v
```, here they are:

```
[FONT=monospace][COLOR=#000000]$ sudo efibootmgr -v [/COLOR]
[sudo] password for xxx:  
BootCurrent: 0000 
Timeout: 2 seconds 
BootOrder: 0000,000A,000C,000D,0003,0004,0001 
Boot0000* ubuntu        HD(1,GPT,32b9b9c4-3554-8347-8800-29304605bb8c,0x1000,0x96000)/File(\EFI\UBUNTU\SH
IMX64.EFI) 
Boot0001  Hard Drive    BBS(HD,,0x0)AMGOAMNO........o.W.D.C. .W.D.1.0.E.Z.E.X.-.3.5.W.N.4.A.0............
........A...........................>..Gd-.;.A..MQ..L. . . . . . . . .C.W.6.C.3.Y.Y.S.R.5.V.3......AMBOAM
NO.......a.A.D.A.T.A....................A................................Gd-.;.A..MQ..L.4.3.1.1.6.6.5.A.3
.0.8.2......AMBOAMNO........o.W.D.C. .W.D.1.0.E.Z.R.X.-.0.0.A.8.L.B.0....................A...............
............>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.1.C.3.U.2.3.8.3.1.3......AMBOAMNO.........K.i.n.g.s.t.o
.n.D.a.t.a.T.r.a.v.e.l.e.r. .G.3. .1...0.0....................A...................................F..Gd-.
;.A..MQ..L.0.0.1.C.C.0.E.C.3.2.B.C.F.B.8.0.9.7.1.2.2.3.4.5......AMBO 
Boot0003  CD/DVD Drive  BBS(CDROM,,0x0)AMGOAMNO........o.T.S.S.T.c.o.r.p. .C.D.D.V.D.W. .S.H.-.2.2.4.D.B.
...................A...........................>..Gd-.;.A..MQ..L.9.R.E.3.Y.6.D.C.0.C.9.1.E.N. . . . . . .
.....AMBO 
Boot0004  Windows Boot Manager  HD(3,MBR,0x57c4d,0xc382800,0x64000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI
) 
Boot000A* UEFI: ADATA   PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(6,0)/HD(1,MBR,0x3285,0x20,0x3a385fe0)AMBO 
Boot000C* UEFI OS       HD(1,GPT,32b9b9c4-3554-8347-8800-29304605bb8c,0x1000,0x96000)/File(\EFI\BOOT\BOOT
X64.EFI) 
Boot000D* ubuntu        HD(1,GPT,32b9b9c4-3554-8347-8800-29304605bb8c,0x1000,0x96000)/File(\EFI\UBUNTU\GR
UBX64.EFI)[/FONT]
```

In this, you see traces of the historic past of this box when it was at first a dual boot with Windows. You also see '000A' which is the ADATA external usb drive that has never been bootable.  The '000C' [UEFI OS] when I tried it gave the same hang-up that I was experiencing but did not produce the dialog permitting me to select a recovery mode.

The two apperently identical boot options in the F12 motherboard options and in the BIOS, both labeled 'ubuntu' have in fact some detailed differences. The one in use, 0000, seems to use [FONT=monospace]File(\EFI\UBUNTU\SHIMX64.EFI) whereas the other one, 000D, uses [FONT=monospace]File(\EFI\UBUNTU\GRUBX64.EFI).  I'm afraid I don't know the difference between these two.[/FONT][/FONT]

I suppose a lesson I should take from this is that it is not sufficient to make a clean install of a new version of ubuntu. I should either use a new hard disk or remove all partitions from the old disk and reformat. The clean install's warning about all data being lost, evidently does not cover the boot partition.  Is this correct?

For now, all seems to be back to normal but it is troubling not to know what caused the problem and why I was suddenly in 'emergency mode'.

---

### Post by MAFoElffen on 2022-12-21
Here's what I get from your output and from what you said...
```

BootOrder: 0000,000A,000C,000D,0003,0004,0001
 
Boot0000* ubuntu HD(1,GPT)(\EFI\UBUNTU\SHIMX64.EFI) 
Boot0001  Hard Drive    BBS(HD,,0x0)
Boot0003  CD/DVD Drive  BBS(CDROM,,0x0)
Boot0004  Windows Boot Manager  HD(3,MBR,)(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI) 
Boot000A* UEFI: ADATA PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(6,0)
Boot000C* UEFI OS HD(1,GPT,)/File(\EFI\BOOT\BOOTX64.EFI) 
Boot000D* ubuntu HD(1,GPT,) File(\EFI\UBUNTU\GRUBX64.EFI)

## Take off /delete: 0004, 000A, and (maybe) 000C
sudo efibootmgr --delete-bootnum --bootnum 4
sudo efibootmgr --delete-bootnum --bootnum A
# sudo efibootmgr --delete-bootnum --bootnum C  <-- Are you sure???

## Set Boot Order:
sudo efibootmgr -o 0000,000D,0003,0001

```
You said you wanted to take off 3. But you may want to recheck 000C again before deciding that one.

The commands are there if that is how you want it... Your prefrence on what stay and the order of...

When I do a "clean install"., I use the other menu and format the efi partition... Except on newer laptops, where the EFI Setup, Diagnostics, and USB drives are set in the EFI Menu. (BUT a lot of those are in the UEFI BIOS)

Just saying to test them first before removing an entry. Easier to delete than to add back in.

---

### Post by Nosphky on 2022-12-21
Thank you, MAFoElffen. I've read the man pages for efibootmgr and your examples show how changes are made. I'll take off 0004 and 000A and leave the others for more testing in due course.

But for the moment, I'll do nothing more for a few days, waiting to see if the problem reappears.

This problem and exercise have taught me a fair bit but I'm well aware that there's a lot more I don't know.

---

### Post by Nosphky on 2022-12-22
Today, the boot hung up again so I went thro the reboot recovery mode  routine and the rapidly scrolling pages of text on the screen suddenly stopped and I saw the system was trying to find sdd, a  Kingston Datatraveller USB stick. I had noticed last night that this usb  memory stick was still in my hub so I had removed it (correctly using  the systems 'remove safely' option). I stuffed it back into the hub and  the boot completed, but with the usual screwed-up display. I then  re-started and all booted nicely.

Then I recalled that the day before the start of these boot issues, I had been  using Gparted to do some stuff with this usb stick - to clean and  reformat but not to make it bootable. I looked in /etc/fstab and sure  enough, there was an entry for this usb stick. I commented it out,  removed the usb stick, shut down and rebooted with no problem.

My  removable ADATA usb disk did not have an entry in /etc/fstab and that  is always plugged into the back of the pc under the desk. In Ubuntu  16.04, 18.04, 20.04 the ADATA was never automatically mounted at startup. I have a bash script for back up with one of the first items being  to mount the ADATA disk. In 22.04, I noticed that when running this  script there was a protest message to the effect that the disk was  already mounted. 

So there is some different behaviour with  external usbs. I don't often put a removable usb stick in but if I need  to transfer some files to my wife, I may do so. I don't expect such a  file transfer op to make entries in /etc/fstab though. Maybe, I did something with Gparted that I shouldn't have done.

Is it a credible possibility that having an entry in /etc/fstab for a removable disk which is actually not present could provoke a boot problem and cause  'emergency mode' to be instigated?

---

### Post by Nosphky on 2022-12-28
I've now had 6 days with no further boot problems and no-one has contradicted my supposition that an errant entry in /etc/fstab was responsible for my boot problems. So I'm marking this as solved.

---

