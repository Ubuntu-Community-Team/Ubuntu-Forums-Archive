---
title: "Missing tun.ko module"
date: 2016-08-30
forum: General Help
---

### Post by bartosz3 on 2016-08-30
Hi,

I am trying to use openvpn, however tun0 interface is not created and I believe that missing tun.ko module is to blame.

Any idea where do get it?

I am using 16.04

---

### Post by #&amp;thj^% on 2016-08-30
Do you have "network-manger-openvpn-gnome " installed?
I just love guessing in trying to help.
BTW, tun is not a module to be loaded
And with the little information you provide for us I can just guess here: [http://superuser.com/questions/497245/how-to-load-tun-module-in-linux/519770#519770](http://superuser.com/questions/497245/how-to-load-tun-module-in-linux/519770#519770)

---

### Post by bartosz3 on 2016-09-02
Let's leave gui alone and assume I am running multiuser target on both client and server. 
Sorry but I am not following. When I start openvpn@client the tunnel interface is not created which is bad.
I've checked on centos machine on which it works and the tun module is present.
If I understand correctly on superuser the guy works this out by: insmod /lib/modules/3.6.9-1-ARCH/kernel/drivers/net/tun.ko.gz
The problem is I don't have tun.ko.gz on my system.

---

### Post by #&amp;thj^% on 2016-09-02
Dose this report anything
```
find /lib/modules/ -iname 'tun.ko.gz'
```
Mine Shows This
```
$ find /lib/modules/ -iname 'tun.ko.gz'
/lib/modules/4.7.2-1-ARCH/kernel/drivers/net/tun.ko.gz

```
Now I am beginning to see what you are asking about. The more  information you provide here, the better the reply's are....makes sense  right?:smile:
OpenVPN has a lot of case use's
Edit: I just remembered this as I have not used Ubuntu for OpenVpn for your use for a couple of years now.
The tun.ko is built-in the kernel on ubuntu and my work around was like this.
```
cd /dev
sudo MAKEDEV tun
sudo openvpn --mktun --dev tun0
```
Of course any attempt to use 
```
modprobe tun
```
Will not show any results... but a reboot now should let you see a tun0 now. (At least it did for me)

---

