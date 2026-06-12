---
title: "I dont have plugin unity in compizconfig setting manager"
date: 2013-12-12
forum: General Help
---

### Post by ayebk123 on 2013-12-12
i need to turn on my plugin unity cuz all the panel and icons disappear so i run this compizconfig setting manager with this black screen (i dont know what you called it) cuz my terminal doesnt working so can anyone help to bring back or add my plugin unity???

thank you very much !

---

### Post by asus-user on 2013-12-12
> **ayebk123 said:**
> i need to turn on my plugin unity cuz all the panel and icons disappear so i run this compizconfig setting manager with this black screen (i dont know what you called it) cuz my terminal doesnt working so can anyone help to bring back or add my plugin unity???

thank you very much !

I suppose that you made some changes in Compizconfig setting manager so that you lost control over unity.
I suggest that you remove compizconfig setting manager and re-install unity and desktop to make sure everything went back the way it should.
to remove compizconfig setting manager use the following commands:
```

sudo apt-get remove compizconfig-settings-manager 
sudo apt-get remove compiz-plugins-extra 
sudo apt-get purge compiz*
``` 
to re-install unity and desktop and compizconfig again:
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install unity-2d
sudo apt-get install ubuntu-desktop
sudo apt-get install ubuntu-desktop-2d
sudo apt-get install compizconfig-settings-manager
sudo apt-get install compiz-plugins-extra
sudo apt-get install unity
```

Reboot and I hope it works :)
Report here any messages you get during the operation.

---

### Post by ayebk123 on 2013-12-13
YYYYYYYEEEEEEEEEAHHHHHH !

Oh man thanks you very much, it works !!!

realy appreciate that !

---

### Post by asus-user on 2013-12-13
> **ayebk123 said:**
> YYYYYYYEEEEEEEEEAHHHHHH !

Oh man thanks you very much, it works !!!

realy appreciate that !

Good to know :)

---

### Post by mörgæs on 2013-12-13
Please mark the thread 'solved'.

---

### Post by poitiers on 2013-12-15
And which version are you guys talking about? I'm in the process of using these instructions after having messed something up with compiz in 12.04, and I'm told that apt-get is "unable to locate package ubuntu-desktop-2d"...(?) Thanks.

---

### Post by deadflowr on 2013-12-15
> **poitiers said:**
> And which version are you guys talking about? I'm in the process of using these instructions after having messed something up with compiz in 12.04, and I'm told that apt-get is "unable to locate package ubuntu-desktop-2d"...(?) Thanks.

I've never seen that package exist, for any version.

If your missing the unity plugin, then simply reinstall unity(the package).

---

### Post by philinux on 2013-12-15
> **poitiers said:**
> And which version are you guys talking about? I'm in the process of using these instructions after having messed something up with compiz in 12.04, and I'm told that apt-get is "unable to locate package ubuntu-desktop-2d"...(?) Thanks.

In your case you may only need to reset unity and compiz.

[http://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/)

---

### Post by grahammechanical on 2013-12-15
> **poitiers said:**
> And which version are you guys talking about? I'm in the process of using these instructions after having messed something up with compiz in 12.04, and I'm told that apt-get is "unable to locate package ubuntu-desktop-2d"...(?) Thanks.

Unity 2D was a fallback mode in the original release of 12.04 for use on machines that did not have 3D acceleration. Unity 2D was left out of later versions of Ubuntu and it seems that it is not available in the latest images of 12.04, which is at version 12.04.3. The fallback mode is now a subset of the Nouveau video driver called llvmpipe. This is why the Unity 2D packages are not in the repositories.

By the way, to restore Unity we do not actually need to remove Compiz Configuration Settings Manager (CCSM). Early versions of CCSM allowed us to disable the Unity plugin but doing that broke the desktop. so, the latest version of CCSM do not allow us to disble the Unity plugin.

We can get in a similar mess if we remove ubuntu-desktop without installing a replacement desktop before hand.

Regards.

---

### Post by poitiers on 2013-12-15
Hi guys, thanks for the prompt responses. My problem has actually turned out to be minor: I must have magically reset the desktop properties and disabled moving and resizing windows, and managed to remove their frames, too. But, by a combination of asus-user's hints and clicking around inside compiz (disabling plugin ordering and checks also helped), I got it all running smoothly with nvidia drivers from 304 thru 319 to 331 now, which is such a relief after [3 nights lost on meddling with Saucy's setup]("http://ubuntuforums.org/showthread.php?t=2193643") (and giving up in despair).

---

### Post by mc4man on 2013-12-15
> **grahammechanical said:**
> Unity 2D was a fallback mode in the original release of 12.04 for use on machines that did not have 3D acceleration. Unity 2D was left out of later versions of Ubuntu and it seems that it is not available in the latest images of 12.04, which is at version 12.04.3. The fallback mode is now a subset of the Nouveau video driver called llvmpipe. This is why the Unity 2D packages are not in the repositories.

By the way, to restore Unity we do not actually need to remove Compiz Configuration Settings Manager (CCSM). Early versions of CCSM allowed us to disable the Unity plugin but doing that broke the desktop. so, the latest version of CCSM do not allow us to disble the Unity plugin.

We can get in a similar mess if we remove ubuntu-desktop without installing a replacement desktop before hand.

Regards.

OT - 
it's usually better to ck. stuff out first
unity-2d is in 12.04.3, ck. the manifest if you don't have an install
users can disable the unity plugin, nothing to prevent that & for certain actions can be useful
ubuntu-desktop is just a meta package & causes no issue if removed except under very limited circumstances & additionally  should be (re)installed if one is doing an upgrade to new Ubuntu release

---

