---
title: "Nvidia nightmare on Xubuntu 12.04"
date: 2014-02-15
forum: General Help
---

### Post by ericmark4 on 2014-02-15
&#65279;Hi. Need help with Nvidia graphics on Xubuntu Precise x86. (I went back to 12.04 after wasting fruitless hours trying to get DVD playback on 13.10.) 

I've fought for days to get Nvidia drivers installed. I have read tons of posts on this problem, and tried every solution proposed, one by one. Nothing works long-term. I keep giving up, purging all things Nvidia and going back to the Nouveau driver. That works---but the Nvidia driver does make things look better and brighter---plus the principle of the thing.

Here's where things stand: Every time I install any Nvidia graphics driver via any method, (jockey, terminal, Synaptic, several different drivers) when I reboot I need to log in via command line and do startxfce4. When I get to the desktop, all shutdown options except Log Out are grayed out, the display is at 1280x1024 even though I had set it for 1024x768 and things are a mess. I've tried every suggestion I read, from re-doing headers manually on down the line.

A few other things: 

1. When I push the button to shut down, a notification pops up that "power manager is not authorized."

2. I repeatedly delete the xorg.conf file from etc/X11 each time things go wrong. A weird quirk here is that an X11 folder is created in /usr/bin, too. I have not read about that and cannot figure it out. I delete that folder as well. 

3. My 2008-build PC runs the GeForce 6 series. The last Nvidia driver to support it is supposedly 304---but now an option for 331 appears in jockey, and the latest version of nvidia-settings is listed as 331. Not sure if that contributes to the problem.

4. No matter what graphics I use, enabling Hibernation leads to the scenario outlined: Next boot or the boot after that I get the command-line log-in, etc. 

Any help would be great. Thanks. I seriously might go back to Lucid, which was rock-solid the whole time I used it. Maybe I just lucked out by having a box with Nvidia graphics and whatever quirk causes Saucy not to play DVDs....but I gotta wonder about how things are going in 'buntu-land lately. 

Thanks and Regards.

---

### Post by ericmark4 on 2014-02-21
Marking this as Solved, though that's debatable. My "solution" was to wipe the partition and do a clean install of Xubuntu 12.04.4. So far all is well, in Nvidia-land and elsewhere. It is amazing that two years after the disconnect between Nvidia and 12.04 became clear there is no clear fix. Apart from that I like Precise with xfce and plan to stick with it. We shall see.

---

