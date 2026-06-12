---
title: "/etc/xdg/compiz/: No such file or directory"
date: 2008-05-06
forum: General Help
---

### Post by twistedtwig on 2008-05-06
Hi all,

I was following this link: [http://www.makeuseof.com/tag/check-if-compiz-will-run-well-on-your-linux-box-with-compiz-check/]("http://www.makeuseof.com/tag/check-if-compiz-will-run-well-on-your-linux-box-with-compiz-check/")

and this is the output I got when I ran the script:

```
jonh@UbuntuWiggly:~/Desktop$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 7.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...ls: /etc/xdg/compiz/: No such file or directory
           [WARN]

Something potential problematic has been detected with your setup:
 Warning: No path to Compiz found. 

Would you like to know more? (Y/n) y

 In case you did not compile Compiz manually, this will result in Compiz
 failing to run. The problem is presumably a result of you installing the
 proprietary fglrx driver manually or by script, which changed a certain
 config file to get itself on Compiz' whitelist
```

I can see that I do not have an /etc/xdg/compiz folder at all.  I have tried uninstalling all of the compiz packages with synaptic and reinstalling them but it is still the same.

Could anyone point me in the right direction please?

Am I going about this in all the wrong ways?

Thanks

---

### Post by Forlong on 2008-05-07
Please try again with the latest version (available [here]("http://forlong.blogage.de/article/pages/Compiz-Check")).
The xdg directory check is only meant for Gutsy and Hardy.

---

