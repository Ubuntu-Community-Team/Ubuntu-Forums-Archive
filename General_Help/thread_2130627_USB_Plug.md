---
title: "USB Plug"
date: 2013-03-30
forum: General Help
---

### Post by mld9373 on 2013-03-30
I need to charge my Iphone when my lid is down on my laptop.I am running  ubuntu 12.04 LTS .so my question is how do i keep my usb ports active  even when the lid is closed ?


                                                                                                                                                                                             thanks:p

---

### Post by CaptainMark on 2013-03-30
You can either stop the laptop from suspending by changing settings in the power section, if you want the laptop go into standby but keep the usb ports powered then its down to if your laptop will allow you to do this and option will usually be found in your bios menu usually under power again

---

### Post by tgalati4 on 2013-03-30
Install* acpitool*.  Open a terminal:

```
sudo apt-get install acpitool
acpitool -w
```

You will get a printout of your devices:

tgalati4@Mint14-Extensa ~ $ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID0	  S3	*enabled   
  2. SLPB	  S3	*enabled   
  3. HDEF	  S3	*disabled  pci:0000:00:1b.0
  4. PXSX	  S5	*enabled   pci:0000:02:00.0
  5. USB1	  S3	*enabled   pci:0000:00:1d.0
  6. USB2	  S3	*enabled   pci:0000:00:1d.1
  7. USB3	  S3	*enabled   pci:0000:00:1d.2
  8. EHC1	  S3	*enabled   pci:0000:00:1d.7

Pick the USB port you want to enable after putting to sleep.  Remember the number.

```
sudo acpitool -W 7
acpitool -w
``` to verify the change.

---

