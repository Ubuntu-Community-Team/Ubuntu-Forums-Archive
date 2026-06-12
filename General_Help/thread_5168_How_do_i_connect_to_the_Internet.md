---
title: "How do i connect to the Internet?"
date: 2004-11-16
forum: General Help
---

### Post by raso on 2004-11-16
Ok this must be a really stupid question.

First of all i m a total Linux Newbie. First time i ever installed Linux.

I cannot seem to find the way to connect online. Doing the 'windows' thing i went and checked the device manager and Ubundu finds and recognises my modem there.  However i cannot find the way to go online. I tried through some of the 'networking' options but nothing.


So am i missing something obvious? Or despite the modem appearing correctly there is a driver issue. 


Thanks in advance. I hope it is indeed something obvious. Feel free to laugh if it is indeed :)

---

### Post by p!=f on 2004-11-16
[QUOTE=raso]Ok this must be a really stupid question.
  
  First of all i m a total Linux Newbie. First time i ever installed Linux.
  
 I cannot seem to find the way to connect online. Doing the 'windows' thing i went and checked the device manager and Ubundu finds and recognises my modem there. However i cannot find the way to go online. I tried through some of the 'networking' options but nothing.
  
  
  So am i missing something obvious? Or despite the modem appearing correctly there is a driver issue. 
  
  
  Thanks in advance. I hope it is indeed something obvious. Feel free to laugh if it is indeed :)[/QUOTE]  What's your modem? Manufacturer + model. Use lcpci command to get your hw list.
  ```

   * 13:06:11 * pef @ agonicus *
  [~] > lspci
  0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
  0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
  0000:00:08.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
  0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
  0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
  0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
  0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
  0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
  0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
  0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
  
```

---

### Post by raso on 2004-11-16
Ita  sold as Tornado bulk 56k/v92

Ubuntu Device manager says: 

HSF 56K HSFi Modem 

The vedor is : Conexant

---

### Post by p!=f on 2004-11-16
This thread might be of help:
 [http://www.ubuntuforums.org/showthread.php?t=3155](http://www.ubuntuforums.org/showthread.php?t=3155)

---

### Post by foggy98 on 2004-11-17
[QUOTE=raso]Ok this must be a really stupid question.

First of all i m a total Linux Newbie. First time i ever installed Linux.

I cannot seem to find the way to connect online. Doing the 'windows' thing i went and checked the device manager and Ubundu finds and recognises my modem there.  However i cannot find the way to go online. I tried through some of the 'networking' options but nothing.


So am i missing something obvious? Or despite the modem appearing correctly there is a driver issue. 


Thanks in advance. I hope it is indeed something obvious. Feel free to laugh if it is indeed :)[/QUOTE]
-------------------

Try this:

From your desktop click on COMPUTER ----> System Config -------> Networking
-------> enter your password at the prompt ------>under Network Settings click  +Add
button ------> configure (modem is probably on ttys0) and accept -------> click on ACTIVATE from the Network Setings box ..... Your modem should start dialing. 
 I hope this helps.

---

