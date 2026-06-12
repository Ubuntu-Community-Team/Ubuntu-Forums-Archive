---
title: "Keyboard issue: crash on type and no mod keys"
date: 2008-05-23
forum: General Help
---

### Post by decoherence on 2008-05-23
The behavior I'm observing is that modifier keys will stop working on running applications. No shift, no Alt F4, no Ctrl Alt F1 (which really sucks.) New applications I open run fine until I try to input some text, then they segfault.

I'm running VMWare Server and nVidia. Aside from that, everything is stock, fresh Hardy (not dist-upgraded from gutsy.) The problem appears to start after using my virtualized XP machine. It should be noted that the virtual guest does not experience any of these problems. Mod keys always work in the guest, so this is not a hardware issue (i also kvm in to three other machines with no problem)

I haven't really done much more looking in to it as I'm at work and I need to, well, work (in virtualized windows no less! yech!)

At this point I'm just wondering if anybody else is seeing this?

---

### Post by decoherence on 2008-05-23
Just rebooted. I'm going to try to reproduce the issue now. With my typical suite of apps running (evolution, terminal, firefox, pidgin) everything is humming along fine. Mod keys work, no crashing when I try and type.

It should be noted that VMWare Server and my virtual machine are already running, even though I haven't run the VMWare Server Console. The virtual machine is configured to boot automatically once the host is up.

I'm running xev in the terminal. Now I'll run VMWare Server.

I've switched over to XP and I'm still able to use mod keys (as my Capitals show.)

the next thing i do is run groupwise.... the one and only reason i still use windows... hey lookit that1 my capitals are gone1 and i can't make exclaimations anymore1

sure enough, alt f4 is broken.

xev in the terminal appeared to die... it no longer responds to key presses at all. however if i open up another terminal and run xev, it responds to all key presses. here's ctrl... one of the keys currently not working

KeyPress event, serial 31, synthetic NO, window 0x3e00001,
    root 0x1a6, subw 0x0, time 2135824, (-139,-193), root:(644,404),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3e00001,
    root 0x1a6, subw 0x0, time 2135944, (-139,-193), root:(644,404),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


okay, well this is sorta like troubleshooting an extensions conflict in system 7. i just have to do this 20 more times with 20 variations and i might get an idea. unless anyone else has one/
cheers,

---

### Post by decoherence on 2008-05-30
It seems to be fine as long as I don't go in to fullscreen.

That's what I get for using proprietary software!

---

### Post by dreaminhere on 2008-08-28
I've got the same problem.  the only way I can get things to work again in ubuntu is to reboot.  I'm a power windows user but a new linux user, so I'm useless as far as troubleshooting or coming up with fixes.  Is there any way to get the keys to work without rebooting?  Any way to fix this?

---

### Post by dreaminhere on 2008-08-28
after googling, I found this is an old problem. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982).  Supposedly, if hardy has the focus when you go to full screen or you push the full screen button, it doesn't happen.  If it does happen and you can type setxkbmap in the terminal, it makes your keys work again for linux.

---

### Post by drzjan on 2008-09-02
ok im having problems wit the shift alt control keys n i cant i mean i dont know how to get them to work any1 can help please and setxkbmap its not working for me

---

### Post by drzjan on 2008-09-02
> **drzjan said:**
> ok im having problems wit the shift alt control keys n i cant i mean i dont know how to get them to work any1 can help please and setxkbmap its not working for me
ok im having problems wit the shift alt control keys n i cant i mean i dont know how to get them to work any1 can help please and setxkbmap its not working for me

---

