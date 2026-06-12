---
title: "Ubuntu equivilent of Fedora rc.local?"
date: 2007-03-06
forum: General Help
---

### Post by speedway on 2007-03-06
Hi all

I am about to move my MythTv machine over to Ubuntu but I need to put things in the Ubuntu equivilent of Fedora's rc.local file. Only problem is, is that I have no idea where to find what I am looking for.

I need it to have my TV cards recognised properly and on the Fedora version this is placed into rc.local to help out:

> 
#!/bin/bash

touch /var/lock/subsys/local
# Remove modules
/sbin/modprobe -r cx88-blackbird
/sbin/modprobe -r cx88-dvb
/sbin/modprobe -r saa7134
/sbin/modprobe -r saa7134-dvb
/sbin/modprobe -r dvb-bt8xx
/sbin/modprobe -r bttv
# DVB
/sbin/modprobe cx88-dvb
/sbin/modprobe cx88-alsa
/sbin/modprobe saa7134-dvb
/sbin/modprobe saa7134-alsa
/sbin/modprobe b2c2-flexcop-pci
/sbin/modprobe cinergyT2
/sbin/modprobe pluto2
/sbin/modprobe budget
/sbin/modprobe dvb-ttpci
/sbin/modprobe dvb-bt8xx
/sbin/modprobe budget-av
/sbin/modprobe budget-ci
/sbin/modprobe em28xx
/sbin/modprobe saa7146_vv
/sbin/modprobe ir-kbd-i2c
/sbin/modprobe -r cx88-blackbird
sleep 5
chmod -R 777 /dev/dvb/adapter0
chmod -R 777 /dev/dvb/adapter1
chmod -R 777 /dev/dvb/adapter2
Can anyone tell me what I am looking for? It would be very much appreciated.

Cheers
Bruce

---

### Post by llamakc on 2007-03-06
Have you looked in /etc yet? I have an /etc/rc.local file there:

```

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

exit 0

```

---

### Post by superm1 on 2007-03-06
> **speedway said:**
> Hi all

I am about to move my MythTv machine over to Ubuntu but I need to put things in the Ubuntu equivilent of Fedora's rc.local file. Only problem is, is that I have no idea where to find what I am looking for.

I need it to have my TV cards recognised properly and on the Fedora version this is placed into rc.local to help out:

Can anyone tell me what I am looking for? It would be very much appreciated.

Cheers
Bruce
That's quite a list of cards there.  I'm assuming you do all of that so that there is absolutely no confusion about which card gets /dev/video0, /dev/dvb0 etc, right?

---

### Post by speedway on 2007-03-06
> **llamakc said:**
> Have you looked in /etc yet? I have an /etc/rc.local file there:

```

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

exit 0

```
Oops, now I feel like a right idiot! I did a search on Google first and assumed the Debian way as the Ubuntu way. Pays to look at the machine first huh? :)


> **superm1 said:**
> That's quite a list of cards there.  I'm assuming you do all of that so that there is absolutely no confusion about which card gets /dev/video0, /dev/dvb0 etc, right?

That rc.local is from MythDora so yes, I assume the designer does that to not only ensure the cards are recognised but also in the same place every time....

Cheers
Bruce

---

