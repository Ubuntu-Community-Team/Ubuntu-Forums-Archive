---
title: "Help- System Volume"
date: 2008-05-07
forum: General Help
---

### Post by jijo on 2008-05-07
Friends,
        The sound volume in my system drastically became very low one fine morning. I don't know the reason. I upgraded to hardy heron only two weeks back.  Even after the upgradation, everything was running smooth and fine.  What could be the problem? Is it with the O.S or any other reson?M  PLEASE HELP

---

### Post by TeoBigusGeekus on 2008-05-07
Type 
```
alsamixer
```
in terminal to adjust master volume.

---

### Post by jijo on 2008-05-08
dear friend, 
         I did as u said. The master volume level is maximum in alsa mixer. Then could it be the intel sound card?

---

### Post by jijo on 2008-05-08
dear friend, 
         I did as u said.But no change. The master volume level is maximum in alsa mixer. Then could it be a problem with the intel sound card?

---

### Post by TeoBigusGeekus on 2008-05-08
Type 
```
lspci
```
in terminal to see your sound card and post results.

---

### Post by jijo on 2008-05-08
jijo@jijo-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Modem: SILICON Laboratories Intel 537 [Winmodem] (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
jijo@jijo-desktop:~$

---

### Post by jijo on 2008-05-08
I'm really thankful to u for the continuing help and support. Hole we can sort out this problem.. Expecting more help from you. thanks

---

### Post by jijo on 2008-05-08
I'm really thankful to u for the continuing help and support. Hope we can sort out this problem.. Expecting more help from you. thanks

---

### Post by TeoBigusGeekus on 2008-05-08
Could you do the same for 
```
lspci -n | grep `lspci | grep -i audio | awk '{print $1}'
```
please?

---

### Post by jijo on 2008-05-08
nothing happened when i did like that

---

### Post by jocko on 2008-05-08
Let's see the output of these commands:
```
aplay -l
asoundconf list
```

---

### Post by jijo on 2008-05-10
I don't know what is happening with my system. Today the volume  automatically solved. Thanks to all who tried to help me. thanks a lot....

---

