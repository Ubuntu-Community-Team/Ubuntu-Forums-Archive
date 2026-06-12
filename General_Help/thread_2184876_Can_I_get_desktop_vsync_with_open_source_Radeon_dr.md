---
title: "Can I get desktop vsync with open source Radeon driver and no xorg.conf?"
date: 2013-10-30
forum: General Help
---

### Post by UnrealMiniMe on 2013-10-30
I'm currently using the open source Radeon driver with the Mate desktop, and the desktop tearing is driving me crazy.  According to [this page]("http://xorg.freedesktop.org/wiki/RadeonFeature/#index2h2"), enabling either or both of the following two options in xorg.conf might help (whereas the EVAXVync is unnecessary with KMS enabled...which it is):
[LIST][*]EnablePageFlip
[*]SwapBuffersWait[/LIST]
Unfortunately, I no longer have an xorg.conf at all; everything is autoconfigured.  Is there a way to get vsync and fix (or at least reduce) tearing without one, or is it necessary to create one?  (I'm hoping it's not necessary.  I tried configuring Xorg to create an xorg.conf, and I got stuck on the same issue someone else talked about [here]("http://askubuntu.com/questions/169725/xorg-number-of-created-screens-does-not-match-number-of-detected-devices").)

I'm sorry if this is a duplicate thread: I've seen a lot of Vsync threads on this forum, but it's hard to find one that's specifically about the open source Radeon driver (which has no Catalyst Control Center of course), especially a recent one that takes xorg autoconfiguration into account.  As a side note, I tried driconf, and it didn't include any relevant options.

---

### Post by deadflowr on 2013-10-31
Have you tried simply generating an xorg.conf file?
And then adding the parts you need set.
[http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file](http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file)
Slightly old, and not sure what displaymanager you have running, but the way to get it is the same.

---

### Post by Yellow Pasque on 2013-10-31
PageFlip and EXAVsync may help, but swapbufferswait pertains to 3D and is irrelevant for MATE. Also, MATE/metacity used to have an option to enable compositing:
```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```

Skeleton xorg.conf:
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

