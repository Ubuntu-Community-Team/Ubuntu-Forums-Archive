---
title: "Bluetooth problem"
date: 2007-02-18
forum: General Help
---

### Post by Boule on 2007-02-18
Hi,

I have a bluetooth USB dongle, and I'm having trouble transferring files from/to my cellphone.
I installed bluez-utils and gnome-bluetooth, and when I try sending a file, my phone prompts for a pin. I tried 1234, and then the pc says unable to "connect".
I tried removing the security in /etc/bluetooth/hgid.conf, and it didn't solve anything.

Any ideas ?

Here's the hcid.conf file:

```
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security none;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

```

---

### Post by PartisanEntity on 2007-02-18
I am having the same problem, I recently installed edgy and am trying to pair my sony ericsson D750i with the laptop. Just as you mentioned, entering 1234 on the cell phone doesnt seem to match the pin number on the laptop even though my hcid.conf file also contains the standard 1234.

Ironically it works perfectly on my dapper installation.

---

### Post by PartisanEntity on 2007-02-18
Okay I got it to work:

In may case I looked through synaptic and installed bluez-passkey-gnome and gnome-bluetooth (both of which were not installed). I then had to restart the computer for it to work. Then I was able to pair my cell phone with Edgy.

---

### Post by Boule on 2007-02-18
Ok, thx for the tip, I'll try that... Well actually I'll just install bluez-passkey-gnome since I already have the other ones installed

---

### Post by Boule on 2007-02-21
ok, I've installed the passkey package, how do I use it ?

---

### Post by PartisanEntity on 2007-02-21
You have to initiate the connection from your cell phone, then Ubuntu should pop up a window where you can enter the PIN to match that on the cell phone.

---

### Post by MichaelSM on 2007-03-17
Hi. This is probably a useless comment but I'll continue anyway. For a start, you can go to Synaptic Package Manager and install anything with blu- blah blah you like. Or you can go terminal and do the bluez utils stuff. All good. OK. You also need the obex server file,which is in Synaptic. Why this isn't packaged with bluez I'll never know. When you try to mark and apply it, it yells at you with evil crap about being unauthorized etc. Just DO it. Have a look at [http://ubuntuliving.blogspot.com/2007/02/pairing-cellphone-with-ubuntu-via.html](http://ubuntuliving.blogspot.com/2007/02/pairing-cellphone-with-ubuntu-via.html) which will help. Copy and paste what the dude says. 
I'm a newbie to this too, and have had to learn the hard way, and if I stuff up just use your brains and back-pedal a bit.
Now, when the man says edit a conf file, as in   /etc/bluetooth/hcid.conf you have to go sudo as in $ sudo gedit /etc/bluetooth/hcid.conf which will bring up a box filled with crap. (probably at some stage you have to put in a password, I can't remember) Anyway, you'll wind up with a window which can be edited. Take a deep breath(as I did) and find the line of words 'security user' just down from the top of the heap .Click on  the end of it, delete it by back-spacing or however,, and replace it by typing in 'security auto'. Exit ASAP.
If you've downloaded all the bluez stuff, you ought to be able to go Applications>Accessories>Bluetooth File Sharing. Click it, and a tiny icon will appear in your task-bar. This means that it is able to search for transfers.
Oh, now, this is important. Linux hates usb stuff being disconnected and re-connected. When I couldn't get this working, I pulled out the dongle usb cable then re-started with it in. Suddenly everything started to work. 
It just takes practice.
I'm using a Nokia 6233. There is nothing more that I can say except that there's a bug patch I got from somewhere but if I found it, you can too. I wouldn't have a clue if it made any difference. 
As far as 'pairing' is concerned, I never had a problem. None of that pass-word stuff. The Nokia finally found my PC, or the reverse.
MOST IMPORTANTLY, BE PATIENT! I reckon it took a couple of re-starts and a lot of time before the magical moment arrived. We're talking 10 minutes here, friends.
There's been a lot written about creating a Launcher on desktop. I think it's pointless.If I want to send a file to my mobile I just right-click on it, go to Send To, and I have a choice of e-mail or Bluetooth Obex. You might have to wait a long time for the connection to establish in the dialogue box, but it will happen.
Basically I've just glossed over information gleaned from hours of hunting. If a dill like me can get Bluetooth up and running, so can anyone else. Cheers, Michael. PS you definitely need the obex server program.

---

### Post by fragos on 2007-03-17
I'd been struggling with pairing my LG VX8300 cell phone for a while.  In my case my Palm E2 PDA was already paired.  [http://ubuntuliving.blogspot.com/2007/02/pairing-cellphone-with-ubuntu-via.html](http://ubuntuliving.blogspot.com/2007/02/pairing-cellphone-with-ubuntu-via.html) gave me the answer I needed.  Changing security from user to auto did the trick for pairing.

---

