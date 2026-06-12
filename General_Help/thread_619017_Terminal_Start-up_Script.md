---
title: "Terminal Start-up Script"
date: 2007-11-21
forum: General Help
---

### Post by deputydon on 2007-11-21
My problem is that my wireless drivers are screwy on Gutsy, they worked fine after some small tweaks on Feisty, but Gutsy I have to put in commands in the terminal every time I turn on my laptop. I was wondering if someone could make/show me a script so that it will put the commands in automatically every time I boot up the computer. 

Commands I need:

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="zarkoff" authtype="sharedkey"
sudo sleep 2
sudo dhclient wlan0

Thanks in advance for the help.

---

### Post by banewman on 2007-11-21
Haven't been able to try this but from your lines this should work-
```
#!/bin/sh
echo "$(sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable)"
echo "$(sudo wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true)"
echo "$(sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true)"
echo "$(sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0)"
echo "$(sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="zarkoff" authtype="sharedkey")"
echo "$(sudo sleep 2)"
echo "$(sudo dhclient wlan0)"
```
Then make it executable and add it to startup - feel free to ask more questions. :)

---

### Post by bingoUV on 2007-11-21
remove sudo from all these commands, and put them in /etc/rc.local file. It runs as root anyway, whenever you startup the system, after all other startup initialization has been done.

---

### Post by deputydon on 2007-11-22
> **banewman said:**
> Haven't been able to try this but from your lines this should work-
```
#!/bin/sh
echo "$(sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable)"
echo "$(sudo wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true)"
echo "$(sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true)"
echo "$(sudo wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0)"
echo "$(sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="zarkoff" authtype="sharedkey")"
echo "$(sudo sleep 2)"
echo "$(sudo dhclient wlan0)"
```
Then make it executable and add it to startup - feel free to ask more questions. :)

How, exactly (noob question) do I turn it into a executable?  Sorry I'm not good with Linux at all haha.  What program do you recommend I use for this?  Does open office work?  Or am I suppose to use something like gedit?


PS.  Also, since i'm here, is there any way to make the boot up quicker?  It might just be because this isn't the best laptop, but when I hit the power button it can take up to ten minutes just to get to the login screen.

---

### Post by nick_h on 2007-11-22
> How, exactly (noob question) do I turn it into a executable?
To make a file executable type the following:
```
sudo chmod a+x filename
```

---

### Post by deputydon on 2007-11-22
> **nick_h said:**
> To make a file executable type the following:
```
sudo chmod a+x filename
```

Maybe i'm doing it wrong, but that did nothing for me.  Didn't give me an error message or anything.

---

### Post by nick_h on 2007-11-22
Check the permissions by typing:
```
ls -l filename
```

---

### Post by tskoog on 2007-11-22
I found this post looking for similar help with the rc.local file...I checked mine before and after trying the[FONT="Lucida Console"] sudo chmod a+x rc.local [/FONT]command and both show the same permissions... hope that helps...

[FONT="Lucida Console"]user@Ubuntu:/etc$ ls -l rc.local
-rwxr-xr-x 1 root root 339 2007-11-22 14:46 rc.local
user@Ubuntu:/etc$[/FONT]

---

