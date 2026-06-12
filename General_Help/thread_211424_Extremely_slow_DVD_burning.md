---
title: "Extremely slow DVD burning"
date: 2006-07-08
forum: General Help
---

### Post by vijirajan on 2006-07-08
I am experiencing extremely slow DVD burning with Dapper 6.06 LTS (dist-ugraded from Breezy). I have a Plextor PX-750UF USB/IEEE 1394 drive and I tried to burn a RITEK P16 (Sold by OfficeDepot) 16x DVD+R and it took close to 45 minutes to burn a DVD. I tried both GnomeBaker and nautilus-cd-burner to write DVDs and they both exhibit the same issue.

I tried to burn a 4G vmware image with the same drive and a RITEK P16 on a Windows XP machine with nero 6, believe it or not, it burned under 6 minutes.   

Can somebody point me in the right direction to fix this issue? Any help on this is greatly appreciated.

---

### Post by Athropos on 2006-07-08
Try to run this command:

> 
sudo hdparm /dev/hdc


and see if DMA is on.

(if /dev/hdc is not your DVD device, correct it to your needs).

---

### Post by vijirajan on 2006-07-08
Thanks for the reply. Does hdparm work for external drives (USB/IEEE 1394)?

---

### Post by Athropos on 2006-07-08
> **vijirajan said:**
> Thanks for the reply. Does hdparm work for external drives (USB/IEEE 1394)?

I believe it should...

---

### Post by vijirajan on 2006-07-08
This is the output of hdparm:

```
rajan:~$ sudo hdparm /dev/scd1

/dev/scd1:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
```

Looks like DMA is not supported on this drive.

---

### Post by vijirajan on 2006-07-11
Can anybody help me please??? I am still having problem burning DVDs. :(

---

### Post by GuiGuy on 2006-09-23
> **vijirajan said:**
> Can anybody help me please??? I am still having problem burning DVDs. :(

I'd like to be more positive, but am convinced that Linux is not able to burn at speed. I've been trying to resolve poor burning speeds on DVDs for over a year now (Mandrake, Suse, Ubuntu). I have tweaked hdparm.conf until my finger tips bled. I have changed hardware, I rebooted, I have followed every bit of advice that I have been able to find. I have tried Lite-On, Samsung, LG, Sony and Pioneer burners. I have tried K3B, Gnomebaker, Nero Linux etc etc.

Current SAMSUNG 8X Burner

/dev/hdc:
 IO_support   =  1 (32-bit)
 using_dma    =  1 (on)
 keepsettings =  1 (on)

 Current Pioneer DVD Burner 16X
/dev/hdd:
 IO_support   =  1 (32-bit)
 using_dma    =  1 (on)
 keepsettings =  1 (on)

K3B identifies the media (Verbatim 16X DVD+R) correctly but burns at 1.68x :confused: 

I can do no more and suggest that this is a general issue.

I'm burning under Windows. No problems there, same machine, same hardware.

regards

---

