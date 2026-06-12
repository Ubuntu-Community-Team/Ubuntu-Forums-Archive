---
title: "Shell Scipt"
date: 2008-06-04
forum: General Help
---

### Post by psylance on 2008-06-04
How can i create a shell script to activate my wireless connection  when needed? Newbie in ubuntu, currently playing around with it.

for eg, 

whenever i type : wlanstart <wireless adaptor 1/2>

it would grab a dhcp address from my access point. As shown, i have 2 adaptor and this should direct which adaptor to get the ip add from dhcp server

---

### Post by cmnorton on 2008-06-04
Depending on how you are configured, it should be possible to use network manager to find your wireless network and then connect from within Network Manager.

I am curious as to why you would not want to stay connected all the time.

---

### Post by nick_h on 2008-06-04
To learn shell scripting have a look at [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

To create a simple script to bring up an interface, write the following into a file called *wlanstart*:
```
#!/bin/bash
sudo ifup wlan0

```

Then make the file executable with:
```
chmod a+x wlanstart
```

Run it with:
```
./wlanstart
```

It is convenient to put it in your PATH, for example ~/bin.

---

### Post by fragos on 2008-06-04
Right click the network manager icon in the upper applet bar and disable networking. Enable it later and it will start up again. My Dell laptop has a switch on the front to turn off the WiFi radio.

---

### Post by psylance on 2008-06-04
I'm using server edition to play around.

---

### Post by werries on 2008-06-04
on my desktop, which has badly supported drivers for wireless, i chose to do it myself.
i use the command
```
sudo iwconfig wlan0 essid <my_essid> key <my_key> && sudo dhclient
```
im not sure if that would work as a bash command, but i know it works just fine to connect w/ dhcp.

---

### Post by nick_h on 2008-06-05
That should work in a bash script.

It would also be easy to extend a script to handle more than one interface.

---

### Post by bodhi.zazen on 2008-06-05
> **werries said:**
> on my desktop, which has badly supported drivers for wireless, i chose to do it myself.
i use the command
```
sudo iwconfig wlan0 essid <my_essid> key <my_key> && sudo dhclient
```
im not sure if that would work as a bash command, but i know it works just fine to connect w/ dhcp.

And, you do not need sudo in the script. Just:

[quote]iwconfig wlan0 essid <my_essid> key <my_key>; dhclient[/qoute]

Then:

```
sudo <script>
```

In general, for security considerations, any script that will be run as root should be owned by root and run with sudo. Try to avoid using sudo within a script to run a command as root. Within a script you can sudo -u to run a command as a non-root user.

---

