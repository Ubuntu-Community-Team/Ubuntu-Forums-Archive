---
title: "Faxing in Unbuntu 7.04"
date: 2007-08-10
forum: General Help
---

### Post by malel on 2007-08-10
Hi folks,
I am using Ubuntu 7.04 and want some help to enable me to do some faxing. It appears that not very many people using Ubuntu do any faxing but if someone has some compreshensive knowledge on how to set it up I would greatly appreciate it.
Many thanks

---

### Post by Scunizi on 2007-08-11
First you'll have to check to see if your modem is hardware or software driven.  If it's software there are referances to a program in the forums to check it's compatibility.  I bought an older US Robotics usr5686e external and hooked it to the serial port.  It works great for outbound faxes.  I never tried inbound faxes since I use j2.com.  To set up a fax "print" driver I followed the directions below.  Keep in mind it should be the same on Feisty but I'm using Dapper.

First, install efax gtk from the Synaptic Paxkage manager if you haven't already.
Next go to Administration printing
Double click on new printer
Select Network Printer HP JetDirect
Host is localhost
Port is 9900
Hit Forward
Printer manufacter should be raw
click on queue and click forward
Replace the name queue with something like fax then click on apply.
Now start Efax-gtk under Appications/Office make sure the fax entry method is socket
Now if you print a document in openoffice using the fax driver a dialog box from efax should open and just enter the telephone number
Hope this helps

---

### Post by malel on 2007-08-11
Thankyou Scunzi . I forgot to add that I am using an  ADSL modem on broadband. Will that handle faxing or do you have to have a separate modem

Regards

---

### Post by Scunizi on 2007-08-12
An ADSL modem is not really a modem in the classic sense.. It's really more of a Gateway.  If it has multiple ethernet ports on the back then it also has a router built in for multiple computer hookups.  Even though it plugs into the phone jack,  it really only connects you to the internet and not to the actual phone system (POTS).  You will need a seperate modem to be able to fax.  Here's a link to explore which modems would be compatible... [http://tldp.org/HOWTO/Hardware-HOWTO/modems.html](http://tldp.org/HOWTO/Hardware-HOWTO/modems.html).  I got mine at Staples on the clearance table for about $29 us.

---

### Post by MotHaiBa on 2007-08-13
Hi Scuniza,

Thanks for the instructions.

I also have problems sending faxes in Ubuntu 7.04. My fax modem works fine under Win XP.

I managed to get to the eFax screen with your instructions and received the following error message.

Have I missed something in the setup.

Regards

Socket running on port 9900
Print job received on socket
efax-0.9a: 16:29:02 opened /dev/ttyS0
efax-0.9a: 16:29:08 sync: dropping DTR
efax-0.9a: 16:29:12 sync: sending escapes
efax-0.9a: 16:29:18 Error: sync: modem not responding
efax-0.9a: 16:29:18 failed page /home/chau/efax-gtk-server/efax-gtk-server-3Nd1BH.001
efax-0.9a: 16:29:18 finished - no response from modem

---

### Post by Scunizi on 2007-08-13
You may not have a compatable modem.  Here is a link that pretty much covers how to identify your modem and its compatability as well as how to set it up.  [http://linmodems.technion.ac.il/#scanmodem](http://linmodems.technion.ac.il/#scanmodem)

I hope it helps!

---

### Post by Chilongola on 2007-08-15
If I may jump in here also...  I have a Pctel 789 internal modem.  It appeared on my device listing after installing ubuntu.  So i loaded drivers.  I got the modem to where it said it was activated.  When I try to send a fax this is what I get:

First Try:
Socket running on port 9900
Print job received on socket
efax-0.9a: 20:34:55 Error: can't open serial port /dev//dev/ttyS_PCTEL0: No such file or directory
efax-0.9a: 20:34:55 failed page /home/xxxxxx/efax-gtk-server/efax-gtk-server-lvxWdt.001
efax-0.9a: 20:34:55 finished - unrecoverable error

Second Try fixed the /dev//dev error in settings
efax-0.9a: 20:35:41 opened /dev/ttyS_PCTEL0
efax-0.9a: 20:35:44 using PCtel HSP56 MicroModem Linux Driver K2.4.7.V92.001 (03/26/2003) in class 1
efax-0.9a: 20:35:44 dialing T2230576
efax-0.9a: 20:37:44 Error: dial command failed
efax-0.9a: 20:37:44 failed page /home/xxxxxx/efax-gtk-server/efax-gtk-server-lvxWdt.001
efax-0.9a: 20:37:44 finished - unrecoverable error

Third Try
efax-0.9a: 20:38:15 opened /dev/ttyS_PCTEL0
efax-0.9a: 20:38:18 using PCtel HSP56 MicroModem Linux Driver K2.4.7.V92.001 (03/26/2003) in class 1
efax-0.9a: 20:38:18 dialing T2230576
efax-0.9a: 20:40:18 Error: dial command failed
efax-0.9a: 20:40:18 failed page /home/xxxxxx/efax-gtk-server/efax-gtk-server-lvxWdt.001
efax-0.9a: 20:40:18 finished - unrecoverable error

---

### Post by niceguy123 on 2007-09-06
> **Scunizi said:**
> You may not have a compatable modem.  Here is a link that pretty much covers how to identify your modem and its compatability as well as how to set it up.  [http://linmodems.technion.ac.il/#scanmodem](http://linmodems.technion.ac.il/#scanmodem)

I hope it helps!

I don't know where I'm going wrong here. I followed the trail here and on another post. I've got efax-gtk showing up on the menu under Applications>Office and under System>administration>printer> efax ready

but in openoffice under edit>print it doesn't show and if I try to drag into the efax window nothing happens...


Aside for that when I've tried the above to check the modem I get these notices in terminal:

```

~$ gunzip scanModem.gz
gunzip: scanModem.gz: No such file or directory
~$ chmod +x scanModem
chmod: cannot access `scanModem': No such file or directory
~$ ./scanModem   gunzip scanModem.gz
bash: ./scanModem: No such file or directory
~$ chmod +x scanModem
chmod: cannot access `scanModem': No such file or directory
~$ sudo ./scanModem
sudo: ./scanModem: command not found

```

---

### Post by Chilongola on 2007-09-06
[http://ubuntuforums.org/showthread.php?p=3321751](http://ubuntuforums.org/showthread.php?p=3321751)

have a look at post #2

---

### Post by niceguy123 on 2007-09-07
> **Scunizi said:**
> First you'll have to check to see if your modem is hardware or software driven. 

Sorry, How do I figure that out?

---

### Post by paul.drover on 2007-09-07
> **niceguy123 said:**
> I don't know where I'm going wrong here. I followed the trail here and on another post. I've got efax-gtk showing up on the menu under Applications>Office and under System>administration>printer> efax ready

but in openoffice under edit>print it doesn't show and if I try to drag into the efax window nothing happens...


Aside for that when I've tried the above to check the modem I get these notices in terminal:

```

~$ gunzip scanModem.gz
gunzip: scanModem.gz: No such file or directory
~$ chmod +x scanModem
chmod: cannot access `scanModem': No such file or directory
~$ ./scanModem   gunzip scanModem.gz
bash: ./scanModem: No such file or directory
~$ chmod +x scanModem
chmod: cannot access `scanModem': No such file or directory
~$ sudo ./scanModem
sudo: ./scanModem: command not found

```

Looks like you may have a path problem, try 
```

~$ gunzip ./scanModem.gz

```

---

