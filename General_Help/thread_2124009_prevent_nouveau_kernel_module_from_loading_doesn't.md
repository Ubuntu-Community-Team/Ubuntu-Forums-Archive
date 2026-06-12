---
title: "prevent nouveau kernel module from loading doesn't work anymore"
date: 2013-03-09
forum: General Help
---

### Post by Helgefan on 2013-03-09
I have a Dell Inspiron Laptop with an NVidia 650M graphics card with Optimus technology. I followed the tutorial [http://eternalvoid.net/tutorials/linux-optimus-gt650m/](http://eternalvoid.net/tutorials/linux-optimus-gt650m/) to be able to selectively run programs with my power-consuming graphics card (bumblebee optirun with propriatary nvidia drivers).
It worked perfectly for some time but recently optirun didn't work anymore for unknown reason and said:

```

[ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[DEBUG]Socket closed.
[ERROR]Could not connect to bumblebee daemon - is it running?

```

So I tried to uninstall everything related and redo all the steps of the tutorial. There I noticed that blacklisting the nouveau kernel module in the file /etc/modprobe.d/blacklist.conf had no effect anymore and
lsmod | grep nouveau
still listed nouveau as loaded driver module.
Does anyone have an idea what might be going on here?

Thanks!

---

### Post by gwill83419 on 2014-01-17
Hi
I get exactly this too. (13.10, gtx770m)
I have tried modifying the config file in all the ways mentioned, no joy
I have tried: ttp://ppa.launchpad.net/xorg-edgers/ppa/ubuntu to get the latest nvidia drivers. - this told me that all was well, what a shame!
Ihave tried Ubuntu-x-swat/x-updates.
Bumblebee will not run. restarting bumblebee returns me 'Unknown instance.

Graham

---

