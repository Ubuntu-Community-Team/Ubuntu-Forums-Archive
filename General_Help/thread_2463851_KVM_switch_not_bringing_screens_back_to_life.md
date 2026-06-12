---
title: "KVM switch not bringing screens back to life"
date: 2021-06-19
forum: General Help
---

### Post by Ofloo on 2021-06-19
I have some issues when switching with my KVM switch.

When I switch to an other computer and the screens go to sleep, then when I come back to Xubuntu I can't bring back the screens with just a mouse click or keyboard stroke. I'm required to <crtl> + <alt> + <F1> then go back to <ctrl> + <alt> + <F2>. When logging on for a while now before I can make use of the keyboard, .. I'm required to click the desktop picture. Then and only then I'm able to use the keyboard. However on the login screen I can input my password just fine?

KVM switch is single port 8k DP 1.4 with 3 screens MST. The video card is only DP1.2 NVIDIA GTX 760. When everything is active everything works fine.

The problem might be with light-locker as well. When I lock the computer with <ctrl>+<alt>+<del> I can only revive by killing light-locker. From a console screen.

---

### Post by TheFu on 2021-06-20
My KVM is fairly old.  It has a push-button on the front that cycles through the 4 ports or if I press  Scroll-Lock twice, there is a beep, and pressing 1, 2, 3, or 4 will switch to that KVM port.  No hdmi or DP or USB on my KVM switch, just VGA and PS2 connections.

Every once in a while, the KVM scroll-lock hot-key doesn't work and I have to reach over to the box and press the button to switch input port groups.  I've never needed to change TTYs to activate anything.  Could that be a DP signaling fault?  I'm afraid you'll need to contact the makers of the KVM to get this question answered.

Before my current KVM, I had a dumber KVM. A new release of Windows came out and the KVM switch didn't send the computers an "I'm here" ping from time to time, so the KVM was much less useful. the newer (at the time) KVM switch does send signals that a connection exists, but it doesn't cause the monitor to wake, so it isn't any keypress or mouse movement, just some sort of "device still connected" signaling.

I've been looking to move to 4K video, but the 4K 4-port KVMs are really expensive.  I have a Belkin OmniCube now. The newer KVMs all seem to be  double the costs.  I might end up using a normal video matrix switch (have a 4x2 currently) with Synergy to access different computers instead. Still thinking about that.

---

