---
title: "Re: hybrid for ubuntu14.04(ATI/Intel)"
date: 2014-05-04
forum: General Help
---

### Post by nanite on 2014-05-04
(this post is a continuation along the lines of [http://ubuntuforums.org/showthread.php?t=2205627](http://ubuntuforums.org/showthread.php?t=2205627))

I am having this problem as well starting after my upgrade to Ubuntu 14.04. My hardware is an Acer TimelineX 5820TG laptop which has a Intel/Radeon 5650 combination.

In addition to being unable to turn off the discrete graphics through vgaswitcheroo, I am seeing a fake "second monitor" since X thinks the discrete card is another graphics card. In arandr this second monitor appears as LVDS-1-1. This is a bit annoying since I have an invisible extra desktop during the login screen and in my sessions, until I open arandr and turn it off.

So far I have been using the initramfs script hybrid_boot_options at [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics), along with the grub boot options. Now apparently these fail 

Output from cat /sys/kernel/debug/vgaswitcheroo/switch :
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynPwr:0000:01:00.0
2:DIS-Audio: :Pwr:0000:01:00.1
```

Output from  lspci | grep VGA :
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
```


[HR][/HR]

While writing this post, the discrete card switched itself off, but I am not sure how to reproduce it. What I see is:
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0
2:DIS-Audio: :Off:0000:01:00.1
```

I could re-power it (to DynPwer) by enabling the second display in arandr but after disabling the display again, it doesn't seem to go back... Hmm this will take some more investigation.

[HR][/HR]

**_SEMI-FIX_**. It is possible to restore the vgaswitcheroo to the old behaviour where the discrete card can be switched off manually. To do this, add radeon.runpm=0 in your kernel boot options. In other words if you have been using the initramfs fix on the Ubuntu wiki mentioned above, then in /etc/defaults/grub make:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=1 hybridopts=ON,IGD,OFF radeon.runpm=0"
```

and then run update-grub. After this I see the desired (previous) result of a completely disabled radeon card.
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0
2:DIS-Audio: :Off:0000:01:00.1
```

---

### Post by Elfy on 2014-05-04
I've moved this post out of the Utopic Unicorn area. You can edit the post here to point to the utopic discussion - but I've closed that thread now.

---

### Post by nanite on 2014-05-04
Thanks, I realized after posting that it might be in the wrong thread, so it's good you put it in the right place.

---

