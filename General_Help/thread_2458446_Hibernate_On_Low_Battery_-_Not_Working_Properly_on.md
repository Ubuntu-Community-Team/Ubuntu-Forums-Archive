---
title: "Hibernate On Low Battery - Not Working Properly on Gnome"
date: 2021-02-24
forum: General Help
---

### Post by Asif_Ahmad on 2021-02-24
Hello Everyone, 

I installed Ubuntu Gnome a few weeks ago (Fresh install) on my Dell XPS 13 laptop. I am having an issue with hibernate not working when reaching a critical low battery. 

**The Issue:** 
I&#8217;ve noticed that when my laptop battery reaches about 3%, I get a system message saying the system will enter hibernation mode very soon. Oddly, it seems that the computer goes into standby / suspend mode, because I can wake up the computer with the mouse, and does NOT enter hibernate mode. I tested and made sure hibernate works (by running systemctl hibernate) and the computer does hibernate properly without any issues when running the command manually in the terminal. 

**The Problem: **
So, the main issue is the computer enters standby / suspend and not hibernate when the battery reaches 3%. I haven&#8217;t done much in terms of custom configurations, and it **APPEARS** that it should enter hibernate according to the system message that pops up on the screen. What should I do to check if things are setup correctly, and to fix the actual problem and have the computer enter hibernate when the battery reaches 3%? 

[B]Other Stuff:
[/B]I also forgot to add, that I did modify a few configs to enable a power management setting for when I close the laptop lid (and the machine goes into standby, this is expected), I also wanted the machine to go into hibernate after a specific period of time (60-min). Specifically, for the laptop to go into &#8216;suspend then hibernate&#8217; functionality. To achieve this, I followed the steps outlined by &#8220;PRIHLOP&#8221; in the following post here:
[https://askubuntu.com/questions/12383/how-to-go-automatically-from-suspend-into-hibernate](https://askubuntu.com/questions/12383/how-to-go-automatically-from-suspend-into-hibernate)

By modifying the sleep.conf and the logind.conf config files, I was able to get this working **PERFECTLY** as expected. However, I mention it because maybe that&#8217;s the issue preventing the laptop from going into Hibernate on low-battery, even though the System displays a message that it wants to hibernate on low-battery:
[https://imgur.com/Pn2bFri](https://imgur.com/Pn2bFri)


Any help would be greatly appreciated. Thanks in advance to anyone who can help me figure this out.

---

### Post by Asif_Ahmad on 2021-02-27
Bump

---

