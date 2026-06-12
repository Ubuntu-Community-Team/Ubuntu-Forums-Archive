---
title: "I can't log Out"
date: 2007-04-23
forum: General Help
---

### Post by groovomata on 2007-04-23
I installed feisty on my compaq V5000 laptop and I noticed that I can't Log Out. I can Shut Down, Hibernate, Restart (I haven't tried Suspend yet), however Log Out does not work. If I try, I end up with a black screen. If I do <Ctrl><Alt>backspace though, I will be Logged Out. 
Has anyone else had this problem?
Thanks,
Erik.

---

### Post by INFERNO2K on 2007-04-23
Yes, this exact problem occurs on my Dell Inspiron 1501 laptop. Are you running Beryl by any chance?

I have not tested to see if this will occur when I disable Beryl. Hopefully someone has a solution in the meantime.

---

### Post by groovomata on 2007-04-23
As an experiment I was going to disable Desktop Effects however there is only an enable button. Hmmm. Anyways Suspend does work.
As soon as I figure out how to disable Desktop Effects I will give it a try
Erik.

---

### Post by dweez on 2007-04-23
Have you tried opening a terminal window and typing "logout"?  Does it respond the same way?

---

### Post by groovomata on 2007-04-23
No, that doesn't work. This is what my terminal says when I type 'logout':
bash: logout: not login shell: use `exit'

I did disable my desktop effects and I still was unable to Logout.
Thanks,
Erik.

---

### Post by groovomata on 2007-06-12
I added another use account and then tried to Switch User and that didn't work either, all I got was a black screen. By the way, I'm not using Beryl anymore as I favour stability over weirdness.

---

### Post by UncleFoo on 2007-06-12
Same here. Just since I installed Fiesty Fawn. I'm glad I'm not the only one. I'm on an old Dell Optiplex GX1 desktop.

---

### Post by groovomata on 2007-06-14
I found this launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.8.1/+bug/107115](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.8.1/+bug/107115)

---

### Post by groovomata on 2007-06-24
For myself, I found that editing /etc/X11/gdm/gdm.conf did resolve my problem as I can now logout, switch user and hibernate my laptop. Check out the launchpad link above.
Erik.

---

### Post by Absorbed on 2007-07-10
I have had a similar problem, which is now fixed, but I didn't find the solution anywhere on this forum so I'll post it here. It's pretty simple, but being a complete linux newb it took me ages to discover it.

My onboard graphics:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

I don't use any special effects or graphics acceleration, but still I was getting a blank screen when I logged out and when I ctrl+alt+f7, although I could move to a ctrl+alt+f1, then ctrl+alt+backspace and tty1 would appear. I would also get no splash screen when shutting down, even though I would when booting up.

I fixed it using "dpkg-reconfigure xserver-xorg", the key being to change the video driver from vesa to "i810". Here are the specific /etc/X11/xorg.conf settings:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection
```

---

### Post by groovomata on 2007-07-19
I have noticed that despite editing /etc/X11/gdm/gdm.conf I still cannot get my computer out of suspend mode as I end up with the 'black screen of death' and need to reboot to use my computer again.
Thanks,
Erik.

---

### Post by iridiumcao on 2007-08-11
> **INFERNO2K said:**
> Yes, this exact problem occurs on my Dell Inspiron 1501 laptop. Are you running Beryl by any chance?

I have not tested to see if this will occur when I disable Beryl. Hopefully someone has a solution in the meantime.

Did you solve this problem? Our computers are the same edition. I encountered the same problem! 

P/S: After I uninstalled the non-official graphic diver -- fglrx, everything goes well!

---

### Post by Lax368 on 2007-10-08
Thanks Absorbed, your fix worked for me.  It seems like my black screen on logout was also because of my video card driver configuration.  I did exactly what you suggested and being a Linux newbie was still able to fix the problem.  Thanks again.

---

### Post by Absorbed on 2007-10-18
> **Lax368 said:**
> Thanks Absorbed, your fix worked for me.  It seems like my black screen on logout was also because of my video card driver configuration.  I did exactly what you suggested and being a Linux newbie was still able to fix the problem.  Thanks again.

My pleasure.

I've just installed Gutsy and had exactly the same problem, but exactly the same fix worked.

---

