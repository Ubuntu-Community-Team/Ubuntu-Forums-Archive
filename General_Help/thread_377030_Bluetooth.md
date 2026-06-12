---
title: "Bluetooth"
date: 2007-03-05
forum: General Help
---

### Post by g3brownsc on 2007-03-05
I have worked for almost three months off and on on this problem. Gnome Bluetooth just doesnt work. I worked hard at it, and i got my phone to pair with my computer (once in a while) i worked harder, and i got my phone to be listed under devices i could send files to under bluetooth send. I try to send a file to my phone, and Gnome Bluetooth hangs like it's its job. 
It is my understanding, from various threads and development sites, that Gnome bluetooth, in it's current state, does not work. 
I would love to know if anyone has been able to send/recieve files from thier phone using any other programs.

---

### Post by strabes on 2007-03-05
I haven't used it but bluetooth apparently works out of the box in kubuntu.  You could try installing KDE or kubuntu-desktop.

---

### Post by fragos on 2007-03-05
After a learning curve I've been able to consistently send files from Ubuntu to my Palm E2.  I never have been able to succeed in the other direction.  I recently got a new cell phone LG VX8300 with bluetooth but have yet been able to make it pair with Linux.  Everything I've come accros discuses connecting a single bluetooth device so I have some questions about how does the configuration change when there's more than one device to pair with.  I specifically asked that question backed up with considerable research but nobody has chosen to respond. Acopy of that post follows.  I hope my data can be of help to you.

---------------------------------------------

Add 2nd bluetooth device, LG VX8300 phone.  
I already work with a bluetooth PalmE2.
The phone has a MAC of 00:19:A1:58:12:87 and an ID "LG VX8300".
Best guess is the phone uses bluetooth channel 10.
I believe I'll have to edit /etc/rc.local and /etc/bluetooth/rfcomm.conf.
The changes I believe I have to make to these two files are below.  For illustration purposes the new lines start with ^^.  My question is am I on the right path here -- please comment.

#/etc/rc.local
#Start Bluetooth for Palm E2
modprobe l2cap
modprobe rfcomm
mknod /dev/rfcomm0 c 216 0
^^mknod /dev/rfcomm1 c 216 0
sdptool add --channel=10 OPUSH
rfcomm bind /dev/rfcomm0 00:07:E0:6F:85:DE 10
^^rfcomm bind /dev/rfcomm1 00:19:A1:58:12:87 10
exit 0

#/etc/bluetooth/rfcomm.conf
rfcomm0 {
device 00:07:E0:6F:85:DE;
channel 10;
comment "connected Geo & PalmE2";
}
^^rfcomm1 {
^^device 00:19:A1:58:12:87;
^^channel 10;
^^comment "connected Geo & VX8300";
^^}

---

### Post by g3brownsc on 2007-03-06
Thanks for the replies, guys. 
Strabes- I've heard that too, but I dont like kde and have aleady been using regular ubuntu for too long to turn back now. 
Fragos- All of the information i've gathered has dealt with hcitool commands, the use of which has given me most of the information im working off of. ive been able to pair with hcitool, see the phone once in a while in gnome send, and thats it. I guess the learning curve has outran me for now.
I'm only using one device, so I hope that keeps things simple, but to complicate things, I dont know what /etc/rc.local and /etc/bluetooth/rfcomm.conf *are*, exactly. If you could elaborate on what some of the lines in both of those files do, or what the additions do at least, it would be very helpful. 
Thanks, g3brownsc

---

### Post by fragos on 2007-03-06
/etc/rc.local is executed during startup for purposes like loading drivers.  In my case these commands were required to startup bluetooth for recognizing my Palm E2.  /etc/bluetooth/rfcomm.conf is the configuration file user for pairing my Palm.  It includes the MAC address of my Palm and the bluetooth channel to pair with.  /dev/rfcomm0 is a mount point for my bluetooth interface.  I arrived at this information by following howto files I found on the Ubuntu web site.

---

### Post by g3brownsc on 2007-03-07
I've set up my config files as such: 

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
#Start Bluetooth for Palm E2
modprobe l2cap
modprobe rfcomm
mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
rfcomm bind /dev/rfcomm0 00:19:a1:3f:54:b2
exit 0


#
# RFCOMM configuration file.
#

#rfcomm0 {
#	# Automatically bind the device at startup
#	bind no;
#
#	# Bluetooth address of the device
#	device 11:22:33:44:55:66;
#
#	# RFCOMM channel for the connection
#	channel	1;
#
#	# Description of the connection
#	comment "Example Bluetooth device";
#}
rfcomm0 {
bind yes;
device 00:19:a1:3f:54:b2;
channel 10;
comment "Bluetooth link to LG Cu400";
}

Still nothing, bluetooth send to stalls when i try to send an image to phone and vice versa. Unsure of where to go from here.

---

### Post by fragos on 2007-03-07
What happened when you paired the phone with Linux.  One Linux is configured you have to initiate pairing from the phone.  when you pair you will be asked enter the pin code.  That 4 digit code is stored in /etc/bluetooth/pin.  Default is usually 1234.  If you run hciconfig on the command line you'll get the status of bluetooth on the Linux end.  Mine looks as follows:

fragos@Geo:~$ hciconfig
hci0:   Type: USB
        BD Address: 00:0B:0D:08:38:E8 ACL MTU: 120:20 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:639 acl:0 sco:0 events:17 errors:0
        TX bytes:316 acl:0 sco:0 commands:17 errors:0

---

### Post by g3brownsc on 2007-03-07
g3brownsc@g3brownsc-laptop:~$ hciconfig
hci0:   Type: USB
        BD Address: 00:02:5B:01:3E:6A ACL MTU: 384:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:1278 acl:0 sco:0 events:32 errors:0
        TX bytes:386 acl:0 sco:0 commands:24 errors:0

immediately after the phone and computer successfully paired.
Still fails to send anything or recieve anything, is stuck at the attached screen. Interestingly, the phone acknowledges that a bluetooth file is trying to be sent (when i attempted to delete the pairing link for the laptop, it said cannot delete, file transfer in progress), but does not display the bt file in transit icon that it does when transferring files with another phone.
I've let this screen chill for about 10 minutes and nothing has happened.

---

### Post by fragos on 2007-03-07
Your cell phone may not support OBEX file transfers.  I believe those bluetooth utilities are using it.  You may find it easier with faster transfer rate to connect to your cell with a USB cable.  Check out bitpim which is in the Ubuntu repositories.  Bitpim works with many cell phones but not all.

---

### Post by g3brownsc on 2007-03-07
My cellphone is OBEX compatible, ive done this before with other computers. But i will check out Bitpim, it sounds it does the same thing. 
I've had a lot of trouble with bluetooth, this is my second fresh install it wont work on, so i guess at this point gnome bluetooth just does not work with my hardware. 
Maybe BluetoothManager will provide a solution for me in the near future. [http://live.gnome.org/BluetoothManager](http://live.gnome.org/BluetoothManager)

[EDIT] Just tried Bitpim, my phone is newer and isnt supported, so I'd like to follow up on my bluetooth woes. I've posted my config files above, and if i absolutely cant get gnome bluetooth to work, is there something else that does?

---

### Post by g3brownsc on 2007-03-13
Anyone know where to go from here?

---

### Post by rajman on 2007-11-16
i've managed to get bluetooth working under gnome. however, bitpim is stubborn as hell. somehow it worked under OS X with bluetooth, but now that i have a usb bluetooth dongle it refuses to work.

---

### Post by cdean on 2007-12-05
This is the best tutorial I've seen yet.

[http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/](http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/)

However, it doesn't handle setting up the local scripts to establish the rfcomm connection at boot. Ideally, Bitpim should have a facility to do this upon its own launch because the phone may not always be present when the script launches.

---

