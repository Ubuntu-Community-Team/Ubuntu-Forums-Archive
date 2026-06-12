---
title: "Turning of UEFI boot"
date: 2016-07-19
forum: General Help
---

### Post by dagring on 2016-07-19
I was asked during an kernel upgrade (4.2.0-42 generic) this morning if I wanted to turn of UEFI boot, because it would not be compatible with properitary drivers. I plotted in a password, and I was told I should insert this special password again when the machine rebooted. I got a system screen after I rebooted and confirmed I wanted to boot. I must have made the wrong choice here, because it seems the system has not loaded then wlan driver. No password before the ordinary user login. 

Is it a way to redo this, and what is the right choice when I come to the system screen?

Dag R

---

### Post by oldfred on 2016-07-19
I have not seen system ask to turn off UEFI. 
I have never seen it say to give a new password.

It does ask for your normal password, if installing something new like a new kernel.

What brand, model system?
 Did you have to install any proprietary drivers to make it work?

From live installer:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2016-07-19
This is the second or third post I have seen where the user was asked to create a password. I do not have a UEFI system so I have no idea where this is coming from.

Here is one

[https://ubuntuforums.org/showthread.php?t=2330873](https://ubuntuforums.org/showthread.php?t=2330873)

and others

[https://ubuntuforums.org/showthread.php?t=2330930](https://ubuntuforums.org/showthread.php?t=2330930)

[https://ubuntuforums.org/showthread.php?t=2331009](https://ubuntuforums.org/showthread.php?t=2331009)

Possibly related? A change in how things are done?  Or, pilot error?   Turning on secure boot after installation?

Regards.

---

### Post by dagring on 2016-07-19
My system is a netbook Asus One five years old. The installed system is ubuntu 15.10 64 bit. This is a crappy old machine, but I use it for writing, så it works fine in this instance. When it comes to what grahammechanical talks about, the posts refer to some of my problems. What is is alike is that the message says you have to turn off UEFI boot, because properitary drivers will not work after the upgrade. When it asked for a password, this would be a precaution for security in this change. It was a password only for  this operation, and not the user password. 

I have tried a lot of things after I wrote my post. What I did was to opt out af the properitary driver for my Broadcom wlan card (under system settings -->software & updates -->addiional drivers). It was not any alternative driver mentioned. The only choice I had beside still using the broaddcom driver was: Not use this device. I thought I should try to turn it of, and the system find an open driver for the card. It worked! When I go to the additional drivers now, it says the broadcom card does not work. That does not make any sense for me, because it's the same card that worked under the former kernel with the broadcom-sta driver.

When I do a lspci -vvnn | grep -A 9 Network, it prints kernel driver in use: bcma-pci-bridge

The problem for me is solved, but shouldn't there be a explanation. Is this a virus or is it a way of dealing with properitary drivers?

Dag R

---

### Post by grahammechanical on 2016-07-25
Is this what you saw?

[https://fourdollars.blogspot.co.uk/2016/07/disable-secure-boot-in-shim-signed.html](https://fourdollars.blogspot.co.uk/2016/07/disable-secure-boot-in-shim-signed.html)

Regards.

---

### Post by dagring on 2016-07-25
Yepp this was the screen I experienced! I made this password but the did not see any MOK management screen. That is what made me frustrated. I missed the control of the process, and the wlan card driver got messed up. Thanx for looking into this. 

Dag R

---

