---
title: "How do i connect to the Internet?"
date: 2006-09-29
forum: General Help
---

### Post by samquest on 2006-09-29
Hi,

Can anyone tell me how can i connect to the internet using
a dial-up modem?

I've Breezy Badger 5.10.
My modem is Conexant HSF V.92 internal modem.

The device manager shows this device.

But i am not able to find any dialer or modem configuration link.
 i only know how to connect to the internet on a windows machine.

Can anyone help me?

---

### Post by macogw on 2006-09-29
Go to System > Administration > Networking and change the settings on the modem.

---

### Post by samquest on 2006-09-30
Hi,


      Thanks for your advice.

But the modem is not available in System > Administration > Networking.

Where is the dialer? So i can put the dialing no. , username & password.

Is there any OTHER WAY?

---

### Post by _duncan_ on 2006-10-01
Take a look at the following article:

[How To Conexant and Smartlink Modem]("http://www.ubuntuforums.org/showthread.php?t=190728")

---

### Post by samquest on 2006-10-03
Hello,

	Again , thanks your advice. The forum link given above is not helping to use the modem.

In the forum link, the driver given is suitable for soft modems.
I don't have a soft modem.

	I still tried to install the drivers, but there were too many errors. Gnome ppp does not detect the modem. Only the device manager shows the device. 

Can anybody help me?

---

### Post by _duncan_ on 2006-10-03
You mentioned in your first post that it's an internal modem. So presumably your modem is just a card that is connected to a PCI slot inside the computer. This is one of the surest sign that you have a software modem. These are sometimes called winmodems, since they work perfectly with windows but not with linux. Most people don't even know they have a software modem until they tried using it with linux.

In contrast, a hardware modem is usually plugged into the computer via a serial port although some are connected to USB ports. Note that not all modems connected via USB are hardware modems. This type of modem comes complete with a casing, various control buttons, and a set of indicator lights.

I'll leave you to decide which type of modem you have. Good luck.

---

### Post by samquest on 2006-10-04
Hi,

Again thanks for your advice.

                   I know about software and hardware modems.
I have a hardware modem connected through a serial port.
I have several times removed it from pc. 

                   It still works woth windows. 

Can anyone help me?

---

### Post by chuckman78 on 2006-10-04
Hi,samquest and welcome.

  The previous poster confusion (and mine too) arises because of your orignal post:

> **samquest said:**
> Hi,

Can anyone tell me how can i connect to the internet using
a dial-up modem?

I've Breezy Badger 5.10.
My modem is Conexant HSF V.92 **internal modem**.

The device manager shows this device.

But i am not able to find any dialer or modem configuration link.
 i only know how to connect to the internet on a windows machine.

Can anyone help me?

   We really need to stablish the nature of your modem so we can find the appropiate solution for your problem.

Regards,

Carlos.

---

### Post by samquest on 2006-10-05
Hello,


         If you want any information about the modem or anything,
JUST ASK.

---

