---
title: "Can't get external USB harddisk working in VMware player"
date: 2007-08-06
forum: General Help
---

### Post by Snam on 2007-08-06
Hello,

I've got an External USB Elements 500 GB harddisk WDE1U5000E by Western Digital.
I use: VMware Player 1.0.1 build-19317
My guest OS is: Ubuntu 6.06 LTS Dapper Drake (Linux) - kernel 2.6.15-28-686
My VM OS is: Windows XP Service Pack 2


When I plug in my external USB harddisk the following button in VMware player appears: "Western Digital External HDD". It also shows up in Ubuntu.

If I connect the "Western Digital External HDD" in VMware player the following happens: The external USB disk disappears from the Ubuntu Nautilus file explorer. I get the following message in Windows "This device can perform faster - This USB device can perform faster if you connect it to a Hi-Speed USB 2.0 port. For a list of available ports, click here." And the "Safely remove USB hardware icon" appears in the Windows taskbar. 
But when I open explored in Windows, I can't see my external usb harddisk. In the "Safely Remove Hardware window" no hardware devices are shown (the list is empty).

Therefor I cannot use my external usb harddisk in my Windows Virtual Machine.

How can I fix this problem?

---

### Post by SeanHodges on 2007-08-06
Did you format your external disk with a filesystem other than NTFS or FAT?

How experienced are you with filesystems?

---

### Post by Snam on 2007-08-07
> **SeanHodges said:**
> Did you format your external disk with a filesystem other than NTFS or FAT?
The External USB Elements harddisk WDE1U5000E by Western Digital is formatted FAT32 out of the box.  (**I** haven't  (re)formated the disk.)

> **SeanHodges said:**
> How experienced are you with filesystems?
I'm not a real expert, but I know something... amongst others the difference between FAT32 and NTFS. What should I know?

---

### Post by komalhahi on 2007-12-25
dear sir

i have one 80GB external HDD and i configured one machine having 2003 OS.in that machine i configured VMWare software and load another OS of XP Pro.Now whenever i connect External HDD,it support only in main OS(i.e 2003 server ),it doesnot detect in VMWare machiine having XP.

    now tell me how to enable my external HDD in VMWare machine,s XP os???

thanks
kuldeep

---

