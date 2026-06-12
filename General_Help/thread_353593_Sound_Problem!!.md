---
title: "Sound Problem!!"
date: 2007-02-04
forum: General Help
---

### Post by hgmgtak on 2007-02-04
I have already done it step by step according
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching)

 I have compiled ALSA driver, but there is no sound.
and I tried to type aplay -l and it displayed device_list:221: no soundcard found...

My sound card is onboard.....
My old laptop is Twinhead Slimonote VX.....
I am using Xubuntu 6.10.....
 
Why my old laptop cant play sound??

Please help me!!

Thanks a lot

---

### Post by amohanty on 2007-02-04
After a default install, what does lspci return?

AM

---

### Post by hgmgtak on 2007-02-04
> **amohanty said:**
> After a default install, what does lspci return?

AM

Thank you for anwsering..=]
 
It returns ..
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:02.0 VGA compatible controller: Trident Microsystems Cyber 9388 (rev d3)
00:03.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:03.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:03.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:03.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1221
00:0a.1 CardBus bridge: Texas Instruments PCI1221
01:00.0 Ethernet controller: Linksys 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)

---

### Post by amohanty on 2007-02-04
Post the output of:
lshw -C sound

also is it enabled in bios

AM

---

### Post by hgmgtak on 2007-02-04
> **amohanty said:**
> Post the output of:
lshw -C sound

also is it enabled in bios

AM

bash: lshw: command not found

I have enabled it in bios

---

### Post by hgmgtak on 2007-02-05
Please help me!!

---

### Post by amohanty on 2007-02-05
install lshw using:

> sudo apt-get install lshw

and then post the output of:

> lshw -C sound

and
 
> lsmod | grep snd

AM

---

### Post by hgmgtak on 2007-02-05
> **amohanty said:**
> install lshw using:



and then post the output of:



and
 


AM

There is nothing...

---

### Post by amohanty on 2007-02-06
I dont understand, there is no output from the commands??

Can you post the entire output of lsmod then??

AM

---

