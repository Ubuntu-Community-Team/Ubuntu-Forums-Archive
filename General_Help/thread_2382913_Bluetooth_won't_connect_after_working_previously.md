---
title: "Bluetooth won't connect after working previously"
date: 2018-01-18
forum: General Help
---

### Post by judahwolf on 2018-01-18
I am using Ubuntu 16.04 on a Lenovo thinkpad E520. 

I have a bluetooth speaker that was working perfectly for a month or so until today. Now it will no longer connect, after a routine update yesterday (not sure if this is connected). The only way I can get it to connect is to remove the device from my bluetooth settings completely, then use device discovery to connect; however, it then disconnects within seconds and the same problem reoccurs. This speaker will connect to my phone fine. 

I have tried various fixes. Usually the common element is that they ask to input the following command:

```
load-module module-bluetooth-discover
```

But this only returns the response:

```
Failure: Module initialization failed
```

These are the fixes I tried. They either had no effect, or I was stymied at the error I just mentioned:

[https://askubuntu.com/questions/831732/bluetooth-paired-but-not-connected-ubuntu-16-04](https://askubuntu.com/questions/831732/bluetooth-paired-but-not-connected-ubuntu-16-04)
[https://askubuntu.com/questions/634382/bluetooth-speaker-pairs-but-wont-connect](https://askubuntu.com/questions/634382/bluetooth-speaker-pairs-but-wont-connect)
[https://askubuntu.com/questions/689281/pulseaudio-can-not-load-bluetooth-module-15-10-16-04-16-10](https://askubuntu.com/questions/689281/pulseaudio-can-not-load-bluetooth-module-15-10-16-04-16-10)

Thanks!

---

### Post by #&amp;thj^% on 2018-01-18
No promises here but can we see the contents of this.

```
gedit /usr/bin/start-pulseaudio-x11
```

paste back so we can see.

---

### Post by judahwolf on 2018-01-18
```
#!/bin/sh

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.


set -e


if [ x"$DISPLAY" != x ] ; then


    /usr/bin/pactl load-module module-x11-publish "display=$DISPLAY" > /dev/null
    /usr/bin/pactl load-module module-x11-bell "display=$DISPLAY" "sample=bell.ogg" > /dev/null
    /usr/bin/pactl load-module module-x11-cork-request "display=$DISPLAY" > /dev/null


    if [ x"$KDE_FULL_SESSION" = x"true" ]; then
       /usr/bin/pactl load-module module-device-manager "do_routing=1" > /dev/null
    fi


    if [ x"$SESSION_MANAGER" != x ] ; then
	/usr/bin/pactl load-module module-x11-xsmp "display=$DISPLAY session_manager=$SESSION_MANAGER" > /dev/null
    fi
    /usr/bin/pactl load-module module-bluetooth-discover
fi
```

---

### Post by #&amp;thj^% on 2018-01-18
Mine looks like this:
```
  GNU nano 2.9.2                                                   /usr/bin/start-pulseaudio-x11                                                              
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

set -e

if [ x"$DISPLAY" != x ] ; then

    /usr/bin/pactl load-module module-x11-publish "display=$DISPLAY" > /dev/null
    #/usr/bin/pactl load-module module-x11-cork-request "display=$DISPLAY" > /dev/null

    if [ x"$KDE_FULL_SESSION" = x"true" ]; then
       /usr/bin/pactl load-module module-device-manager "do_routing=1" > /dev/null
    fi

    if [ x"$SESSION_MANAGER" != x ] ; then
    /usr/bin/pactl load-module module-x11-xsmp "display=$DISPLAY session_manager=$SESSION_MANAGER" > /dev/null
    /usr/bin/pactl load-module module-bluetooth-discover   
    fi
fi

```
maybe give that a try, with 16.04 Bluetooth is a bit flakey so remove the device and try to pair it again after the change has been made..

---

### Post by judahwolf on 2018-01-18
After doing that and re-pairing the speaker, it connected for about 10 seconds, before the speaker went back to blinking, searching for a connection. Ubuntu still says they are connected, but the speaker has disappeared from the sounds output options. It cut out right in the middle of a test sound clip I was running.

---

### Post by judahwolf on 2018-01-19
I installed blueman to see if it would help, and it connected and played for a bit before disconnecting. Blueman swore they were connected, but when I actually tried to reconnect or change settings, the status went to disconnected, and the following error was returned:

```
Connection Failed: blueman.bluez.errors.DBusFailedError: Resource temporarily unavailable

```

---

### Post by #&amp;thj^% on 2018-01-19
You may have this installed already but what dose this show;
```
apt policy pulseaudio-module-bluetooth
```
If you can also try on a (live) Ubuntu  first, so that you can have an idea if the problem is in the BT stack version. Ubuntu 16.04 had a bluetooth stack update which significantly broke BT functionality.

---

### Post by judahwolf on 2018-01-19
```
pulseaudio-module-bluetooth:  Installed: 1:8.0-0ubuntu3.7
  Candidate: 1:8.0-0ubuntu3.7
  Version table:
 *** 1:8.0-0ubuntu3.7 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:8.0-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

---

### Post by #&amp;thj^% on 2018-01-19
Report any errors from this command:
```
pactl load-module module-bluetooth-discover
```
And sometime when you get a chance try to pair it with a Live CD/USB Installer just to check it works without dropping.

---

### Post by judahwolf on 2018-01-19
```
Failure: Module initialization failed

```

If I unload first, then reload, then it outputs a number like "24" - but does not do anything to improve the connection when I retry it.

---

### Post by #&amp;thj^% on 2018-01-19
One other suggestion then, try connecting your WiFi network to 5.4Ghz if not already.
Bluetooth uses 2.4Ghz channels and could be overcrowded in your location.
Sorry not more helpful here.:(

---

