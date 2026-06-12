---
title: "Help getting files off a HDD"
date: 2016-08-05
forum: General Help
---

### Post by silsurf on 2016-08-05
Hello,

I have HDD that was inside my NAS (Iomega Home) which is failing, but spins up, I think the SMART status is calling for imminent failure. It is under the Linux file system so I have been told.

I have removed the HDD from the case and I have a SATA to USB converter and power supply and the disk spins up fine, under OSX it is unrecognizable.

I also have a copy of VirtualBox installed on my Mac OSX and a USB stick with Unbuntu Installer on it.

I just want to copy the contents of the HDD onto a new drive or even my desktop would be fine.

I am hoping to get some support here on how exactly to do this?

TIA

Henry

---

### Post by wildmanne39 on 2016-08-05
*Thread moved to **General Help**.*

---

### Post by &amp;KyT$0P# on 2016-08-05
If you don't already have a virtual machine running Linux, you'll need to create one.  (You presumably know how to install Ubuntu in a VM and add Guest Additions.)

Plug your SATA to USB converter in the computer (probably doesn't need the disk attached for this step) and use it to create a device filter on your Linux VM: Settings > USB > Device Filters > Add (the green +) > Select your converter
You can choose whether to repeat that procedure for a (good) external USB disk or just use a shared folder to receive the data.  Not sure which would be faster.

Now, after booting your Linux VM, you should be able to plug in the adapter with the disk attached and it will be plugged into the Linux VM not the host. (Again, consider to use [FONT=Courier New]lsusb[/FONT] in the VM to first verify that it works without the disk attached, just to be safe.)

Does this help?

---

### Post by silsurf on 2016-08-05
"[COLOR=#000000]You presumably know how to install Ubuntu in a VM and add Guest Additions."

ahh, nope!

I would love some help on that matter or a pointer to a good tutorial, please[/COLOR]

---

### Post by &amp;KyT$0P# on 2016-08-06
Do you still have the ISO image you used to make the Ubuntu USB stick?  If not, you'll need to download an ISO image of Ubuntu to use for the VM.

[Sections 1.7 and 1.8 of the manual]("https://www.virtualbox.org/manual/ch01.html#gui-createvm") give a tutorial on creating a VM and running it.  [This part]("https://www.virtualbox.org/manual/ch04.html#idm1948") explains the Guest Additions for Linux VMs.

---

### Post by silsurf on 2016-08-06
thanks, I think I have enough info to get started. Appreciate your support

---

### Post by &amp;KyT$0P# on 2016-08-06
You're welcome, let us know how it turn out.  :KS

---

### Post by silsurf on 2016-08-07
[IMG]http://imgur.com/g9fsxXr[/IMG]

I have the VM running but cannot find the USB Device Filter in the System Settings?

I tried to embed a screenshot from imgur, but it did not take?

---

### Post by &amp;KyT$0P# on 2016-08-07
You embedded the link as an image instead of leaving it as a link.  Just replace img tags with url tags in your post and it'll work fine.

I'm referring to VM settings (on your host's VirtualBox - this is not inside the guest).

---

### Post by silsurf on 2016-08-07
Ah,

thanks again.

The VM is running. I set the USB in VirtualBox Devices Ports System Settings

Checkbox USB Controller: Radio Box USB 1.1 (OHCI) Controller: Device JMicron USB to ATA/ATAPI bridge (0100) (that is the only controller I see that is not a printer or iSight, Bluetooth, Keyboard or Printer.

If I plug in the SATA adapter while VirtualBox is running I dont see anything change in the USB settings.

If I select USB 2.0 a warning comes up in VirtualBox that Oracle VM VirtualBox Extension Pack to be installed.

When I boot Unbuntu I see activity in the VM icons for USB with a green light, but when I plug in the SATA Linux drive nothing happens? I am not sure where to even look for that device? It does not show up on the desktop.

Thanks, I think I am getting closer?

Henry

---

### Post by &amp;KyT$0P# on 2016-08-08
Sorry, silly me to assume you already had Extension Pack installed. #-o
You need to download and install exactly the same version of Extension Pack as VirtualBox version (shut down all running VMs first).  What VirtualBox version are you using?

---

### Post by silsurf on 2016-08-08
Oracle VM VirtualBox Manager 5.1.2, © 2007-2016 Oracle Corporation

I installed from this link: 
[LIST]
[*]**VirtualBox 5.1.2 for OS X hosts** [ amd64]("http://download.virtualbox.org/virtualbox/5.1.2/VirtualBox-5.1.2-108956-OSX.dmg")
[*]But I dont see the Extension Pack with the same version #, there are two downloads *If you are using **[VirtualBox 5.0.26]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_0")**, please download the extension pack*
[*]
[*]*If you are using **[VirtualBox 4.3.38]("https://www.virtualbox.org/wiki/Download_Old_Builds_4_3")**, please download the extension pack*
[/LIST]
*&#8203;I assume it is the first one, but my assumptions are not always spot on!!*

---

### Post by &amp;KyT$0P# on 2016-08-08
Your Extension Pack from this link [Oracle_VM_VirtualBox_Extension_Pack-5.1.2-108956.vbox-extpack]("http://download.virtualbox.org/virtualbox/5.1.2/Oracle_VM_VirtualBox_Extension_Pack-5.1.2-108956.vbox-extpack")

---

### Post by silsurf on 2016-08-08
yeah, didnt like the 5.0.26 extension pack? 

Failed to install the Extension Pack **/Users/henrycline/Downloads/Oracle_VM_VirtualBox_Extension_Pack-5.0.26-108824.vbox-extpack**.
VBoxExtPackRegister returned VERR_VERSION_MISMATCH, pReg=0000000000000000 ErrInfo='VirtualBox version mismatch - expected 5.0 got 5.1'.
[TABLE="width: 100%"]
[TR]
[TD]Result Code: [/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component: [/TD]
[TD]ExtPackManagerWrap[/TD]
[/TR]
[TR]
[TD]Interface: [/TD]
[TD]IExtPackManager {edba9d10-45d8-b440-1712-46ac0c9bc4c5}[/TD]
[/TR]
[/TABLE]

---

### Post by &amp;KyT$0P# on 2016-08-08
Did we collide posting?  Try using the link I posted above.  It's also listed on the download page as > **VirtualBox 5.1.2 Oracle VM VirtualBox Extension Pack**  _All supported platforms_

---

### Post by silsurf on 2016-08-08
[COLOR=#000000][INDENT]Your Extension Pack from this link [Oracle_VM_VirtualBox_Extension_Pack-5.1.2-108956.vbox-extpack]("http://download.virtualbox.org/virtualbox/5.1.2/Oracle_VM_VirtualBox_Extension_Pack-5.1.2-108956.vbox-extpack")

that worked

Now, does that mean I should select USB 1 or USB 2? And after that when I boot up the VM, where would I look for the HDD?

Thanks[/INDENT]
[/COLOR]

---

### Post by &amp;KyT$0P# on 2016-08-08
Select either USB 2 or 3 - whichever your host (Mac) has.  Unless your device is USB 2, or you're using a USB 2 hub, I'd suggest to try USB 3 first.

---

### Post by silsurf on 2016-08-08
when the USB 3 was chosen, it seemed the VM choked, got a bug software lockup and no boot.

I backed off to USB 2 and rebooting now. Still unclear where I even look for the attached drive?

In the VM settings it says USB Controller: OHCI, EHCI Device Filters: 1 (1 active)

Unbuntu is up and running, no sign of attached HDD. When I close out of VM I get the OS X dialog telling me that the attached drive is unrecognizable.

---

### Post by &amp;KyT$0P# on 2016-08-08
With the device attached to the VM, please open a Terminal inside the Ubuntu VM and post the output of this command
```
lsusb
```

---

### Post by silsurf on 2016-08-08
I downloaded Guake and installed, ran lsusb and got back

Bus 001 and Bus 002 Device info

I would copy and paste, but my OSX command (command-c) invokes something different on the VM

---

### Post by &amp;KyT$0P# on 2016-08-08
Use the Control key instead of Cmd for inside the VM

EDIT Oops, Ctrl-C isn't Copy when in a Terminal window.  It would be either Ctrl-Shift-C or you need to right-click > Copy.
You can also go this route - dump the output in a file
```
lsusb > somefile.txt
```
then open somefile.txt and copy from that text editor (where Ctrl-C should work to copy).

---

### Post by silsurf on 2016-08-08
thanks, gotta go to work now so I will get back to this later. Thanks so much for your support and help in the matter.

---

### Post by &amp;KyT$0P# on 2016-08-08
You're welcome.
(See my above edit, I forgot something about keyboard shortcuts in Terminals :oops: )

---

### Post by silsurf on 2016-08-10
[https://www.dropbox.com/s/p7hqwf7u8r737l5/Screenshot%202016-08-10%2014.56.54.png?dl=0](https://www.dropbox.com/s/p7hqwf7u8r737l5/Screenshot%202016-08-10%2014.56.54.png?dl=0)


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 80ee:0021 Virtualbox USB Tablet
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


This is the response after typing lsusb in terminal

Any thoughts?

Henry

---

### Post by &amp;KyT$0P# on 2016-08-10
I think that means it's not seeing the device.  If it's plugged in your host as USB 3 it won't show in the guest which only has USB 2.

Do you have a USB 2 hub or can you buy or borrow one?  Because since giving the guest USB 3 doesn't work, that's probably the only way to get access to this disk without doing a bare-metal installation of Ubuntu on your Mac (which I know from experience is really tricky to get right and I don't even remember everything I had to do to make it work in my case).

---

### Post by silsurf on 2016-08-10
One thing I will try tomorrow is doing the same thing on my laptop, I have had other issues with USB on my desktop as it is slightly older. The SATA device bridge is USB 2, I purchased it solely for this task.

---

### Post by silsurf on 2016-08-11
I used [this post]("http://www.tomshardware.com/forum/266110-32-recovering-data-dead-iomega-networked-media-storage") to initially try and get my data back:

"[COLOR=#070F14][FONT=Verdana]- the key to the recovery is that the drive is using Linux filesystem, the data is not lost and the drive is still functional (just the NAS operating system is malfunction).[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Tool that you need:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]- Ubuntu CD to boot the laptop to run Linux[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]- Sabrent SATA-C35U Serial ATA to USB 2.0 Cable Converter Adapter with Power Supply[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]How:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]- boot the laptop with the Ubuntu CD[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]- connect the Iomega drive with the Sabrent USB converter[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]- connect the USB and the new Filesystem should be automatically mounted and show up in the home folder.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Good luck."

That is how I wound up with this particular SATA adapter cable and how I wound up on this thread. [/FONT][/COLOR]

---

### Post by silsurf on 2016-08-15
When I use my laptop I get this additional line from the lsusb command

[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 002 Device 002: ID 80ee:0021 Virtualbox USB Tablet[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/COLOR][COLOR=#ff0000][SIZE=3]
Bus 001 Device 002: ID 152d:2329 JMicron Technology Corp. / JmMicron USA Technology Corp. JM2 0329 SATA Bridge[/SIZE][/COLOR]

Isn't that the SATA device I have been searching for? If it is (finger crossed) how do I access it?

Henry

---

### Post by &amp;KyT$0P# on 2016-08-15
Sure looks like it to me 8-)
If the disk doesn't now "just show up" in your Ubuntu VM, I'd next install Gparted and/or Disks (aka gnome disks) inside the VM and take a look to see if it even gets listed and if so how. **Do NOT format the disk or otherwise make any changes!  Doing so at this stage has big data loss risk!**
(You're using Ubuntu 16.04 right?)

---

### Post by silsurf on 2016-08-16
hmm, I see the drive in "disks"

Model# = visible
Size = (just a dash - )
Serial Number = visible
Assessment = Disk is OK One bad sector
Device = /dev/sdb

I dont see it all the time. It mounted in "disks" only after multiple times of plugging in and out the USB cable, trying different ports, etc. One of the those times it just "showed up" in Disks.

---

### Post by &amp;KyT$0P# on 2016-08-16
That looks bad, so extra safety precautions might be wise.  Create a mountpoint if you haven't already:
```
sudo mkdir -p /mnt/xyzzy
```
When it shows up in Disks, click on the partition with the desired data and look at the exact /dev/sdbN path.  Use that to mount:
```
sudo mount -v -o ro /dev/sdbN /mnt/xyzzy
```
This mounts it read-only (mostly anyway - refer to man page of mount for more information).

If that worked now try to copy your data and hope...

---

