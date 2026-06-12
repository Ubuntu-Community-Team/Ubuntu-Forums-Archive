---
title: "Setting DMA, Inappropriate ioctl"
date: 2008-01-16
forum: General Help
---

### Post by dbarbour on 2008-01-16
After experiencing painfully slow files transfers on my new IDE drive (2+ minutes to transfer a 4MB mp3 across a wired network), I read that DMA is important and is off by default in Ubuntu. (WTF?) So using hdparm I tried to enable it...```
sudo hdparm -d1 /dev/sda
```and the response...```
/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```Any ideas what this might mean? Kinda at a loss.

---

### Post by ckoester on 2008-01-21
You said IDE drive, but IDE drives are named hd*.  SATA and SCSI drives are named sd*.  Are you sure you're working with an IDE drive?  Just want to verify this, because myself and others seem to be getting this same error with SATA drives.

Use the following to get a list of installed drives:

```
sudo lshw -C disk
```

Use the command below to get detailed drive information.

```
sudo hdparm -I /dev/sda
```

There should be an asterisk next to the DMA mode that is active.  Here is what mine looks like:

```
 DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
```

---

