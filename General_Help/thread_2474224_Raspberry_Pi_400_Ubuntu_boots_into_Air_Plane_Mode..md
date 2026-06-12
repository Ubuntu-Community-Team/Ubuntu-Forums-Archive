---
title: "Raspberry Pi 400 Ubuntu boots into Air Plane Mode."
date: 2022-04-24
forum: General Help
---

### Post by WacoJohn on 2022-04-24
Ubuntu 21.10 Impish.  Have to turn off the mode on every boot.  Help appreciated in advance.

---

### Post by WacoJohn on 2022-04-29
Now upgraded to:

PRETTY_NAME="Ubuntu 22.04 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy

and still starting up with Airplane Mode turned on.  Any help, please?

---

### Post by WacoJohn on 2022-05-01
Am I in the wrong Topic??  never have been ignored this long.

---

### Post by him610 on 2022-05-01
I have a couple of Rpi devices, but I do not use Ubuntu 20.?? on either one of them. So, I probably can not give you any advice.
> still starting up with Airplane Mode turned on
How do you manage to do that? Just curious.

If it is enabled, there should be a way to disable it. Does this device have a Sim card in it?

---

### Post by WacoJohn on 2022-05-01
> **him610 said:**
> I have a couple of Rpi devices, but I do not use Ubuntu 20.?? on either one of them. So, I probably can not give you any advice.

How do you manage to do that? Just curious.

If it is enabled, there should be a way to disable it. Does this device have a Sim card in it?

First, thank you for the reply.  No Sir, ... no Sim card.  Raspberry Pi 400 is a desktop computer.  It runs a slew of OS's.  Ubuntu is one of them.  I will be glad to answer any questions I can.  

I don't believe just any Pi will run Ubuntu but the 400 is one of them.  It's a 64-bit CPU.  Grab yourself a mini SD card ... 32MB or larger. Download IMAGER from [https://www.raspberrypi.com/]("https://forums.raspberrypi.com/") (click SOFTWARE on their home page). to a windows machine.  Mount SD card on Windows machine and run Imager.  

The UBUNTU image is a few selections down on the menu, .. I believe the menu title is OTHER.  Under OTHER should be Ubuntu 64 and another 32 as I recall.  I'm running 64.  Proceed and Imager will do the rest.  Easiest thing I have done on any computer.  There are other OS's to choose from.  Linux Debian and Raspberry's OS's.  Pop the SD card in your Rasp. device and turn her on.  BAM!!  

The Pi 400 is only 4GB of memory and I have problems with browser briefly failing to respond.  That and the Air Plane Mode ... only problems I have.  You might get around those problems with a 32-bit image.  Need further help, msg me.

---

### Post by QIII on 2022-05-01
No PMs for support, please.  That selfishly deprives the community of a solution that might help another.  

All support should take place in public.

---

### Post by WacoJohn on 2022-05-02
Sorry.  I unselfishly figured we were going off topic and best to go private on his question.  Now I know.  Thanks.

---

### Post by him610 on 2022-05-03
@Moderator - This post is for public consumption
WacoJohn,
I believe I was unclear in my initial response. I was not asking for advice as I have RaspberryPi OS (Bullseye) installed on both of my RPi devices (RpiBr2 & RPi3B). 
I was curious as to how you got Airplane Mode on installed on a RPi 400. I have only seen Airplane Mode on cell phones that use a Sim card.
How did you solve it?

---

### Post by WacoJohn on 2022-05-03
> **him610 said:**
> @Moderator - This post is for public consumption
WacoJohn,
I believe I was unclear in my initial response. I was not asking for advice as I have RaspberryPi OS (Bullseye) installed on both of my RPi devices (RpiBr2 & RPi3B). 
I was curious as to how you got Airplane Mode on installed on a RPi 400. I have only seen Airplane Mode on cell phones that use a Sim card.
How did you solve it?

AHHH.  Thought you were asking how I got Ubuntu onto my Pi 400.  In any case, seemed to install with Airplane Mode on (default) and I could find nowhere to change that.  Finally, found it under Network Settings.

Cheers to you too.

---

