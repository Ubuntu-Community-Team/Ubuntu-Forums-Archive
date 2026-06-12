---
title: "How to Remove Automatix?"
date: 2007-12-01
forum: General Help
---

### Post by teejay17 on 2007-12-01
Anyone know how to remove Automatix using the terminal? (because this was the way it was installed?)
I accidentally installed version 7.10 on 7.04.

---

### Post by PriceChild on 2007-12-01
I would suggest a reinstall of Ubuntu.

---

### Post by -grubby on 2007-12-01
```
sudo apt-get remove automatix2
``` or

```
sudo apt-get remove automatix
``` 


I can't remember which, but if you choose the wrong one it won't hurt anything and in that case then just run the other command

---

### Post by fjgaude on 2007-12-01
After that, if you can use Synaptic Package Manager, go to it and then click on Status. From there click on Not installed (residual config) and uninstall anything to do with Automatix. That should do it.

---

### Post by teejay17 on 2007-12-01
> **fjgaude said:**
> After that, if you can use Synaptic Package Manager, go to it and then click on Status. From there click on Not installed (residual config) and uninstall anything to do with Automatix. That should do it.
Thanks.

---

### Post by bodhi.zazen on 2007-12-19
Automatix is a third party project and, at this time, is not supported on the ubuntu forums. For additional information see the following links :

	[Technical review of Ax](http://mjg59.livejournal.com/77440.html)

	To my knowledge the maintainers of Ax are working to address these issues, but they remain unresolved at this time. You might check the Ax forums for an update. When and if this occurs the situation will be re-evaluated and subject to change.

	[Official Forums Policy](http://ubuntuforums.org/announcement.php?f=13/)

	[Supported Installation Alternatives to Automatix](http://ubuntuforums.org/showthread.php?t=519872)

	[Automatix forums](http://www.getautomatix.com/forum/index.php?act=idx)

	If you want to discuss Ax, feel free to post here : 

	[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

