---
title: "[SOLVED] Failed to start X Sever"
date: 2008-01-06
forum: General Help
---

### Post by Gillette on 2008-01-06
I just started using ubuntu last month. This morning when I tried to boot up the computer I got this message:

"Failed to start x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"

When I select yes the following appears:

"/etc/gdm/failsafeXserver: line 47[:  too many arguments]
Warning: failsafe mode was already attempted within 30 seconds
Warning: falling back to gdm to report issue."

When I select ok the following appears:

"The x server is now disabled. Restart gdm when it is configured correctly."

How do I fix this?

---

### Post by reckless2k2 on 2008-01-06
what have you recently done or fiddled with? i would say that you recently changed something as far as in kernel or video driver setup.

---

### Post by pdub on 2008-01-06
Please post the contents of /etc/X11/xorg.conf.

---

### Post by Gillette on 2008-01-06
I remember I was exploring the System Preferences and Administration, but don't remember doing anything.

I have since booted up the computer from cd and have looked in Preferences and Administration but didn't see anything that looked familiar. So I can't say for sure what I managed to change.

---

### Post by SOULRiDER on 2008-01-06
Can you post your /etc/X11/xorg.conf file?
```
cat /etc/X11/Xorg.conf
```

---

### Post by Haruno Parhina on 2008-01-06
had the same prob...

i typed this, as you suggested...
>  cat /etc/X11/Xorg.conf

this is the only result:

> cat: /etc/X11/Xorg.conf: No such file or directory

please help, i can't start my ibm laptop now..

---

### Post by eapache on 2008-01-06
Ubuntu is case-sensitve. 

cat /etc/X11/xorg.conf

---

### Post by Gillette on 2008-01-06
How do I get the contents of 
 /etc/X11/xorg.conf.

---

### Post by SOULRiDER on 2008-01-06
You can get the contents with 
```
cat /etc/X11/xorg.conf
```

Mind the x in xorg is lowercase, that was a typ0 in my prevous post.

---

### Post by CheeseEatingBulldog on 2008-01-07
If you are desperate for X and it won't load, you can always force a reconfig by killing X first and then reconfiguring via terminal:

```
sudo killall gdm
```

```
sudo dpkg-reconfigure xserver-xorg
```

```
sudo gdm
```

---

### Post by Gillette on 2008-01-09
I had time tonight to look at the contents of 
cat /etc/X11/xorg.con

It took me awhile to figure out how to get there. Anyway the contens of the file were voluminous and I did not know of a way to save it to a floppy so I could transfer it here. I tried using the print command but nothing happened. 

After that I pressed esc to get out of grub. So I pushed b to try and boot up the computer. The computer booted up normally without the "Failed to start X server" message. So something fixed the problem. Perhaps booting the computer from the CD did something to reset it.

There is one annoying problem though. This message appears in extremely large font (maybe font size 100): Ubuntu is running. I have to press the esc key to proceed. Anyway to eliminate this annoyance? Also when I get to the login screen and type in my username and password, the font is also enormous.

Thanks everyone for the help in resolving this problem with the x server.

---

