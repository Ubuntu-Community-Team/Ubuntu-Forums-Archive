---
title: "kubuntu update broken"
date: 2015-06-18
forum: General Help
---

### Post by gert5 on 2015-06-18
Hello All,

Today I chose to fire up the update tool. It came up with its list of updates for application and OS items.
I clicked OK. two odd things happened.

[LIST=1]
[*]A popup asking me about additional changes giving a list of items in a popup window.
I have no idea what is expected from me here. Could the forum expert please explain?
[http://drgert.dyndns.ws:8000/download/kubuntu_update_popup.jpg](http://drgert.dyndns.ws:8000/download/kubuntu_update_popup.jpg)
[*]I clicked OK and let it run. After a while a new popup showed up saying that the update is broken. Now what?
[http://drgert.dyndns.ws:8000/download/kubuntu_update_broken.jpg](http://drgert.dyndns.ws:8000/download/kubuntu_update_broken.jpg)
[/LIST]

Thanks,
Gert

---

### Post by wildmanne39 on 2015-06-18
Hi, please use thumbnails or url's when posting images because many people have slow connections or a limit on bandwidth.
Thanks

---

### Post by gert5 on 2015-06-19
@WildMan. No problem. Apologies for the inconvenience. Gert.

---

### Post by wildmanne39 on 2015-06-19
No problem that is how we learn this crazy thing.:)

---

### Post by oldos2er on 2015-06-19
To fix your broken packages, try ```
sudo apt-get install -f
``` If it fails for some reason, please copy and paste all the output here.

---

### Post by gert5 on 2015-09-26
Hi All,

Thanks.


What is the smart cmd sequence for the dumb user to run every other weekend to keep the system reasonably up to date?
I tried the below. Is that OK?

 apt-get install -f
 apt-get update
 apt-get upgrade
 apt-get dist-upgrade

Cheers,
Gert

---

### Post by oldos2er on 2015-09-27
```
sudo apt-get update; sudo apt-get dist-upgrade
``` will do it. You don't need to use *sudo apt-get install -f* unless there's a problem.

---

