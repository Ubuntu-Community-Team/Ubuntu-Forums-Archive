---
title: "Can't find USB DVD writer"
date: 2006-11-02
forum: General Help
---

### Post by Odyssey1942 on 2006-11-02
Complete Newbie using 6.06 here.

I have plugged in and am trying to use a Sony i.link/USB DVD+/-RW ,+/-r portable drive, but cannot locate it. I have run the following commands:

sudo cat /etc/fstab, which yields the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda3 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

There is an internal CD in the computer which appears to me to be hdc and there are 2 hdd's which I take to be hda2 and hda3. Do I have this right?

lsusb yields:

Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Device manager identifies 3 USB UHCI controllers and one USB2 controller, but none identify the writer or give any helpful clues. 

The thing is that I only have one USB device plugged in and that is the DVD writer. How can I locate it?

(BTW, I have read every tutorial and resource that I can google up, but can find nothing directly in point.) TIA

---

### Post by Odyssey1942 on 2006-11-02
Bump to top

---

### Post by Odyssey1942 on 2006-11-03
I would welcome any opinion regarding the lack of response. If it is simply a matter of no one being able to assist, perhaps someone could suggest a forum better suited?

Alternatively, have I posted badly or otherwise posted in such a fashion as to discourage responses? If this is the case, I certainly would like to better understand how to do this in a way that is more productive and would welcome any suggestions.

Thanks.

---

### Post by Zimmer on 2006-11-03
fstab is the file that can be tweaked to mount specific devices at boot time. It will not automatically change to reflect the presence of a USB drive, but you can write to the file to give it a mount command for a device, if you can first find the device. The only experienxce I have with external USB drives is with a HDD enclosure and a USB mp3 player, both hot plug  and mount automatically.
The lack of response is probable through other's lack of experience with an external CD. Hang in there
, and I will look for the methods of searching for the hardware and try and get back to you, unless of course someone beats me to it :)

---

### Post by Odyssey1942 on 2006-11-03
Zimmer, I trust that you are absolutely correct about the lack of experience as I have tried several forums without much luck.

I have learned a little about the command:

tail -f /var/log/messages

shows a listing of what is happening and should reflect the presence of a USB device when it is plugged in, but my computer doesn't seem to give a notice and does not change it's line by line output, one line every few seconds, when I plug in my USB DVD writer, but neither does it seem to notice when I plug in a known good USB flash drive.

Thank you most heartily for your post and anything additional you might find. I have read extensively but just don't seem to find anything that helps me understand what I need to do.

---

### Post by Zimmer on 2006-11-03
post result of dmesg command after you plug the device in.... it may be you have a dodgy usb plug/controller...

---

### Post by Odyssey1942 on 2006-11-03
Nov  3 13:55:21 Ubuntu606 kernel: [17347767.420000] printk: 4 messages suppressed.
Nov  3 13:55:31 Ubuntu606 kernel: [17347777.180000] printk: 11 messages suppressed.
Nov  3 13:55:37 Ubuntu606 kernel: [17347782.724000] printk: 22 messages suppressed.
Nov  3 13:55:42 Ubuntu606 kernel: [17347788.232000] printk: 15 messages suppressed.
Nov  3 13:55:46 Ubuntu606 kernel: [17347792.368000] printk: 7 messages suppressed.
Nov  3 13:55:52 Ubuntu606 kernel: [17347797.556000] printk: 13 messages suppressed.
Nov  3 13:55:56 Ubuntu606 kernel: [17347802.448000] printk: 16 messages suppressed.
Nov  3 13:56:02 Ubuntu606 kernel: [17347807.888000] printk: 10 messages suppressed.
Nov  3 13:56:06 Ubuntu606 kernel: [17347812.424000] printk: 4 messages suppressed.
Nov  3 13:56:20 Ubuntu606 kernel: [17347826.320000] printk: 11 messages suppressed.
Nov  3 13:56:50 Ubuntu606 kernel: [17347856.020000] printk: 1 messages suppressed.
Nov  3 13:56:52 Ubuntu606 kernel: [17347857.532000] printk: 1 messages suppressed.
Nov  3 13:56:58 Ubuntu606 kernel: [17347863.580000] printk: 5 messages suppressed.
Nov  3 13:57:08 Ubuntu606 kernel: [17347874.416000] printk: 1 messages suppressed.
Nov  3 13:57:11 Ubuntu606 kernel: [17347877.440000] printk: 5 messages suppressed.

BTW, is there a way to "un-suppress" messages so that I can see what they are?

---

### Post by Zimmer on 2006-11-03
> **Odyssey1942 said:**
> Nov  3 13:55:21 Ubuntu606 kernel: [17347767.420000] printk: 4 messages suppressed.

Nov  3 13:57:11 Ubuntu606 kernel: [17347877.440000] printk: 5 messages suppressed.

BTW, is there a way to "un-suppress" messages so that I can see what they are?

That is not the output I was expecting from  dmesg 
 :(

Despite reading the MAN page for dmesg I am no wiser as to how to un suppress the messages.
Have you tried looking at the system log System>Administration>System log   ?

---

### Post by Odyssey1942 on 2006-11-03
That approach using the GUI yields the same result, 

Somehow I opened a GUI window that has two tabs, one labeled "messages" which is the same list as above, but the other tab is labeled "udev" which lists the sort of info that I suspect is what you were expecting. But it is extremely long (lots and lots of device descriptions.)

If you can tell me what to look for, I will copy and post what I find. Thanks.

---

### Post by Zimmer on 2006-11-06
Ok, sorry for the late response ..
Boot the computer, log in, then plug in the USB drive. 
 Browse the file system with nautilus for var/log  and open the text file there called   syslog.
If the device has been recognised the last 20 lines or so of the log will look something like this
>   6 10:43:05 ubuntusmall kernel: [17181187.320000] usb-storage: device found at 3
Nov  6 10:43:05 ubuntusmall kernel: [17181187.320000] usb-storage: waiting for device to settle before scanning
Nov  6 10:43:05 ubuntusmall kernel: [17181187.320000] usbcore: registered new driver usb-storage
Nov  6 10:43:05 ubuntusmall kernel: [17181187.320000] USB Mass Storage support registered.
Nov  6 10:43:10 ubuntusmall kernel: [17181192.324000]   Vendor: ST340014  Model: A                 Rev: 0811
Nov  6 10:43:10 ubuntusmall kernel: [17181192.324000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Nov  6 10:43:10 ubuntusmall kernel: [17181192.336000] usb-storage: device scan complete
...
Nov  6 10:43:10 ubuntusmall kernel: [17181192.368000] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Nov  6 10:43:10 ubuntusmall kernel: [17181192.368000] sda: assuming drive cache: write through
Nov  6 10:43:10 ubuntusmall kernel: [17181192.372000] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Nov  6 10:43:10 ubuntusmall kernel: [17181192.372000] sda: assuming drive cache: write through
Nov  6 10:43:10 ubuntusmall kernel: [17181192.372000]  sda: sda1 sda2
Nov  6 10:43:10 ubuntusmall kernel: [17181192.396000] sd 0:0:0:0: Attached scsi disk sda

Nov  6 10:43:10 ubuntusmall kernel: [17181192.372000]  sda: sda1 sda2 
shows me the device names sda1 and sda2 which the system is now using for the two partitions on my external drive.
Have a look at your log and see what messages(if any) you get when you plug the drive , or any other usb device you may have...

---

