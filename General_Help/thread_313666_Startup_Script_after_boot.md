---
title: "Startup Script after boot"
date: 2006-12-06
forum: General Help
---

### Post by Chouca on 2006-12-06
How hard can it be?  ](*,) 

I have a script that starts my wireless connection in Xubuntu. From the panel it works like a charm. 

I would like it to auto startafter a cold start, suspend or hibernate.

I have tried to use "Autostarted Applications", adding it to the init.d folder with sudo update-rc.d afterwards, I have tried to add it in rc.local.

All with the common result - id does NOT work   :evil: 

Any ideas out there?

Martin

---

### Post by djf_jeff on 2006-12-06
Can I see your script please?

It may be that it don't have the right user to start the script or something like this.

---

### Post by Chouca on 2006-12-06
Hi

The script that works from the panel looks like this;

```
/usr/bin/sudo /sbin/iwconfig wlan0 mode "Managed"
/usr/bin/sudo /sbin/iwconfig wlan0 essid "wiXXXXXXX_235"
/usr/bin/sudo /sbin/iwconfig wlan0 key XXXX-XXXX-XX
/usr/bin/sudo /sbin/iwconfig wlan0 key open
/usr/bin/sudo /sbin/dhclient wlan0 
```


Regards

Martin

---

### Post by djf_jeff on 2006-12-07
It will surely not autostart in Gnome because you use sudo and it need you to enter a password.

Just tried these lines in /etc/rc.local, before exit 0 :

```

/sbin/iwconfig wlan0 mode "Managed"
/sbin/iwconfig wlan0 essid "wiXXXXXXX_235"
/sbin/iwconfig wlan0 key XXXX-XXXX-XX
/sbin/iwconfig wlan0 key open
/sbin/dhclient wlan0
```

---

### Post by Chouca on 2006-12-13
Hi,

sorry for the delay I have  reinstalled to get a light Xubuntu.

I can connect to the wireless from a terminal by;

```
root@ubuntu:/home/martin# sudo iwconfig wlan0 essid wirxxxxx_235
root@ubuntu:/home/martin# sudo iwconfig wlan0 key xxxx-xxxx-xx
root@ubuntu:/home/martin# sudo iwconfig wlan0 key open
root@ubuntu:/home/martin# sudo  dhclient wlan0
```

Still the same startup problem, though. The /etc/rc.local file is now;

```
/sbin/iwconfig wlan0 mode Managed
/sbin/iwconfig wlan0 essid wireless_235
/sbin/iwconfig wlan0 key xxxx-xxxx-xx
/sbin/iwconfig wlan0 key open
/sbin/dhclient wlan0
exit 0
```

...and no autostart I have to go by terminal to get the wireless to work

Regards

Martin

---

### Post by Chouca on 2006-12-14
Ciao,

the adventure continues...hmmmm

Status now: If  i Reboot the Wireless comes up OK   ;) 


but after Suspend or Hibernate I have to run 

```
sudo /etc/rc.local
```

...and the sun shines and everything is OK


...now the final challenge is to get it working after suspend (and  also Hibernate)

whas the difference and what catalogues do affect a script after Suspend or Hibernate


Regards

Martin

---

### Post by Chouca on 2006-12-15
Hi,

I am happy to be able to answer my own question


Make an executable file containing your script and place it in the /etc/acpi/resume.d folder

I have now placed


```
/etc/rc.local
```

in a file called WirelessWakeUp.sh located in the resume.d folder and it works fine!

Regards

Martin

---

