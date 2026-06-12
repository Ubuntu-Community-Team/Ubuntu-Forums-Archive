---
title: "BASH - how to PUSH text to prompt from script"
date: 2015-12-22
forum: General Help
---

### Post by kapetr on 2015-12-22
Hello.

I want to make something like bash history do - to insert (push) text to command line to be able to edit it and then eventually to execute. And this all from script.

Example:

```

#!/bin/bash

clear
echo "Chose often used command:"; echo
echo " 1/       iwconfig wlan0; ifconfig wlan0"
echo " 2/       service network-manager stop"
echo " 3/       service network-manager start"
echo " 4/       killall wpa_supplicant"
echo " 5/       killall nm-applet"
echo " 6/       iwlist wlan0 scan"
echo " 7/       airmon-ng start wlan0"
echo " 8/       airodump-ng -c 9 mon0"  

read a
case $a in

        1)      echo -en "iwconfig wlan0; ifconfig wlan0" ;;
        2)      echo -en "service network-manager stop" ;;
        3)      echo -en "service network-manager start" ;;
        4)      echo -ev "killall wpa_supplicant" ;;
        5)      echo -en "killall nm-applet" ;;
        6)      echo -en "iwlist wlan0 scan" ;;
        7)      echo -en "airmon-ng start wlan0" ;;
esac


```

But I do not want do "echo -en", I want to push the text to parent (or current if sourced) BASH command line. Similar as when using history.

Any Idea ?

---

