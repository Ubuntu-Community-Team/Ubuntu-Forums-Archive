---
title: "Bluetooth PIN issues"
date: 2007-03-11
forum: General Help
---

### Post by pieroxy on 2007-03-11
I have followed a few HOWTO's to make bluetooth work and am stuck at the same point in all of them:

1. I got everything running up to the service discovery and the scanning. So "hcitool scan" gives me my phone and "sdptool browse aa:bb:cc:dd:ee:ff" gives me the list of services my phone exposes.

2. I tried "rfcomm connect 0 aa:bb:cc:dd:ee:ff 9", and my phone prompts me for the PIN. There, whatever I put I get the message "pin invalid" and the application stops with the message "Can't connect RFCOMM socket: Connection refused".

3. So I tried "obexftp -b aa:bb:cc:dd:ee:ff -B 9 -l" and same here. My phone asks for a PIN and whatever I get in, obexftp complains that the connection is refused and the phone tells me my PIN is invalid.

Of course, my /etc/bluetooth/pin contains the PIN I consistently try.

Any help over my problem?

---

### Post by fragos on 2007-03-11
default pin is 1234 and is stored in /etc/bluetooth/pin.

---

### Post by pieroxy on 2007-03-12
Thanks, but whatever I put in /etc/bluetooth/pin, the result is the same.

---

### Post by fragos on 2007-03-12
I'm not the expert here but I thought most cell phones use channel 10 and you seem to be using 9.

---

### Post by pieroxy on 2007-03-12
I don't think it's an issue of channel number (although I don't know what's wrong). I tried to sync the contacts with opensync and the moto-sync plugin configured to go through bluetooth. The moto-sync plugin takes only the MAC address of the BT device to go so...

And of course, always the same results: Invalid PIN on the phone and connection refused on the PC.

I am currently trying with two phones: A Motorola v500 and a Motorola RAZR v3

Oh well...

---

### Post by pakux on 2007-03-24
I had the same issue today... tried everything found in the forums, but nothing... always this same passkey error.

then, some guy mentions that you should restart the bluetooth services, and someone else says that first you must kill the hcid process. At that point, just before giving up, I tried the desperate solution: reboot. You're not going to believe me but somehow it triggered something and after the reboot a tiny window with the bluetooth logo popped up for a moment in the lower right corner (and that was new); then I tried to initiate the pairing process from the phone and bingo!

I know, I'm almost embarrassed, this sounds like an advise to the death blue screen... but  (funny) it worked !  give it a try...

---

### Post by Grayscale on 2007-03-24
Hey Guys, I've got a motorola v3i, and a kensington usb bluetooth dongle.  Having the same issue, invalid pin.  Even though I set it in hcid.conf.  I've tried EVERYTHING.  I can send files from my phone to my laptop without my phone or laptop asking for a pin but communicating from laptop to phone makes my phone ask for a pin.  Can people with working setups please post their hcid.conf file?

---

### Post by yigal.weinstein on 2007-03-27
I used 8 and got a connection

---

### Post by dddf on 2007-04-01
This is the default hcid.conf. Pin_helper is the most important row here. Bluepincat outputs pin from /etc/bluetooth/pin.

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
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	# if you want a interactiv query of your pin use /usr/bin/bluepin
	# /bin/bluepincat is using the pin in the /etc/bluetooth/pin file
	# pin_helper /usr/bin/bluepin;
	pin_helper /bin/bluepincat;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "BlueZ %h (%d)";

	# Local device class
	# e.g.
	#  0xsss100 = Computer
	#  0xsss104 = Computer Desktop
	#  0xsss108 = Computer Server
	#  0xsss10c = Computer Laptop
	# The 'sss' above defines the service-class (not quite, only the
	# first 11 bits, the next 11 define the device-class, than 2 format bits.)
	# See [https://www.bluetooth.org/foundry/assignnumb/document/baseband](https://www.bluetooth.org/foundry/assignnumb/document/baseband)
	# for more information.
	# 0x100bbb stands for "Object Transfer  (v-Inbox, v-Folder, ...)"
	# 0x020bbb stands for "Networking (LAN, Ad hoc, ...)"
	class 0x100100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	# valid parameters: enable | disable
	iscan enable;
	pscan enable;

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

	# Authentication and Encryption (Security Mode 3)
	auth disable;
	encrypt disable;
}

---

### Post by polomint on 2007-04-01
Which guide did you follow to get this config? as far as i can tell the pin_helper line is pretty much outdated.  newer bluetooth library uses dbus pin helpers and the settings stored in hcid.conf is ignored after hcid daemon is run for the first time.

On my configuration the gnome pin agent will pop up automatically if a connecting device is not paired. Once paired it will stay paired forever.

you might want to try the following:

1. ```
sudo aptitude install bluez-passkey-gnome
```
2. Add bt-applet to gnome's session, and make sure it is started.
2. restore the original hcid.conf. nothing needs to be changed, apart from the device name if you wish. 
3. Clear any persistant settings in case they are messed up (back up first recommended):
```
rm -r /var/lib/bluetooth/*
```
4. restart bluetooth by:
```
sudo /etc/init.d/bluetooth restart
```
5. try pairing again. if successful, a dialog box should pop up prompting you to enter code. note that once this is done,  you don't ever need to pair again, unless the settings are cleared of course.

hope the above works for you....

btw, this is my hcid.conf (the passkey line is useless because security is set to user):

```

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
	security user;

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
	name "%h";

	# Local device class
	# e.g.
	#  0xsss100 = Computer
	#  0xsss104 = Computer Desktop
	#  0xsss108 = Computer Server
	#  0xsss10c = Computer Laptop
	# The 'sss' above defines the service-class (not quite, only the
	# first 11 bits, the next 11 define the device-class, than 2 format bits.)
	# See https://www.bluetooth.org/foundry/assignnumb/document/baseband
	# for more information.
	# 0x100bbb stands for "Object Transfer  (v-Inbox, v-Folder, ...)"
	# 0x020bbb stands for "Networking (LAN, Ad hoc, ...)"
	class 0x3f0104;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	# valid parameters: enable | disable
	iscan enable;
	pscan enable;

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

### Post by Cresho on 2007-05-31
thanks for this post, i was able to get my razr paired correctly with the cell phone.

this sudo aptitude install bluez-passkey-gnome    and then I rebooted fixed my pair issue.

---

