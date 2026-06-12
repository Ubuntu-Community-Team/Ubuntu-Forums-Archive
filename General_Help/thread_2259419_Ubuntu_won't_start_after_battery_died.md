---
title: "Ubuntu won't start after battery died"
date: 2015-01-03
forum: General Help
---

### Post by laserman on 2015-01-03
Greeting all and Happy New Year.

I have an HP 10.1 laptop that was running Ubuntu Netbook 10.04. a few months back, I install alongside, a full version of Ubuntu 12.04. Some time during the night a couple of days ago, while the computer was hibernating, the battery lost power. When I went to power up, it would not boot. I got to the grub and selected the proper kernel header but it would not boot. Got some text on the screen, something about runnit: Warning, child failed.

I found a topic where they recommended re-installing the system. I researched and found where I can re-install the OS without losing the data (backed it up anyways) and was successful. It would boot once but when I powered down and powered back up, I would only end up with a blank screen and a blinking cursor.

I downloaded Boot-Repair ISO and booted up. Went through the recommendations and was again, able to boot up, but when tried a second time, blank screen and blinking cursor.

Here is the URL:
[http://paste.ubuntu.com/9665432/]("http://past.ubuntu.com/9665432")

If all is unsuccessful, I will just install a new OS. I was planning to upgrade anyways but wanted to maintain what I have already installed with out painstakingly having to do it individually.

laserman

---

### Post by cariboo on 2015-01-04
Move to a thread of it's own. 

Have you tried starting in recovery mode?

If you haven't , try it, and once you reach the menu select root. Once at the prompt, run:

```
fsck /dev/sdX
```

where /dev/sdX = the root partition of your Ubuntu installation.

---

### Post by oldfred on 2015-01-04
You have grub from the old 10.04 install in the MBR.
Better to have grub from the 12.04 install in MBR. You can use Boot-Repair's advanced mode to choose which install to install grub into the drive that is sda.

---

### Post by laserman on 2015-01-06
I was not able to perform either of your suggestions because the laptop itself, now in its sixth year, is not able to power up. Thanks for your suggestions.

---

