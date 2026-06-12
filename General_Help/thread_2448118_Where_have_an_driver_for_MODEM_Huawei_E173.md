---
title: "Where have an driver for MODEM Huawei E173 ?"
date: 2020-08-02
forum: General Help
---

### Post by aug7744 on 2020-08-02
Lubuntu 20.04 not have drivers for MODEM Huawei E173 ?
I need to download an driver using windows and after install in Lubuntu because I not use wifi or LAN internet access.
Have any site repository for drivers in Ubuntu ?

---

### Post by CelticWarrior on 2020-08-02
Huawei E173 is supported and has been since before 2012!!! No additional drivers required.
All you need to do is to setup the connection using the network menu. 

In Ubuntu 20.04 (Gnome) is certainly different from the old Unity shown in this question: [https://askubuntu.com/questions/179324/huawei-e173-on-ubuntu-12-04](https://askubuntu.com/questions/179324/huawei-e173-on-ubuntu-12-04) . That said, the wizard is probably similar.

Alternatively, if you have any current Android or iPhone, you can use the SIM card in the phone and then activate USB tethering. It automatically establishes a "Ethernet-over-USB" for which NO drivers are required, in Ubuntu or Windows.

---

### Post by aug7744 on 2020-08-02
Hmmm I had done an device internal command to not mount the "disk partition with windows driver" in windows.
Perhaps is the because not is working ? Well I will disable that command.

---

### Post by grahammechanical on 2020-08-02
It is possible to turn off WiFi and ethernet in Windows. If we do that then when we load Linux those hardware devices will not be switched on. The same thing will happen if we disable WiFi and ethernet in the UEFI/BIOS

When you installed Lubuntu did you do it from a live session running from a USB stick or a DVD? Was it connected to the internet? If this is true then there are hardware drivers installed and you must look elsewhere for the problem.

Regards.

---

### Post by aug7744 on 2020-08-03
MODEM is working now.
Thanks for reply.

---

