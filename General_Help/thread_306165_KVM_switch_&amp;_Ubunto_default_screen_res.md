---
title: "KVM switch &amp; Ubunto default screen res"
date: 2006-11-24
forum: General Help
---

### Post by Indiana Red on 2006-11-24
Has anyone seen this kind of problem,
I have just added a KVM switch for Ubuntu and Server2k3
IOGEAR GCS62 KVM   and it works as advertiesed except:  Switching over to Ubuntu the display is set to 640x480 and navigating to the screen res options does not allow any other choices.
Strange.  This is on a decent 176" monitor that I know is capable.
800x600 I could probly work with but this is just too fat.
Any ideas or experience with this would be helpful.
Thanks.

---

### Post by CoolHand on 2006-11-24
I also have an IOGEAR KVM.  Not sure if it is the same model or not.  I have seen the same issue and worked on it to try to get past it for a long time. I have a laptop and tried to get it to work with my port replicator connected to a 21 inch monitor.  It worked before the KVM but not after. In the xorg.conf you can configure two different monitors to run at the same time one being the laptop screen and the other being the monitor.  After trying a lot of setups it seems that the KVM is blocking some part of the detection process and xorg can't figure out the capabilities of the monitor so it defaults to low res.  With mine I was able to get it to come up at a decent res if I booted to the laptop screen and then switched the KVM to display it but then I get some sort of pulsing on the screen.  I have not found the fix after trying a bunch of configs but I can recommend that you concentrate on the auto detection settings in xorg.conf and do some trial and error.  If you do get it to work I'd love to hear about it.

---

### Post by strawberry on 2006-12-05
I had similar trouble that Indiana wrote.
After added KVM switch, Ubuntu booted 640x480 res instead of the previously used 1024x768. There was no chance to modify the resolution at all. 
I searched the forum for solution and found this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
In my xorg.conf file at the "Monitor" section the HorizSync and VertRefresh lines were missing. I added proper refresh rates and restart gdm. After restart I had the desired old resolution.
I hope it'll help.

---

