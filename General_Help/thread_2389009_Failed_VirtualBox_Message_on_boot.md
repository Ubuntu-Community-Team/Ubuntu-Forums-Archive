---
title: "Failed VirtualBox Message on boot"
date: 2018-04-10
forum: General Help
---

### Post by simon114 on 2018-04-10
```
failed to start VirtualBox Linux kernel module see systemctl status vboxdrv.service for details
```

This is a FAILED error message when booting into Ubuntu 16.04

I removed virtualbox some time ago and am only now getting round to resolving this issue.

I have run
 ```
sudo dpkg -P virtualbox-qt
Sudo dpkg -P virtualbox
```

And in both cases get this message 

```
dpkg: warning: ignoring request to remove virtualbox which isn't installed
```

So I can only assume that this error is the what remains of a virtualbox install, How to I remove or disable this service.

Thanks

---

### Post by cruzer001 on 2018-04-10
> So I can only assume that this error is the what remains of a virtualbox install, How to I remove or disable this service.
Do a search on "virtualbox" and remove the leftovers (its ok to leave the .png's).

---

### Post by simon114 on 2018-04-10
SOLVED the problem with

```
[COLOR=#111111][FONT=Consolas]sudo apt-get remove virtualbox* --purge[/FONT][/COLOR]
```

No Failed messages anymore

 Thanks for the tip

---

