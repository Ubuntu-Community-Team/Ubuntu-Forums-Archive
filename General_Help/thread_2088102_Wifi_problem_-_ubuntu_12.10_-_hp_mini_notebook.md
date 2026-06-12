---
title: "Wifi problem - ubuntu 12.10 - hp mini notebook"
date: 2012-11-25
forum: General Help
---

### Post by amantu on 2012-11-25
Hello, 

I am running ubuntu 12.10 on a hp mini notebook with Intel Atom CPU. I have problem connecting to wifi. 

I tried these codes and still no success. 

```
sudo sudo rfkill unblock wifi

sudo rfkill unblock all
[CODE]

and when I check with this command, sudo rfkill list all
[CODE]0: hci0: Bluetooth
          Soft blocked: no
          Hard blocked: no
1: hp_wifi: Wireless LAN
          Soft blocked: no
          Hard blocked: no
2: hp-bluetooth: Bluetooth
          Soft blocked: no
          Hard blocked: no
```I managed to fix the same problem on a dell vostro 1520 laptop by using below  commands following by rfkill commands: 

```
lsmode | grep dell

sudo rmmod -f dell_laptop
```I don't know what to do on this hp mini notebook.
can someone help me with this please!! 

Thanks

---

### Post by Abhinav Kumar on 2012-11-25
Hi amantu,
Have you tried installing drivers on your system?
May be you don't have proper wifi drivers on your system.

:)
Regards,
Abhinav

---

### Post by wildmanne39 on 2012-11-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by amantu on 2012-11-26
Thanks guys for your response. 

You are right Abhinav. The driver or its update was needed. 
Thanks Wild Man! Your link is useful. I save it in my notes to be able to use it in case of necessity. 

I managed to solve the problem with following code which I found in this link: [http://askubuntu.com/questions/204608/problem-with-network-in-ubuntu-12-10](http://askubuntu.com/questions/204608/problem-with-network-in-ubuntu-12-10)

here is the code: 
```
sudo apt-get update; sudo apt-get install bcmwl-kernel-source
``` 

Thanks again guys for your considerations. :) 
Cheers!

---

### Post by incendiary on 2013-02-27
Hi there.

I'm having trouble with my HP Mini having just switched modem from an older Netcomm router / modem after power supply failed.

Old router - NetComm NB9WMAXX

New Router - Netcomm NB16VW

I've configured everything the same on the new router and all devices connect to wifi with no issues (Win7 laptop, iphone, ipod, other Ubuntu PC).

Note the other Ubuntu PC is 12.04 and has an external USB wifi dongle.

However, my HP Mini 210 1100 will not connect although obviously had no issues with the previous modem / router.

It can see all networks OK and when I try to connect to mine, I am prompted for a passkey. However it seems to attempt connection several times before timing out and dropping the connection.

I ran the shell script provided by Wild Man above on each Ubuntu machine and have published each on Ubuntu One:

Working PC:
[http://ubuntuone.com/6zrjqJNi67uHfOyDUtSZGh](http://ubuntuone.com/6zrjqJNi67uHfOyDUtSZGh)

Not working HP Mini:
[http://ubuntuone.com/7WQPY1SS4Uymxbu3QjgHKf](http://ubuntuone.com/7WQPY1SS4Uymxbu3QjgHKf)


...and I've tried updating drivers etc as well as per the recommendations above.

I'm finding it hard to understand why changing routers would cause this? The key difference is that the new router provides B/G/N mixed wireless mode and is also IPv6 capable.

Router logs are showing these entries regularly and seem to coincide with the connection failures:

wide-dhcp6c[9159]: dhcp6_ctl_authinit: failed to open /root/2012_FW/CID561NC/Formal_FW/R0.09a0/rootfs/src/open_src/OWide//etc/dhcp6cctlkey: No such file or directory

Possibly an issue with IPv6 compatibility? I'm assuming DHCP6 is related to IPv6?

Finally... I'm using the Broadcom STA proprietary driver:

" This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware."

Help would be enormously appreciated!

---

### Post by incendiary on 2013-02-27
MANY APOLOGIES!!

Correction to my post - this buffoon had the network logs the wrong way round...

Should be:

Not working HP Mini:
[http://ubuntuone.com/6zrjqJNi67uHfOyDUtSZGh](http://ubuntuone.com/6zrjqJNi67uHfOyDUtSZGh)

Working PC:
[http://ubuntuone.com/7WQPY1SS4Uymxbu3QjgHKf](http://ubuntuone.com/7WQPY1SS4Uymxbu3QjgHKf)

Sorry for the confusion...

---

