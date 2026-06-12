---
title: "How do I &quot;blacklist&quot;"
date: 2008-05-16
forum: General Help
---

### Post by haran_hockey on 2008-05-16
I am trying to setup my wireless internet and one of the instructions was to blacklist something. I am using ubuntu 8.04.

Once installed, you have to blacklist the open source bcm43xx that comes with Ubuntu. The file /etc/modprobe.d/blacklist contains the blacklisting information. Just open it in gedit with root rights.

gksudo gedit /etc/modprobe.d/blacklist

And add to it...

blacklist bcm43xx

I opened up the file so what exactly do i add and where do i add it.

---

### Post by amingv on 2008-05-16
This is how I usually do it:
```
sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.backup
gksudo gedit /etc/modprobe.d/blacklist
```

Go to the very bottom of the file, add a brief description of why it was blacklisted and in favour of what:
```
#Drivers blacklisted by default are up here^^^
#####################################################

#Blacklisted in favour of ndiswrapper by <user>, acx presents problems with WPA
blacklist acx
```

---

### Post by strabes on 2008-05-16
You can just add it to the very end of the file. The following command will do this for you.```
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
```

To verify that it worked, run:```
cat /etc/modprobe.d/blacklist
```

Note that this simply prevents the module from being loaded upon boot, so you'll have to reboot.

---

### Post by haran_hockey on 2008-05-21
Thanks. Wireless still doesn't work for some reason :S

---

### Post by strabes on 2008-05-21
> **haran_hockey said:**
> Thanks. Wireless still doesn't work for some reason :S

That's because it's a broadcom wireless card. Broadcom stubbornly refuses to provide proper drivers for linux. The best way to overcome this is to simply never purchase another Broadcom product again and encourage others to do the same. Selling hardware without proper drivers is laughable and any company that does so will never receive a dime of my money.

---

### Post by haran_hockey on 2008-05-21
lol- thanks

---

