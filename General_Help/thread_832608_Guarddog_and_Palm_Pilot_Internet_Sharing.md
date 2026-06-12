---
title: "Guarddog and Palm Pilot Internet Sharing"
date: 2008-06-17
forum: General Help
---

### Post by lumpy211 on 2008-06-17
Hi everybody,

I followed the instructions [here]("https://help.ubuntu.com/community/PalmBluetoothHowto") to get internet sharing with my Tungsten E2. However, this only works with Guarddog disabled, which I really don't want to do. I'm assuming it has something to do with Guarddog undoing the operations done by the following lines:

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
iptables -A FORWARD -i ppp0 -j ACCEPT 
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
```

I've tried figuring out how to do this manually in Guarddog, but I haven't had any luck. Has anybody had any success setting up internet sharing with a Palm device and still having Guarddog enabled?

Thank you in advance!

---

### Post by lumpy211 on 2008-06-18
*Bump*

I tried a few more things to no avail. I tried using Guidedog with Guarddog but none of the configurations I tried worked. I enabled Masquerading and forwarded my DNS (53) and HTTP (80) ports to the ip address I'm using for my Palm device (192.168.2.2) with no results. In Guarddog, I created a zone for my Palm device and allowed communication between the Internet, Local, and Palm on the aforementioned protocols, as well as pinging. I cannot ping my DNS server or any pages with Mergic Ping.

I ditched Guarddog and tried Firestarter and KMyFirewall. Both seem to work once I run /etc/init.d/startbluetooth.sh as root. However, it's annoying to run this script every time I connect, especially if I'm across the room.

I found that if I run the command
```
tail -f /var/log/messages | grep "remote IP address 192.168.2.2"
```
I can get a terminal to write a line every time I connect with my Palm. I'm not very familiar to bash scripting, but is there any way that I can run /etc/init.d/startbluetooth.sh every time that particular line is written to that log file?

I'd still like to try using Guarddog/Guidedog together, so if anybody has gotten them working with a Palm, please let me know.

---

### Post by unutbu on 2008-06-18
Forgive me since I only understand about half the words in your posts, but if you want a certain command to be run every time your Palm is connected, have you tried System>Preferences>Removable Drives and Media? Click on the PDAs tab.

---

### Post by lumpy211 on 2008-06-18
Well, this is a weird way of doing it, but it works with Firestarter!

Create a file in whatever directory you like. I did it in ~/Programs. Enter the following code:

```
#!/bin/bash

if=/var/log/messages;
wd="remote IP address 192.168.2.2";

# instruction to execute each time someword is found in somelog
action="/etc/init.d/start_bluetooth.sh & echo 'Connecting...starting up Bluetooth'";

# change occasional '/' in wd into \/ this change is needed to allow
# usage of var wd between / and / in pattern for awk.
wd=$(echo "$wd"|sed -e "s#/#\\/#g;";);

if [ ! -f ${if} ]; then
  echo "file ${if} to monitor, not found." >&2;
else
#real action
  tail -f ${if}|\
  awk -W interactive "/${wd}/{print \"${action}\"; fflush();}"|\
  bash
#end of real action
fi
```

and chmod the file to 755. Now if you run it in the background (as root) it'll restart Bluetooth with Firestarter every time you connect your Palm pilot!

I got the code for the bash script from [here]("http://www.linuxquestions.org/questions/linux-software-2/shell-script-find-word-run-command-192490/").

---

### Post by lumpy211 on 2008-06-26
Okay, so I've noticed now that there is a new problem... I can't use HotSync without disabling Firestarter. The script I've posted above works for internet sharing.

So, if I change the LAN connected device to ppp0 (with internet connection sharing activating) everything with HotSync works fine. However, since ppp0 is not always connected, Firestarter gives me errors when I try to start it when my Palm is not connected via bluetooth:

"Internal network device ppp0 is not ready. Aborting.." (in a terminal)
"The device ppp0 is not ready. Please check your network device settings and make sure your internet connection is active." (in a dialog box)

So obviously that's no good, because if I have it setup like that I can only have the firewall on when my Palm is connected!

By changing the LAN forwarding device to wlan0 (my connected device) I can start Firestarter. Stopping the firewall during HotSync then gives me no problems, so I know it's something to do with Firestarter. This even happens when I stop the script that I posted before, so it's not a problem with that. The nice thing, however, is that the firewall restarts itself after my Palm disconnects. Really, then, the only thing I have to do is to manually disable Firestarter for the brief time that I'm HotSyncing OR change my LAN connected device to ppp0 while my Palm is connected (preferred).

Is there any way that I can change my script about a bit to change my "LAN Connected Device" in preferences to ppp0 when the Palm connects and disables it when I disconnect again?

Any suggestions?

---

