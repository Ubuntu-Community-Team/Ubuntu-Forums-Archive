---
title: "admin privileges in scripts"
date: 2008-06-25
forum: General Help
---

### Post by Xbehave on 2008-06-25
how do I allow a user to run a bash script to run actions that require root privilege.

most of the commands the script launches require root privileges (i can remove those that dont if needed), but i want to let myself run the script, without being prompted for the password everytime. I've had a few ideas but im not sure how to do any of them:
[LIST]
[*]Chown it to root:users and use setuid 
[*]add the script to a list that i can run without being prompted in sudoers (would the be allowed to launch other stuff with root privileges?)
[*]store the root password in the script (allow users to execute, but not read it)
[*]none of the above
[/LIST]

my script is 
```
#!/bin/bash
LED=/proc/acpi/acer/wireless
read STATE < $LED

if [ $STATE = 0 ]
then
 modprobe -r ath_pci
 modprobe -r ath_rate_sample
 modprobe -r wlan_scan_sta
 modprobe -r wlan_tkip
 modprobe -r wlan
 killall NetworkManager
 kdialog --passivepopup "network unloaded" 10
else
 modprobe ath_pci
 Networkmanager
 kdialog --passivepopup "network loaded" 10
fi

exit
```

---

### Post by bodhi.zazen on 2008-06-25
make the script owned by root.root and run it as root with sudo.

sudo /path/to/script

Configure sudo to allow you to run the command without a password. Such is the power of sudo.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

