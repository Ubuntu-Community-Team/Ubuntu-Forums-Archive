---
title: "Make a Nokia 6850 Connect with Feisty via Bluetooth..."
date: 2007-09-09
forum: General Help
---

### Post by davideckels on 2007-09-09
[FONT="Century Gothic"][SIZE="3"]... in order to use KDE's Kmobiletools or Gnome's Phone Manager.

This worked for me! (nods to escariot from a helpful old post: 
[http://ubuntuforums.org/archive/index.php/t-28312.html](http://ubuntuforums.org/archive/index.php/t-28312.html)  )

1. Make sure you have the correct software installed:

> sudo apt-get install bluetooth gnome-bluetooth bluez-pin obexfs obexftp obexpushd

2. Open terminal as user:

> hcitool scan

3. Edit /etc/bluetooth/hcid.conf and /etc/bluetooth/rfcomm.conf files as below
(will need to chmod files to allow write access as a user)

4. Terminal:

> sudo /etc/init.d/bluetooth restart

5. Where XX:XX:XX:XX:XX:XX is the MAC of your phone, terminal:

> sdptool browse XX:XX:XX:XX:XX:XX

Will tell you if you're connected and if your phone supports Dial Up Networking or 
Generic Networking, and the channel supported upon.

6. Where 0 is the rfcomm port for your bluetooth device and 1 is the channel where
your phone supports networking, terminal:

> rfcomm connect 0 XX:XX:XX:XX:XX:XX 1

You'll need to set your PINs up correctly.

7. Start kmobiletools or phonemanager, and your phone should connect right up.

=======================
# /etc/bluetooth/hcid.conf
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
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	#pin helper: solves the silly "found but cannot connect" problem;
	pin_helper /usr/bin/bluez-pin;

	# Default PIN code for incoming connections, where XXXX is your pin
	passkey "XXXX"; 
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
========================
# /etc/bluetooth/rfcomm.conf
# RFCOMM configuration file.
#

rfcomm0 {
	# Automatically bind the device at startup
	bind no;

	# Bluetooth address of the device, where XX:XX:XX:XX:XX:XX is the MAC of your phone
	device XX:XX:XX:XX:XX:XX;

	# RFCOMM channel for the connection
	channel	10;

	# Description of the connection
	comment "Hello Dave";
}
==========================

**NOTE: Original typo caught too late: that's a Nokia 6085, not 6850.[/SIZE][/FONT]**

**APPEND:**
To clarify four bits: 
1. Kmobiletools and Gnome Phone Manager are installed via:
> sudo apt-get install kmobiletools gnome-phone-manager

2. To pair the computer to the Nokia 6085, on the 6085 dig into:
Menu > Settings > Connectivity > Bluetooth > Paired Devices > Options > Pair new device: press "Select" will search for computer to pair, prompt for a pin (enumerated in your /etc/bluetooth/hcid.conf file), and prompt for auto connection or prompted connection between the computer and phone. I choose auto connect, but consider your own security needs first.

3. To connect to Gnome Phone Manager, as user:
> gnome-phone-manager &
will open the applet in your notification area. Right click the applet and choose "Preferences", click on "Connection". Choose "Other port:" and enter /dev/rfcomm0 . Click "Apply" and "Close".
You should now be connected.

4. To connect to Kmobiletools, as user:
> kmobiletools &
will open the program windows and an applet. The first window will be an error, and open the configuration window.
Change "Mobile phone device" to /dev/rfcomm0 .
Click on the Mobile Phone icon to see these settings: change "Mobile Phone type" to Nokia (generic).
Click "Apply" and "OK".

Make sure your phone is still connected to rfcomm0 (via the rfcomm connect 0 XX:XX:XX:XX:XX:XX 1 command) and then click Settings > Reinitialize GSM device.

You should now be connected.

---

### Post by loell on 2007-09-09
nice :) , requesting staff, to transfer this in the How To section ;)

---

### Post by efrenefren on 2008-01-26
bluez-pin does not install in GUTSY

e@e-laptop:~$ sudo apt-get install bluez-pin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bluez-pin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bluez-pin has no installation candidate
e@e-laptop:~$ sudo apt-get install bluez-pin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bluez-pin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bluez-pin has no installation candidate

---

### Post by Marsellus Wallace on 2008-02-14
I have the same problem with **bluez-pin**

I got it working under my upgraded Gutsy around a week ago. But now that I have a fresh Gutsy set up. I can't install bluez-pin and without it the connection with my mobile phone breaks, when I enter the pin.

I tried installing bluez-pin from a debian package, but therefore I need dbus-1, which conflicts with dbus. Is there an other pin-helper program? Or is there an easy solution to install bluez-pin under gutsy.

---

### Post by efrenefren on 2008-03-18
you update first
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
then
```
sudo apt-get install bluez-pin
```

i think the reason i wasnt able to install bluez-pin is because i have installed kde-desktop. there must be conflicts between ubuntu-desktop. i dont know. but i did a fresh install but i didnt install kubuntu-desktop and i got bluetooth working

---

