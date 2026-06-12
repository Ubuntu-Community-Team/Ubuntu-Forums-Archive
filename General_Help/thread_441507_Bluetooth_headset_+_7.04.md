---
title: "Bluetooth headset + 7.04"
date: 2007-05-12
forum: General Help
---

### Post by rjharv on 2007-05-12
Hi all,

I'm having real trouble getting my Bluetrek G2 headset working with ubuntu 7.04.

I believe its connected, I've had a pin request from the gnome bluetooth applet and that seemed to go ok. However I can't play any sound though it, or use the microphone.

Please can someone give some pointers of the steps i have to take. I've been through the forums and found a couple of links they but only seem to go to the stage where it connects.

This is also my output from the btsco command

rjharv@laptop:~$ btsco -v XX:XX:XX:XX:XX:XX
btsco v0.42
Device is 1:0
Error: Failed to connect to SDP server: No route to host
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Host is down

The laptop is a IBM T43p

---

### Post by fragos on 2007-05-12
Getting bluetooth to work is a rather involved process and headsets are a special case which I haven't tried yet.  Here's a copy of my /etc/rc.local script that shows what I had to add to get bluetooth up and running with my Palm E2.  I would assume you have something similar and if you don't that might explaine your problem.

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
rfcomm bind /dev/rfcomm0 00:07:E0:6F:85:DE 10
exit 0

---

