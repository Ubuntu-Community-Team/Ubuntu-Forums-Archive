---
title: "Ubuntu 8.04 on MSI board and Intel Duo Core"
date: 2008-06-15
forum: General Help
---

### Post by richardmems on 2008-06-15
hi all

i installed ubuntu on newly assemblied PC with MSI P4M900M3 board with 2.0 GHz intel duo core, sata harddisk and 1 Gb RAM from the CD obtained directly from Ubuntu.

Installation is ok, but when GUI environment came in, the graphic is severely distorted with dual images vertically.

It seems all other features are working, including star office and x-termainal.. only graphic is coming badly 

Is there any way to fix the error? Or anyone of the forum has this kind of problem before?

Please kindly advise.

regards
Richard

---

### Post by Lord Xeb on 2008-06-15
What graphics card are you using. If it is Intel integrated graphics, then that may explain your problems. Post what model the ITTG is and we'll see what we can do...

If problems persist and nothing we suggest works, just go out and get a cheap Nvidia card (like a GeForce 7300 or something. Even a Geforce ^ series will work). That should fix your problems... I think.

---

### Post by richardmems on 2008-06-15
Thanks for your reply.

i am using the integrated on board graphics.

[http://www.msicomputer.com/product/p_spec.asp?model=P4M900M3-L](http://www.msicomputer.com/product/p_spec.asp?model=P4M900M3-L)

is the link to detailed specification of the board.

DO i need to get a VGA card?

Thanks again

Richard

---

### Post by cariboo on 2008-06-15
There is a linux driver for your graphics chip set located  in the repositories. If it isn't installed. you can restart your computer in recovery mode. This will startup in a console and to install the dirver from there. at the prompt type:

```
sudo apt-get install xserver-xorg-video-unichrome
```

Hit enter and it should install. After it is finished type:

```
shutdown -r now
```

This will restart your computer.

---

### Post by richardmems on 2008-06-15
Thanks for your reply

the error

"couldn't find the package xserver-xorg-video-unichrome"

appear in the console.
Can i download it from somewhere? or it exist with other name like Xorg etc...
regards
richard

---

### Post by richardmems on 2008-06-15
for graphics card like GeForce 7300. will Ubuntu automically install driver at startup ? or i need to reinstall the whole OS?

Please let me know which graphic card work well with ubuntu 8.04?

regards
richard

---

