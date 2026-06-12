---
title: "Need help with Verizon Express card"
date: 2008-05-21
forum: General Help
---

### Post by wesy2kn1 on 2008-05-21
the only thing that I have not managed to get working in Ubuntu yet is my Verizon EVDO Rev A express card. Its a Kyocera KPC680 Express card. It should also be noted that I am using wicd manager in replacement of the Ubuntus network manager just because it does much better with the wireless on my laptop.

Oh and computer is a Dell Inspiron E1705 Core Duo Solo if that helps as well.

Thanks in advance for the help.

---

### Post by popuptarget on 2008-05-21
Have you tried gnomeppp?  I use it for my verizon qualcom 3g CDMA card and it works like a champ.  

V/R Jason

---

### Post by wesy2kn1 on 2008-05-21
> **popuptarget said:**
> Have you tried gnomeppp?  I use it for my verizon qualcom 3g CDMA card and it works like a champ.  

V/R Jason

I haven't heard of this before as you can tell I'm a noob here will do some research on that. Thanks.

---

### Post by popuptarget on 2008-05-21
OK.   I am a noob here as well.  Select Applications,Add/remove, in the search type gnome ppp.  It should give you gnome ppp.  Or you can open a terminal session under applications,accessories,terminal.  then type > sudo apt-get install gnome ppp 
 You will be asked for your password.  Enter that then once it is done close your terminal session select Applications,internet, gnome ppp.  When you get that far drop me a line.  You will then need to set up how it dials up and user name/password.

V/R Jason

---

### Post by wesy2kn1 on 2008-05-21
Well this is what I get back. Broken Pakages. Must be the version of gnome I guess.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ppp is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome: Depends: gnome-desktop-environment (= 1:2.20.2.2) but it is not going to be installed
E: Broken packages

```

---

### Post by popuptarget on 2008-05-21
As my command line instructions are not the best by any stretch of the imagination, Have you tried using synaptic?  The Applications, Add/Remove way?  I know that is how I installed it.  just make sure you put a space between the word gnome and ppp.  


V/R Jason

---

### Post by wesy2kn1 on 2008-05-21
> **popuptarget said:**
> As my command line instructions are not the best by any stretch of the imagination, Have you tried using synaptic?  The Applications, Add/Remove way?  I know that is how I installed it.  just make sure you put a space between the word gnome and ppp.

yeah it wasn't available in Synaptic. I should have mentioned that I'm using ubuntu 8.04 as well.

---

### Post by niteshifter on 2008-05-22
Hi,

I believe it's **gnome-ppp**. With a dash betwixt gnome and ppp.

---

### Post by wesy2kn1 on 2008-05-22
> **niteshifter said:**
> Hi,

I believe it's **gnome-ppp**. With a dash betwixt gnome and ppp.

got it...thanks man you rock. wouldn't have caught that all night :)

---

### Post by popuptarget on 2008-05-22
Wes.

  Make sure under synaptic you change the Show option to "All Open Source documents"  as it is not listed under "supported applications".

Niteshifter,

  I am sure you are correct.  

If some other poor noob is reading this debacle no worries.  we will get wes up and running.  

V/R Jason

---

### Post by wesy2kn1 on 2008-05-22
Got Gnome-ppp up and running. Now the only problem I have is the modem not being recognized. In the words of Charlie Brown Argg.

---

### Post by popuptarget on 2008-05-22
Woohoo.  Now take a look at the attached screenshot and see if this gets your card detected.  Also have you figured out you username/password/phone number?

V/R Jason

---

### Post by wesy2kn1 on 2008-05-22
> **popuptarget said:**
> Woohoo.  Now take a look at the attached screenshot and see if this gets your card detected.  Also have you figured out you username/password/phone number?

I remember all the setup information from when I was running it on windows. I ran it from the windows dial up manager instead of verizon's dialer. But no its not being detected. Again its not usb, but an express card.

The Kyocera KPC680 to be exact and its not being detected.

---

### Post by popuptarget on 2008-05-22
Ok.  In a terminal session type > lsusb.  I know it is not a usb but as mine is also a express card it still is recognized as a usb.  see attached.  Mine is the Sierra wireless.

---

### Post by wesy2kn1 on 2008-05-22
k well when i type lsusb in terminal this is what i get...

i'm going to play around here with it a bit

---

### Post by popuptarget on 2008-05-22
Wes,

   type dmesg in terminal and see where your Kyocera is listed.  Then try one of the listed ports.  Mine shows ttyUSB0,ttyUSB1,ttyUSB2.  Normally it is active on USB0 but I have found as I am plaing with other USB devices it changes if I am not using the modem.  Oh and remember I am also very new to this as well.  I just happen to have a verizon card as well and stumbled through this.  I know the pain.  

V/R Jason

---

### Post by wesy2kn1 on 2008-05-22
> **popuptarget said:**
> Wes,

   type dmesg in terminal and see where your Kyocera is listed.  Then try one of the listed ports.  Mine shows ttyUSB0,ttyUSB1,ttyUSB2.  Normally it is active on USB0 but I have found as I am plaing with other USB devices it changes if I am not using the modem.  Oh and remember I am also very new to this as well.  I just happen to have a verizon card as well and stumbled through this.  I know the pain.

when i type dmesg i get a bunch of stuff i have no clue. when searching for usb i get the following entries

[ 2219.299134] usb 5-1.3: USB disconnect, address 3
[ 2284.203182] usb 5-1.3: new full speed USB device using ehci_hcd and address 4
[ 2286.153525] usb 5-1.3: configuration #1 chosen from 1 choice

weird. i can't figure this out at all.

---

