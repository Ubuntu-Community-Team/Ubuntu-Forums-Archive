---
title: "Desktop effects could no be enabled"
date: 2008-05-20
forum: General Help
---

### Post by LOLands on 2008-05-20
Hi again!

So here my new problem. I installed Ubuntu 8.04 (from Wubi). When I try to enable visual effects, it just writes: "Desktop effects could not be enabled" :( I have an laptop with ATI VGA...

compiz says:
> Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 


So what should I do? Like I sad I have a clean install :)

Thanks...

---

### Post by mavsman4457 on 2008-05-20
I am also having this problem.  I just upgraded from 7.10 and I used to have advanced desktop effects working but now I just get this message.  Also, I can't access the internet for some unknown reason.  Any help would be good.

---

### Post by 00arthuryu on 2008-05-20
please give the details of your graphics card, how you installed your graphics and the output of
```

gedit /etc/X11/xorg.conf

```
Also how did try to enable compiz?

---

### Post by Exsecrabilus on 2008-05-20
Try going **System** >> **Administration** >> **Hardware Drivers**.

See if it detected your graphics card and check the box next to it, enabling it.

It will download the appropriate driver to enable it, and since Ubuntu 8.04 has desktop effects enabled by default, when you restart your computer, effects will be enabled.

---

### Post by mavsman4457 on 2008-05-20
When I did that, it didn't show anything.  Before I updated to Hardy Heron it showed my graphics card and worked.

---

### Post by jp734 on 2008-05-20
try this. it worked for me.

echo SKIP_CHECKS="yes" >> ~/.config/compiz/compiz-manager

---

