---
title: "Toshiba Satellite L655D, blank screen"
date: 2013-11-05
forum: General Help
---

### Post by ehasseries on 2013-11-05
I'm having a rather odd problem – my screen doesn't show anything about half the time after I boot up my system. I don't even get a BIOS screen, but the sounds are all in the correct order and I even get the log in drum. When this happens I can either use F2 or F12 to get the screen to work. From there I either set everything to set up defaults, or run Ubuntu in recovery mode. After that my computer will either boot normally or boot in low graphic mode. If I'm in low graphics mode I can reboot and be guaranteed to get the screen to work.


From what I've read here -[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)– it's likely to be a hardware issue. Do y'all think it could befixed with a BIOS update, or am I looking at a dying computer?


This issue has only come up since I dida fresh install of Ubuntu 13.10.

---

### Post by mörgæs on 2013-11-05
Hi, welcome to the fora.

Please run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

---

### Post by ehasseries on 2013-11-05
Uh, all I get is "PCI (sysfs) and the cursor, which then it goes away. I've typed it in twice and checked both times that it was correctly spelled so... I'm confused.

After a bit more looking around and not searching with the word "Ubuntu"I've found that a bunch of my laptops (Toshiba Satellite L655D) have just started to have their video cards die. Luckily I have everything backed up.

Thanks, **mörgæs**, for helping me.

---

### Post by mörgæs on 2013-11-05
> **mörgæs said:**
> ...and post lshw.txt in CODE tags.

What do you mean by a video cards dying and why do think a number of cards 'die' at the same time?

---

### Post by ehasseries on 2013-11-11
I had thought that the problem with my laptop was related to the recent upgrade to 13.10. When I searched on the Internet I was always searching with the word Ubuntu and the make and model of my computer, along with the blank screen issue. When I removed Ubuntu from the search parameters I found that a number of people with the Toshiba Satellite L655D have had the video card on their laptops suddenly stop working. They've tried hooking their laptops up to external monitors, but still nothing displayed. When taken in for testing it turned out that the video card was not working anymore. Since it's sauntered to the mother board there wasn't any way to replace the card.

Am I interpreting this information incorrectly? My own screen no longer even responds visually to a function key.

---

### Post by mörgæs on 2013-11-12
I don't know this Toshiba, but it does happen that GPU's get de-soldered because of their own heat. You could google 'reflow GPU' or similar if you want to study in more detail. 

Sometimes a certain pressure or twist applied to the casing gives enough connection for a (temporary) solution.

---

### Post by ginnie6 on 2013-11-12
We've had two Toshiba laptops (bought at the same time) and both did the same thing as yours.

---

