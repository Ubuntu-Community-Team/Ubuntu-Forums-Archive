---
title: "gdm won't work after dpkg-reconfig"
date: 2004-11-27
forum: General Help
---

### Post by kingmob on 2004-11-27
I had/have the well known problem that i cannot change my resolutions and refresh rates into their real values. Somewhere on this forum it was said i should run "dpkg-reconfigure xserver-xfree86" to fix that.
I've done that, but it seems to have made matters a lot worse. Whenever i now reboot the login manager will hang and i'll get repeated messages if i want to start another xserver. I then go to tty1 and the next problem arises. My keyboard seems to have a strange layout, the / and - have been swapped for instance, this while i have a fairly standard layout.
Well, i thought it had to be XF86config-4 which gave me problems, untill i found out that after killing X and using startx, the xserver starts fine :|. To make matters even odder my keyboard seems to be fine in gnome too, even though it's using X's settings ( i know this because if i change the settings in X, gnome will moan ;)).
To make matters complete, my mousewheel does not work anymore, no matter what options i choose in the reconfigure.

So i seem to have f'ed something up in the reconfigure, which is not that surprising since i don't get half of it. My, hopefully fairly simple, question is now: How do i get things back tot their original settings. Or, more concrete, how can i get everything autodetected again, because all was fine then?

Thanks in advance for your trouble

---

### Post by kingmob on 2004-11-27
I seem to have 'solved' this problem by upgrading to hoary. Only thing left now is no mousewheel.

---

### Post by andbert on 2004-11-27
Exactly HOW do you upgrade to Hoary?

---

### Post by kingmob on 2004-11-27
replace warty in your repositories to hoary, reload and aply upgrades.

---

### Post by wallijonn on 2004-11-27
does your /etc/modules look like this?:
```

psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
floppy

```

---

