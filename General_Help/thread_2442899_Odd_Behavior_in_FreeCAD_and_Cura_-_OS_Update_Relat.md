---
title: "Odd Behavior in FreeCAD and Cura - OS Update Related?"
date: 2020-05-08
forum: General Help
---

### Post by rebeltaz on 2020-05-08
I am running Ubuntu 18.04 LTS with Cura v3.2.0 (via AppImage) and FreeCAD v0.18.4. Up until today, everything has been running fine. Tonight, I went to edit a sketch in FreeCAD in a previously created model. Normally, when I click on the sketch, it opens immediately. Now, it is taking 20 to 30 seconds to open. During that timeframe, I can move the mouse, but nothing responds to it or any clicks - no other program nor any system function. If I do click something while the system is lagging, it will react to the click(s) after that 20 to 30 second delay. 

I though this might be a FreeCAD issue alone, but then I pulled up Cura and loaded a model into that. When I went to change the filament profile, the screen went white with relics of the Cura menu visible and again froze for 20 to 30 seconds just like FreeCAD. It also does that randomly regardless of the actions I'm trying to perform. 

I haven't installed or changed anything, but I am wondering if this might be related to a system update maybe? I mean, nothing else has changed to cause this. I am including a log of the update history. If there is anything that might be causing this, or if anyone has any ideas, I am all ears! I really need to get these programs working again...

---

### Post by rebeltaz on 2020-05-10
Last night, I ran another update/grade and it said it was installing a whole list of graphics and mesa drivers. I thought for sure that that would fix it, so I left it and went to bed. When I woke up, it showed the updates had been installed, but (after rebooting) the programs are still acting up. I tried the update/grade using dist. For some odd reason, it told me that it was installing (what looked to me) to be the exact same graphics and mesa drivers again. Again, after rebooting, nothing has changed in regards to my issue.


```

Start-Date: 2020-05-10  02:21:13
Commandline: apt upgrade
Requested-By: derek (1000)
Upgrade: libegl1-mesa-dev:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libegl-mesa0:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libglapi-mesa:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libglapi-mesa:i386 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libxatracker2:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libegl1-mesa:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), boot-sav:amd64 (4ppa105, 4ppa107), libgbm1:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), boot-sav-extra:amd64 (4ppa105, 4ppa107), libwayland-egl1-mesa:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libgles2-mesa-dev:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libgl1-mesa-dev:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libgl1-mesa-dri:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libgl1-mesa-dri:i386 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libosmesa6:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libosmesa6:i386 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libgl1-mesa-glx:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libgl1-mesa-glx:i386 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), mesa-vdpau-drivers:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), mesa-va-drivers:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libglx-mesa0:amd64 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), libglx-mesa0:i386 (20.2~git2005081930.ab5590~oibaf~b, 20.2~git2005091930.e622e0~oibaf~b), boot-repair:amd64 (4ppa105, 4ppa107)
End-Date: 2020-05-10  02:21:24

Start-Date: 2020-05-10  12:46:04
Commandline: apt dist-upgrade
Requested-By: derek (1000)
Upgrade: libegl1-mesa-dev:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libegl-mesa0:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libglapi-mesa:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libglapi-mesa:i386 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libxatracker2:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libegl1-mesa:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), boot-sav:amd64 (4ppa107, 4ppa109), libgbm1:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), boot-sav-extra:amd64 (4ppa107, 4ppa109), libwayland-egl1-mesa:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libgles2-mesa-dev:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libgl1-mesa-dev:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libgl1-mesa-dri:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libgl1-mesa-dri:i386 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libosmesa6:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libosmesa6:i386 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libgl1-mesa-glx:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libgl1-mesa-glx:i386 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), mesa-vdpau-drivers:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), mesa-va-drivers:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libglx-mesa0:amd64 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), libglx-mesa0:i386 (20.2~git2005091930.e622e0~oibaf~b, 20.2~git2005100730.a92a48~oibaf~b), boot-repair:amd64 (4ppa107, 4ppa109)
End-Date: 2020-05-10  12:46:15
```

---

### Post by rebeltaz on 2020-05-11
I figured out what the problem is/was. A long time ago, I had installed these alternative graphics drivers - [https://launchpad.net/~oibaf](https://launchpad.net/~oibaf) - in an effort to get the latest blender to install (it didn't work) and I never reverted back to the original drivers. Since they've been working all this time, I never gave them any thought. Once I disabled those and reverted back to the original set, everything is back to normal.

---

