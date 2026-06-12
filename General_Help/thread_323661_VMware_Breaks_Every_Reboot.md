---
title: "VMware Breaks Every Reboot"
date: 2006-12-22
forum: General Help
---

### Post by hxx4 on 2006-12-22
Everytime I reboot my computer, VMware server breaks. I have the latest version installed on Edgy. When I type the command```
vmware
```I get the error```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```so I enter the command```
sudo /usr/bin/vmware-config.pl
```and accept the defaults for everything and it works again. But then I have to do the same thing all over again next time I reboot. Any help is appreciated. I have tried running the original install script again and no luck.

---

### Post by hanzomon4 on 2006-12-22
I had a similar issue and fixed it, but I forgot how...... Let me take a moment to jog my memory............

---

### Post by riven0 on 2006-12-22
[This is what]("http://www.vmware.com/community/thread.jspa?messageID=65376&#65376") worked for me.

---

### Post by hanzomon4 on 2006-12-22
I found a few solutions....

1:> **mhancoc7 said:**
> I just finished installing VMware Server to a fresh install of Ubuntu CE v2.0 (Edgy). I was having the same trouble that you have mentioned. 

Here is how I fixed it.

I opened /etc/init.d/ and found 2 vmware files.

vmware
vmware-player
vmware.old.0

I had assumed that these files would not be there since I had done a complete removal of vmware-player before installing vmware-server.

I deleted vmware-player, vmware.old.0. 

I also made sure to delete the /etc/vmware/not_configured file.

Then I rebooted and all works perfect!

I hope that helps someone.

Jereme

2:> **mpo said:**
> @ Jereme: 

It did help for me too, thx for sharing.

Small nuance though, I settled with removing the links from /etc/rc?.d/???vmware* to the mentioned /etc/init.d/vmware-player rather then removing the script.
  ```
$ sudo rm /etc/rc?.d/???vmware-player
```

In any case I found unlinking/removing the extra init-d script less intrusive then editing the script by hand.



@ others with less luck then jereme and me:

I've found this other solution as well that somehow starts from further investigation of the issue:
[http://www.vmware.com/community/message.jspa?messageID=506502]("http://www.vmware.com/community/message.jspa?messageID=506502")

Try those two out and let us know if it worked..... Here's the [link]("http://ubuntuforums.org/showthread.php?t=288018&page=2") to the thread I found these in

---

### Post by hxx4 on 2006-12-22
Thanks for the replies everyone. I tried doing a ```
sudo rm /etc/init.d/vmware-player
``` and this worked perfectly. I rebooted twice so far and vmware server is still working. I guess the problem was a conflict between vmware server and vmware player (which I had not uninstalled before I installed vmware server). Thanks!

---

