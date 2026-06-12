---
title: "libgphoto2 udev error message"
date: 2007-03-08
forum: General Help
---

### Post by kadallas on 2007-03-08
After update (3/8/2007) to latest version of libgphot02-port0 I am getting an error message at boot time from udev.  The message says add_to_rules unknown key 'attrs{idvendor}' or 'attrs{idproduct}'. The error message is recorded in var/log/syslog and seems to come from /etc/udev/rules.d/45-libgphoto2.rules.  

I am not trying to connect a digital camera or anything like that.

Everything seems to work on my system but I get concerned when new messages start showing up at boot time.

Any ideas on how I should resolve these messages?  :confused: 

Thanks

---

### Post by foormea on 2007-03-08
hey
exact same thing happening here

---

### Post by foormea on 2007-03-08
i'm definitely not a linux expert (although i hope that i'll be one some day :D) but from what i can understand, these messages are no problem
if you really do wanna get rid of them, just > mv 45-libgphoto2.rules 45-libgphoto2.rules.backup or something and that will do
i've very quickly read something about udev and i guess for our 'problem', udev tries to 'mount' the inexisting cameras to some /dev/...... files but can't find any cameras, hence the error messages. maybe there's a way to turn udev to a non-verbose mode? that might be better than completely disabling the 45-libgphoto2.rules

i don't know if what i've just said is right or wrong, so please a jedi master correct me if needed!!

---

### Post by foormea on 2007-03-08
for people who actually understand (hint hint: not me), here's the /etc/udev/rules.d/45-libgphoto2.rules :

> # udev rules file for libgphoto2 devices (udev >= 0.98)
#
SUBSYSTEM!="usb*", GOTO="libgphoto2_rules_end"
ACTION!="add", GOTO="libgphoto2_rules_end"

ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="0403", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="0404", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04fc", ATTRS{idProduct}=="504b", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04fc", ATTRS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="08ca", ATTRS{idProduct}=="0111", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04fc", ATTRS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04fc", ATTRS{idProduct}=="504b", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="120a", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="2770", ATTRS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="093a", ATTRS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="093a", ATTRS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="2770", ATTRS{idProduct}=="913c", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0919", ATTRS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="093a", ATTRS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04a5", ATTRS{idProduct}=="3003", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="3047", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="30c0", MODE="0660", GROUP="plugdev"
another tonnes of such lines
then the end of the file is:
> ATTRS{idVendor}=="06d6", ATTRS{idProduct}=="002d", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="04fc", ATTRS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0797", ATTRS{idProduct}=="801a", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0d64", ATTRS{idProduct}=="1001", MODE="0660", GROUP="plugdev"
PROGRAM="check_ptp_camera 06/01/01", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="2770", ATTRS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="2770", ATTRS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="093a", ATTRS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="0c45", ATTRS{idProduct}=="800a", MODE="0660", GROUP="plugdev"
ATTRS{idVendor}=="2770", ATTRS{idProduct}=="905c", MODE="0660", GROUP="plugdev"

LABEL="libgphoto2_rules_end"

---

### Post by larini on 2007-03-10
Problems with me too.
After upgrading to libgphoto2 v 2.3.0 my Nikon coolpix 880 is not working any more.
I had to downgrade to v 2.2.1 to work again.

The problem is: ubuntu always says that there is actualization to do.
There is a way to ignore the 2.3 version??

(please someone correct this bugged version!)

---

### Post by justwannasearch on 2007-03-10
check this thread: [http://ubuntuforums.org/showthread.php?p=2270082#post2270082](http://ubuntuforums.org/showthread.php?p=2270082#post2270082)
should fix it.

---

### Post by larini on 2007-03-10
nop, my file has no ATTRS occurences.
The problem still remains.

---

### Post by justwannasearch on 2007-03-11
> **larini said:**
> nop, my file has no ATTRS occurences.
The problem still remains.

Your problem appears to be different from the others.
I'd suggest to:
1) Install you prefered libgphoto version.
2) Start Synaptic.
3) Select libgphoto in the package list.
4) Select "Package" -> "Lock version" in Synaptics main menu.

The "New updates availabe" message should vanish then. 
Hope that helps.

---

