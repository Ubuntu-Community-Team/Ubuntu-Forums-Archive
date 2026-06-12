---
title: "Newbie. Ubuntu 21.10 Gnome. Nautilus file manager not working right."
date: 2022-02-05
forum: General Help
---

### Post by Advait on 2022-02-05
The Nautilus icon is on my taskbar. I'm using Gnome with the Dash To Dock plugin. 

When I click on the Nautilus icon it opens a file manager window, but there's no orange line under the icon. Also, the "hover over icon" function isn't working. That means, when I hover my mouse over the icon, the open windows don't pop out. These problems started right after I upgraded from 21.04 to 21.10. Anyway to fix this?

I did a google search for this problem but didn't find anything relevant.

When I use the Dolphin file manager, it works properly. But Dolphin doesn't offer the "Other Locations" option which I often use.

---

### Post by TheFu on 2022-02-05
If you are really new to Ubuntu, it is best to stay with the LTS releases.  The current LTS is 20.04 and it has 3 more years of standard support unlike the releases you've been running which have 9 months of total support, which typically means 6 months of use.

I don't know that 20.04 Nautilus works as you desire. I barely, if ever, use file managers.  This post is more about carefully choosing to run LTS releases, not short-term, "hold my beer" and "lookie here" releases.

---

### Post by Advait on 2022-02-05
I haven't considered LTS releases but they may be a better option for me as a newbie. I'll research. Thx!

---

### Post by TheFu on 2022-02-05
I'm a 25+ yr Linux user, admin and programmer. I only use LTS for anything important.  

The non-LTS releases are for seeing what is coming or if my hardware is so bleeding edge that there's no method of HW support other than using a non-LTS release.  In general, I wait at least a year before getting something new and even then, I'll research the important things (like the chips used in a NIC) to avoid compatibility issues. I've been burned too many times. I know not to trust "Supports Linux" on a box, since it could easily be a 4 yr old kernel that had the support, but nothing newer. Actually had exactly that issue with a RAID card. The vendor plastered "Linux Supported!" all over the box and it was a well-known, but not high-end, RAID company. The RAID aspects never worked, BTW. Thankfully, the JBOD modes did work fine and I learned why all Linux people say to avoid HW-RAID and use SW-RAID. It is actually a blessing that HW-RAID support didn't work, I've learned.  When the RAID card died (all cards die), I didn't lose any data and just connected the array to different ports inside the system. I've also moved the array twice - it is on the 3rd system now, but soon to be moved again to a Ryzen (the 4th system). I wouldn't have been able to do that with HW-RAID without risking new drivers and data access changes (total data loss).

---

### Post by Autodave on 2022-02-05
13 year user here and I learned a long time ago to only use the LTS releases.

---

### Post by Advait on 2022-02-06
1. I have a perhaps irrational desire to have the latest versions of  Ubuntu with a newer kernel. My historical experience is that upgrading  from one release to the next usually causes only minimal problems.  Having the latest versions outweigh the problems (almost always).

2. If problems do arise, that means I learn more about Linux/Ubuntu as I resolve the problems with the help of the wonderful Linux community. That's a plus.

3.  I always use Clonezilla to make multiple full images of my system drive  right before I upgrade. So if an upgrade goes bad, I just restore from  an image. Easy. :-)

Now back to my original question: If anyone can help solve my issue, would be great. Thanks!

---

### Post by KBar on 2022-02-06
Could you post the list of installed GNOME Shell extensions? If you have installed them via **apt**, you can invoke **dpkg**:
```
dpkg --list 'gnome-shell-extension*'
```
Also, try creating a new user and see if the problem persists.

Are you affected by [this](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1950054) bug?

---

### Post by Dennis N on 2022-02-06
> there's no orange line under the icon. Also, the "hover over icon" function isn't working.
As to the "hover over icon" function, all you should get by hovering is the name of the application as given in it's .desktop file. If you want to see window previews, right-click the icon and select "All Windows" (see attached image). 

The orange line may be the window counter. Mine are white dots. Check the appearance tab in dash to dock preferences and try the various settings.

Realize that the workings of Dash to Dock can change from version to version.

---

### Post by zebra2 on 2022-02-06
Nautilus is under active development to keep up with Ubuntu Gnome.  I use Ubuntu 22.04 as my primary system and have Nautilus version 41 installed by default.  My secondary system runs Ubuntu 21.10 and has Nautilus version 40.2 installed. both of these versions of Nautilus are completely different than the version that I had installed with Ubuntu 9.10 12 years ago. My guess is that your Nautilus is working as designed. I just don't understand why you went from the LTS to 21.10. Why not jump all the way across the stream and use 22.04. Yes, it will also be even more different. I personally have run every development version since I switched to linux back in 2009. The biggest thing I have learned from the experience is tolerance and how to recover from a crash. 
So far as what to do about your issue, I would say go back to the LTS.  But change will still be on the horizon. Much to do with changes in the underlying dependencies.

---

### Post by Advait on 2022-02-06
> **KBar said:**
> Could you post the list of installed GNOME Shell extensions? If you have installed them via **apt**, you can invoke **dpkg**:
```
dpkg --list 'gnome-shell-extension*'
```

Sure, see below. Anything interesting?


```
advait@advait-Bravo-15-A4DDR:~$ dpkg --list 'gnome-shell-extension*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                     Version       Architecture Description
+++-========================================-=============-============-==================================================================
ii  gnome-shell-extension-appindicator       40-1          all          AppIndicator, KStatusNotifierItem and tray support for GNOME Shell
un  gnome-shell-extension-autohidetopbar     <none>        <none>       (no description available)
un  gnome-shell-extension-caffeine           <none>        <none>       (no description available)
un  gnome-shell-extension-dash-to-panel      <none>        <none>       (no description available)
un  gnome-shell-extension-dashtodock         <none>        <none>       (no description available)
un  gnome-shell-extension-desktop-icons      <none>        <none>       (no description available)
ii  gnome-shell-extension-desktop-icons-ng   20-0ubuntu3   all          desktop icon support for GNOME Shell
un  gnome-shell-extension-gamemode           <none>        <none>       (no description available)
un  gnome-shell-extension-multi-monitors     <none>        <none>       (no description available)
un  gnome-shell-extension-pixelsaver         <none>        <none>       (no description available)
ii  gnome-shell-extension-prefs              40.5-1ubuntu2 amd64        tool to enable / disable GNOME Shell extensions
un  gnome-shell-extension-taskbar            <none>        <none>       (no description available)
un  gnome-shell-extension-top-icons-plus     <none>        <none>       (no description available)
ii  gnome-shell-extension-ubuntu-dock        70~ubuntu3    all          Ubuntu Dock for GNOME Shell
un  gnome-shell-extension-workspaces-to-dock <none>        <none>       (no description available)
un  gnome-shell-extensions                   <none>        <none>       (no description available)
advait@advait-Bravo-15-A4DDR:~$ 
```

---

### Post by Advait on 2022-02-06
> **KBar said:**
> Also, try creating a new user and see if the problem persists. 

Update: I created a new Standard user and switched. Nautilus was operating normally. The multiple dots were appearing and the mouse hover worked normally (the open window thumbnails appeared). However, it looked different cuz I'm using Dash to Dock and the new user isn't. I expected that, of course.

So, how to fix?
-----------------
Hmmm.. Creating a new user... Never done that before. Let me start google searching how and I'll report back.

Any security risks in creating a new user?

---

### Post by KBar on 2022-02-06
Is the list of packages from your main user or the new test user? I'm asking because it indicates to the fact that you don't have Dash to Dock installed but you're saying you do. Did you install it from [this]("https://extensions.gnome.org/extension/307/dash-to-dock/") page?

---

### Post by Advait on 2022-02-06
> **KBar said:**
> Is the list of packages from your main user or the new test user? I'm asking because it indicates to the fact that you don't have Dash to Dock installed but you're saying you do. Did you install it from [this]("https://extensions.gnome.org/extension/307/dash-to-dock/") page?

The list is from my main user account, not the new one.

Well, I think I have dash-to-dock installed. How can I tell? Here's a pic of my dock (taskbar?)  [https://imgur.com/8F3Mb7I.png](https://imgur.com/8F3Mb7I.png) (Right hand side.) Is this dash to dock? I have Gnome Tweaks installed.

---

### Post by Advait on 2022-02-06
> **KBar said:**
> I'm asking because it indicates to the fact that you don't have Dash to Dock installed but you're saying you do. Did you install it from [this]("https://extensions.gnome.org/extension/307/dash-to-dock/") page?

I installed it back in August, so my memory is hazy. The page you link to looks vaguely familiar.

---

### Post by Dennis N on 2022-02-06
> Is this dash to dock?
No, that's dash-to-panel.

---

### Post by KBar on 2022-02-06
> **Advait said:**
> Well, I think I have dash-to-dock installed. How can I tell? Here's a pic of my dock (taskbar?)  [https://imgur.com/8F3Mb7I.png](https://imgur.com/8F3Mb7I.png) (Right hand side.) Is this dash to dock? I have Gnome Tweaks installed.
Unfortunately, I don't use GNOME so I can't really tell what it is. On the GNOME Shell extensions website, there is a tab called *Installed extensions*. Depending on your web browser, you need a dedicated extension (i.e. browser add-on) to access it. Check whether you have it installed and also get the list of extensions if you can. There is also a separate app for extensions on your desktop named *Extensions*. Check there.

---

### Post by Advait on 2022-02-07
> **Dennis N said:**
> No, that's dash-to-panel.

Thanks for recognizing that. Very helpful. Looks like no one here can resolve my issue  :-[  so I'll try posting my q elsewhere. Perhaps on the Dash to Panel github site.

---

### Post by KBar on 2022-02-07
> **Advait said:**
> Looks like no one here can resolve my issue  :-[  so I'll try posting my q elsewhere.
Perhaps you can provide a bit more details as requested? `dpkg -l` tells that Dash to Panel is also not installed.

I was going to suggest removing this extension from that website and install it from the official Ubuntu repositories but it's up to you.

---

### Post by Advait on 2022-02-07
> **KBar said:**
>  `dpkg -l` tells that Dash to Panel is also not installed.

I posted a pic of my taskbar ( [https://imgur.com/8F3Mb7I.png](https://imgur.com/8F3Mb7I.png) ) and Dennis N said it was Dash to Panel. I think that's the only Gnome extension that integrates the taskbar with the system tray (what do they call the system tray in Gnome land?).

---

