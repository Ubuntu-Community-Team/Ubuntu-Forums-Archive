---
title: "2nd bluetooth device"
date: 2007-03-03
forum: General Help
---

### Post by fragos on 2007-03-03
I need to add a 2nd bluetooth device, LG VX8300 phone.  I already have a bluetooth PalmE2 working with Ubuntu.
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

