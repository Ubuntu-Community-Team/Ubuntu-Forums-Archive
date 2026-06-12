---
title: "Ubuntu system corrupt"
date: 2008-03-08
forum: General Help
---

### Post by heyzuphowsitgoin on 2008-03-08
ok so i really messed this computer up I think...

I was running compiz and emerald at the time, so I had all those fancy effects. I was doing a project with the computer and I had to switch monitors. The screen driver was set to my current screen, so it would not display anything on the other screen. I plugged the other screen in with the mouse positiond over the detect button and I pressed it. It worked, but after that I noticed that the buttons on top of the window like minimize and stuff were back to normal, not the emerald theme. I then realized that the effects were back to nothing, and when I tried to set the effects to anything other than none, it would say could not enable effects or something like that. I made sure there were no restricted drivers, did another monitor detect, but it found the wrong monitor, and only gave me the option of a 600X800 display. I restarted the computer, but it said it could not detect the right monitor  setting and could not display right(before the login screen) and gave me the option to detect the right monitor. I did that, but it still could not find my monitor. I also tried changing the video card driver, but that didn;t work either. Now, when i boot my computer up, the screen comes up but the monitor shows a bunch of colored lines. I can see the black increase in the middle of the screen when i type my username, and i can log in, but the system is useless. I need the computer for a project in 2 days... HHHHHHHEEEEEEEEEEELLLLLLLLLPPPPPPPP

---

### Post by pointone on 2008-03-08
Try regenerating your xorg.conf:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

