---
title: "Bluetooth Mighty Mouse passkey problems"
date: 2007-06-06
forum: General Help
---

### Post by cbozic on 2007-06-06
I am trying to get an Apple bluetooth Mighty Mouse to work with a dell pc running Feisty.

"sudo hidd --search" reveals the bluetooth ID of the Mighty Mouse and then a popup dialog appears prompting me for a passkey.  I've tried everything from "1234" to my password but anything I type in that box results in a connection failure to be returned from hidd.  

"Can't create HID control channel: Connection refused"  is the exact error I get.  

Does anyone have any thoughts?

/etc/bluetooth/hcid.conf
```

# HCId options
options {
	# Automatically initialize new devices
	autoinit no;

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


part of /etc/default/bluetooth
```

BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--connect MY_MOUSE_ADDRESS_HERE --master --server"

```

---

### Post by viciouslime on 2007-06-06
I believe the passkey is 0000

---

### Post by cbozic on 2007-06-06
Thanks!  That was all I needed to get my mouse working!  :)

---

### Post by viciouslime on 2007-06-07
> **cbozic said:**
> Thanks!  That was all I needed to get my mouse working!  :)

You're welcome :)

---

### Post by j4play on 2007-06-09
having same problem here, keep getting message:
"Can't create HID control channel: Connection refused"

well, mouse has been working fine for last month or so, until i rebooted in windows where i had to re-pair mighty mouse.

now on booting in (k)ubuntu, it won't connect.  hidd search finds it, and attempts to connect but fails. 

i've tried hidd --search, hidd --connect [bt mac], hcitool scan (which finds it).....
tried taking battery out of mouse and replacing it, resetting mouse

any ideas?

---

### Post by j4play on 2007-06-10
should i perhaps try and reinstall bluez?  don't really want to mess with it, as its been working fine till now, but not sure what else to try....

---

### Post by j4play on 2007-06-10
bump

---

### Post by j4play on 2007-06-10
now fixed.

after reading this:
[http://docs.kde.org/development/en/extragear-pim/kdebluetooth/concepts.html](http://docs.kde.org/development/en/extragear-pim/kdebluetooth/concepts.html)

realised that there was some issue with bluetooth keys (or something).  though the file link_key doesn't exist, i found that removing all subdirectories of /var/lib/bluetooth/ allowed me to repair the mouse.

---

### Post by sfenton on 2007-06-12
I've been having the same problems.  Bluetooth/default is the same as is hcid.conf. 

I've tried deleting the /var/lib/bluetooth directory. It's the same address as my bluetooth receiver in my T60. I've also captured my syslog below. 

Any help would be appreicated. 

Jun 11 23:20:16 ubuntu hcid[8803]: link_key_request (sba=xx:xx:xx:xxT60, dba=XX:XX:XX:XX:mightmouse)
Jun 11 23:20:16 ubuntu hcid[8803]: pin_code_request (sba=xx:xx:xx:xxT60, dba=XX:XX:XX:XX:mightymouse)


sudo hidd --search
Searching ...
        Connecting to device XX:XX:XX:XX:mightymouse
Can't create HID control channel: Connection refused


Cheers,

---

### Post by Ron F. on 2007-11-28
I struggled with this problem for a while.

My problem was that  I was attempting to use my bluetooth adapter and my wireless Mighty Mouse on both my laptop and my desktop. That turned out to be a disaster.

I can get a separate bluetooth adapter for each of my machines, but will that solve the problem? Won't I still run into the same mess just moving the mouse back and forth between the two machines?

Anyway, deleting the /var/lib/bluetooth/* subdirectory for my bluetooth adapter and then running /etc/init.d/bluetooth restart, allowed hidd --search to work. The subdirectory was recreated and my Ubuntu Gutsy laptop connected to my mouse again.

The mouse is running now. I think hidd ought to be a bit smarter than just providing a "connection refused" message for something that is only a mouse. Or - is the problem in the bluetooth daemon?

-Ron

---

