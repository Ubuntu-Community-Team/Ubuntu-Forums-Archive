---
title: "regular usb keys can be mounted automatically, but external hardrive on 22.04"
date: 2023-09-27
forum: General Help
---

### Post by newcfd on 2023-09-27
On Lubuntu 22.04, regular usb keys can be mounted automatically, but an external hardrive can not be mounted. On two other different computers with Lubuntu 22.04, no issues.
journalctl -xe | grep -i usb does not show any errors. The drive is detected correctly when it is un/plugged. What could be wrong?

---

### Post by TheFu on 2023-09-27
50 things could be wrong.  

Did you look at the system logs already?
Did you check that the label for the file system partition is unique or already in some other mounting tool, like the fstab or autofs or a systemd unit file?

BTW, in Linux we 99.999999% of the time don't mount "drives", we mount file systems. If that isn't working, check the file system for issues.

---

### Post by newcfd on 2023-09-27
Thank you for your reply.

Sep 27 18:47:18 CAL-JOE001 kernel: [549047.268353] usb 3-7: new high-speed USB device number 23 using xhci_hcd
Sep 27 18:47:18 CAL-JOE001 kernel: [549047.416855] usb 3-7: New USB device found, idVendor=17ef, idProduct=4531, bcdDevice= 1.00
Sep 27 18:47:18 CAL-JOE001 kernel: [549047.416860] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 27 18:47:18 CAL-JOE001 kernel: [549047.416863] usb 3-7: Product: WD Portable HDD
Sep 27 18:47:18 CAL-JOE001 kernel: [549047.416866] usb 3-7: Manufacturer: WD
Sep 27 18:47:18 CAL-JOE001 kernel: [549047.416869] usb 3-7: SerialNumber: 
Sep 27 18:47:18 CAL-JOE001 kernel: [549047.418041] usb-storage 3-7:1.0: USB Mass Storage device detected
Sep 27 18:47:18 CAL-JOE001 kernel: [549047.418464] scsi host6: usb-storage 3-7:1.0
Sep 27 18:47:18 CAL-JOE001 mtp-probe: checking bus 3, device 23: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7"
Sep 27 18:47:18 CAL-JOE001 mtp-probe: bus: 3, device: 23 was not an MTP device
=============================system log stops here in the computer(not working)===============================================================

=============================system log continues like the following in the computer(working)=====================================================
Sep 27 18:47:18 CAL-JOE001 upowerd[931]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0
Sep 27 18:47:18 CAL-JOE001 upowerd[931]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb3/3-7
Sep 27 18:47:20 CAL-JOE001 kernel: [549050.051219] scsi 6:0:0:0: Direct-Access     WD   USB Hard Drive   1A   PQ: 0 ANSI: 6
Sep 27 18:47:20 CAL-JOE001 kernel: [549050.051462] sd 6:0:0:0: Attached scsi generic sg1 type 0
Sep 27 18:47:20 CAL-JOE001 kernel: [549050.051664] sd 6:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
Sep 27 18:47:20 CAL-JOE001 kernel: [549050.051878] sd 6:0:0:0: [sdb] Write Protect is off
Sep 27 18:47:20 CAL-JOE001 kernel: [549050.051879] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
Sep 27 18:47:20 CAL-JOE001 kernel: [549050.052095] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 18:47:20 CAL-JOE001 kernel: [549050.082969]  sdb: sdb1
Sep 27 18:47:21 CAL-JOE001 kernel: [549050.123615] sd 6:0:0:0: [sdb] Attached SCSI disk
Sep 27 18:47:22 CAL-JOE001 ntfs-3g[8610]: Version 2017.3.23 integrated FUSE 28
Sep 27 18:47:22 CAL-JOE001 ntfs-3g[8610]: Mounted /dev/sdb1 (Read-Write, label "WD_USB_HDD", NTFS 3.1)
Sep 27 18:47:22 CAL-JOE001 ntfs-3g[8610]: Cmdline options: rw,nodev,nosuid,uid=1000,gid=1000,uhelper=udisks2
Sep 27 18:47:22 CAL-JOE001 ntfs-3g[8610]: Mount options: rw,nodev,nosuid,uhelper=udisks2,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdb1,blkdev,blksize=4096
Sep 27 18:47:22 CAL-JOE001 ntfs-3g[8610]: Global ownership and permissions enforced, configuration type 7
Sep 27 18:47:22 CAL-JOE001 systemd[1]: Started Clean the /media/joe/WD_USB_HDD mount point.
Sep 27 18:47:22 CAL-JOE001 udisksd[582]: Mounted /dev/sdb1 at /media/joe/WD_USB_HDD on behalf of uid 1000


ntfs-3g is available in both computers.

---

### Post by TheFu on 2023-09-27
What's different about the kernels and USB controllers used?  As you can see, on recognizes the device and loads the SCSI drivers for it.  The other thinks it is a smartphone.

Some WD USB disks have poor compatibility with Linux USB controllers+drivers.  Try a different USB plug on the opposite side of the motherboard. Perhaps it is just an issue with 1 USB controller, but not the others or the front-USB ports.

Also, try a "Try Ubuntu" boot from a flash drive using the Ubuntu install ISO.  If that works on both systems, then it is NOT a hardware issue and it is a configuration issue.
And there's always this: [https://askubuntu.com/questions/1467629/wd-elements-usb-drive-is-not-recognized](https://askubuntu.com/questions/1467629/wd-elements-usb-drive-is-not-recognized)

The **lsusb** command will show the USB perspective on what the system sees.

If it is a new drive, now would be a good time to reformat to a native Linux file system.  Only use NTFS if the device will hold only data AND be physically connected to MS-Windows computers.

---

### Post by oldfred on 2023-09-28
Did you use drive on Windows that has fast startup?
That sets hibernation flag, preventing full mount with Linux NTFS driver. Otherwise you lose data written when it restores from hibernation. You may be able to manually mount read/only.

---

### Post by newcfd on 2023-09-28
Thank you for your reply. I tried 4 different computers(3 with Ubuntu 22.04 + same installation and 1 with 18.04). Only one computer with 22.04 has this issue. It has a different Intel CPU.
I do use it in Windows as well and have not paid attention to fast start-up.

---

### Post by TheFu on 2023-09-28
> **newcfd said:**
> Thank you for your reply. I tried 4 different computers(3 with Ubuntu 22.04 + same installation and 1 with 18.04). Only one computer with 22.04 has this issue. It has a different Intel CPU.
I do use it in Windows as well and have not paid attention to fast start-up.

It is most likely that fast startup didn't correctly close the file system, so it won't open.  NTFS is a foreign file system and there are lots of bugs in the NTFS driver software on Linux.

Did you try the "Try Ubuntu" flash drive boot yet?
Or using different USB ports?

---

### Post by newcfd on 2023-09-28
Just tried 3 more different computers with the very similar hardware. Two do not show the drive, but one does mount it.
How can I compare the differences? All have the same Ubuntu 22.04 installation.

---

### Post by newcfd on 2023-09-28
The customized computer has only two ports and I tried both of them. No help.
but it could be a port issue. The computer which mounts the drive has an external UBS hub.

---

### Post by newcfd on 2023-09-28
If the USB port causes the mount issue, any fix? Is it USB power issue?

---

### Post by sudodus on 2023-09-28
0. Please check carefully along all the paths suggested in the previous replies.

1. You can try with the external USB hub on the other computers. I remember cases, when things worked via the USB hub but not when connected directly to the USB port in the computer.

2. It might also be a power issue: that there is not enough power for the hard disk drive via the USB port, but the USB hub can have a separate power supply and therefore enough power to feed the hard disk drive.

---

### Post by TheFu on 2023-09-28
Not all USB ports supply lots of power. Some provide next to zero.

I've never personally seen a USB hub make anything "better" than directly connecting, but it couldn't hurt to try.
Not all USB ports/controllers (device AND computer) are compatible.
I have a powered USB3 hub from a reputable vendor that arrived when USB3 was just a few yrs old. Linux drivers for the specific chip used inside that hub weren't very good. Fortunately, the vendor was also having issues with MS-Windows and that caused them to release firmware updates for the hub.  Alas, to install that new firmware required MS-Windows with USB3, which I didn't and still do not have.  They offered to send me an upgraded hub with the new firmware, but they wouldn't guarantee that replacement would be nearly-new hub, like the one I owned.  Eventually, while visiting some relatives, I got the firmware upgraded and that hum has been fantastic for over 10 yrs now.

Is this external drive powered by only USB?  I always avoid those, unless it is an SSD. For spinning rust, I always buy enclosures with external power.

To figure out what the internal differences are, there are a number of different tools that will list all the different devices connected.  inxi is one. lsusb, lspci, lshw are others, but each doesn't provide the same level of information.  For "identical" systems, there are usually differences found by these tools.  Computer makers often change out the internal chips or cards and claim they are "identical".  Sometimes the diffs are subtle, like the same card, but a different revision (which has different chips).  Realtek commonly does this.

Also, be careful to note the specific drivers and driver versions the tools output.  Those differences can be completely unimportant or they can be the entire problem. Until you look, you can't tell.  

We've been doing the easy things. Checking all the drivers and chips for the MB, add-on cards, audio, video, storage, networking, and other things can be a chore.

Lastly, sometimes custom hardware does things that nobody expects and goes off-spec for some reason.  Nearly no USB devices actually follow the formal specification, completely. The reference designs don't either, which doesn't help vendors or us.

The WD troubleshooter [https://support-en.wd.com/app/answers/detailweb/a_id/18918/~/external-usb-drive-will-not-mount%2C-not-seen-or-detected-by-a-my-cloud](https://support-en.wd.com/app/answers/detailweb/a_id/18918/~/external-usb-drive-will-not-mount%2C-not-seen-or-detected-by-a-my-cloud) might be helpful. They have lots of idea, sadly, those seem to be MS-Windows, but translation isn't usually that hard.

---

### Post by sudodus on 2023-09-29
@sumodont,

Are you the same user as **newcfd** or another one? If you are another user, please create an own thread, where we can focus on your particular case.

---

