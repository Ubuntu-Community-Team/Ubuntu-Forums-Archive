---
title: "Upgraded to Gutsy.  Now I have a few problems"
date: 2007-12-02
forum: General Help
---

### Post by Jordan777 on 2007-12-02
I tried/did (dunno really) to update to Gutsy last night.  It went successful and then crashed when installing part of the upgrade.  It just stopped upgrading and went back to my normal desktop so I shut down my system.  I come back later today and turn it on to find my boot up menu now says that I'm running Gutsy.  Cool.  I start it up with a weird problem in the beginning.  It went to the black screen with text which I thought meant it was going to crash since it was saying there was a problem.  (sorry i didn't get the name of these 'problems' they move by pretty fast)  It didn't crash and instead has booted to my normal desktop.  I think the only real problem now is that my graphics driver hasn't been updated.  I tried through the restricted drivers manager, envy, and manually and all three have failed me.  Also I believe my system is running noticeably slower.  Maybe it's just my graphics card though.  Basically I want to know if I upgraded successfully and if not how to remedy the problem.  Also how can I install my graphics driver?  It's an nvidia 8800 gts.  This is the error message I get from the res. drivers manager.

-E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb: subprocess pre-installation script returned error exit status 2

I looked at the envy error in the var/log files and apparently envy is not supported by gutsy so that solves that problem I think.

Any help is greatly appreciated.

---

### Post by Jordan777 on 2007-12-02
Also I tried restarting again and the same black screen with text stating something about having no visual driver or something like that comes up.  I can't remember exactly what it says but it's along those lines.

---

### Post by zvacet on 2007-12-03
boot in recovery mode and type

```
dpkg-reconfigure xserver-xorg
```

select **vesa** driver.Thar will give you graphic and after that read [this]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Jordan777 on 2007-12-03
Well I am on the desktop but I can't seem to upgrade to the newest graphics driver.  I'm just wondering if all of the updates went through and how can I upgrade to the restricted drivers?  

The link isn't working so i can't read what it was going to tell me.

---

### Post by zvacet on 2007-12-04
Is [this](https://help.ubuntu.com/community/BinaryDriverHowto) O.K?

---

