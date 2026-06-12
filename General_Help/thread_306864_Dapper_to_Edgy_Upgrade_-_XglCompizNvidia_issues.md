---
title: "Dapper to Edgy Upgrade - Xgl/Compiz/Nvidia issues?"
date: 2006-11-25
forum: General Help
---

### Post by JohnPhys on 2006-11-25
Hey all,

I'm definitely thinking about upgrading to edgy, but I've read some stuff about issues with having xgl/compiz installed, and I'm wondering how to get around it.

I do *not* (to my knowledge) have "quinn's repositories" in my sources.list.  I followed the how-to here

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

to enable xgl/compiz.

There were a few bugs in it for me (couldn't use mythtv, alt+tab wouldn't scroll through minimized windows), so I put everything back the way it was (no longer load "thefuture", replaced gconf.custom with a blank one, commented out the "EnableGLXwithCompisite" or whatever in my xorg.conf), but I did not uninstall any of the packages that I grabbed to get xgl/compiz up and running.

Is there anything that I obviously need to do before attempting an edgy upgrade?

Thanks!

---

### Post by JohnPhys on 2006-11-25
Bump!

Anyone?  Your help would be greatly appreciated.

---

### Post by reclusivemonkey on 2006-11-26
> **JohnPhys said:**
> Bump!

Anyone?  Your help would be greatly appreciated.

You don't mention what video card you have; if you have a Nvidia card it should be fairly straightforward. I did a reinstall and a clean install on two seperate machines this weekend, and it was *fairly* simple. I did try compiz/XGL on Dapper and it wasn't quite ready for me personally. I have no such qualms on Edgy, it works superb. All I did was follow the instructions here;

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

Now I can't say how it will work with mythtv as my mthtv box is a seperate machine running Slackware 10.2. All you need to do to run beryl on edgy is run beryl-manager from your sessions preferences, so its easy to turn it off if it isn't working for you. I heard of a few people having problems upgrading from Dapper to Edgy. Personally, ever since I started with Linux I keep a /home partition, and retain this every time I upgrade, and just do clean installs, not formatting that partition.

---

### Post by JohnPhys on 2006-11-26
Thanks for the reply, I guess I wasn't clear on what I was asking, though.

I'm just wondering if there's anything I need to do to avoid obvious conflicts/issues with upgrading dapper to edgy, and I'm not intending to enable xgl/compiz/beryl/etc.  I had it enabled before, but am not currently using it.  I had read that some people need to downgrade certain packages before upgrading to edgy, otherwise the installer isn't happy (version conflicts, I think).  This seemed to be with people that used another method of installation, and I was wondering if there were any known issues with the packages I would have installed following that howto.

I have an nVidia 6800 GT (NV40).

Thanks for the reply though, all information is appreciated!

---

