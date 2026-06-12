---
title: "nvidia driver won't load after kernel upgrade"
date: 2008-02-05
forum: General Help
---

### Post by ireneshusband on 2008-02-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/189163](https://bugs.launchpad.net/ubuntu/+bug/189163) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The latest automatic security upgrade to my kernel (2.6.22-14 - end of january 2008 ), as well as doing the usual trick of configuring grub to boot from the swap partition, has left the nvidia driver unloadable. I have had to switch to the nv driver to get X working. :mad:

One thing I discovered was that some of the newly upgraded packages, namely the kernels (I have both generic and rt installed) had not been configured correctly and I had to run whatever it is you do with dpkg to put this right. However this made no difference. The module still doesn't work.

Anyone else know what's going on here?

Thanks.

---

### Post by FuturePilot on 2008-02-05
How did you install the driver? Manually? Restricted Driver Manager? Envy?

---

### Post by Cannaregio on 2008-02-06
Dunnow if this you have is driver related at all, anyway, give it a try.
It worked for me when the nvidia settings got garbaged by an automated update (why oh why do we continuously update instead of leaving our GNU/Linux systems run for ever in peace?).

If you have to reinstall the drives, _[COLOR="Blue"]you have to silence gdm[/COLOR]_
So 
1) fetch the last nvidia drivers
2) change gdm to -say- [COLOR="Blue"]gdmold,[/COLOR] so that it does not start
3) sh NVIDIA... (install the new drivers)
4) ```
sudo dpkg-reconfigure xserver-xorg
```
5) startx

voilà.

---

### Post by katepaulk on 2008-02-06
My husband had this problem - he has one of the later nvidia cards on 64 bit.

He solved it by re-running Envy, and got his video reconfigured properly once Envy had finished its magic.

If you haven't got Envy, information is at [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

The problem with this is that once you start using Envy you'll need to re-run it after each kernel update to get your graphics settings back.

I hope that helps.

Kate

---

