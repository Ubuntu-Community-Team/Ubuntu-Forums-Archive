---
title: "Something is not right with Ubuntu 13.10"
date: 2013-10-24
forum: General Help
---

### Post by jasonbiz88 on 2013-10-24
The day I upgraded my 13.04 to 13.10, my entire system was thrown out of wack. The system was not behaving correctly. I was forced to uninstall ubuntu, download 13.10 from the site and reinstall once again. By doing that, my linux system continues to suffer from bugs and glitches. The clock disappears. The shutdown button fails to respond or does not work. The applications seem to work fine, but my ubuntu software center has only a few apps available compared to the massive library raring ringtail had. 

I continue to send Ubuntu error reports and they still have not fixed it. What's going on? What can I do to make my system run as flawless as it did when it was running 13.04 raring ringtail?

---

### Post by speartip on 2013-10-24
First I would check the MD5 sum from here: [http://releases.ubuntu.com/saucy/](http://releases.ubuntu.com/saucy/) To make sure your image is fine, then check the media that you install from at boot. I must admit when I 1st installed 13.10, I had loads of weird glitches, so I reinstalled & now it runs flawlessly, so must have been a dodgy install. Upgrades can always cause issues, that's why a fresh install is recommended. But from what you describe, I would be tempted to do another fresh install, & see if the problems persist.

---

### Post by rafe101 on 2013-10-24
I don't think it's useful to suggest that these problems are related to installation. The forums and bug reports are full of these problems. I, myself, encountered no abnormalities while upgrading, but have all these (and more) problems. 

I do not remember how I fixed the clock. It was either mucking around in dconf or in the "date & time" settings, checking and unchecking stuff. I had to get my panel menu back too (it's in the same region) and had so many other problems I don't recall any specifics. 

I still have not found a solution for the frequent network problems, where network-manager refuses to come up and suspend really doesn't work at all. There are bug reports with many followers filed, but no solutions yet.

---

### Post by Johan De Cauwer on 2013-10-24
Default update of the system is once a week. I'd start in a terminal:
sudo apt-get update
sudo apt-get upgrade

On another partition of my system I did try out 13.10 (from scratch) and it worked without flaws of networking, clock, shutdown etc.. And the software center gives a large choice. So I wouldn't "blame" Ubuntu.

But on the system I work most on I stay with 12.04 LTS. 
Reading complaints like yours inevitably raises the question: why don't you install 12.04? It's nearly perfect.

---

### Post by sdowney717 on 2013-10-24
> **rafe101 said:**
> I don't think it's useful to suggest that these problems are related to installation. The forums and bug reports are full of these problems. I, myself, encountered no abnormalities while upgrading, but have all these (and more) problems. 

I do not remember how I fixed the clock. It was either mucking around in dconf or in the "date & time" settings, checking and unchecking stuff. I had to get my panel menu back too (it's in the same region) and had so many other problems I don't recall any specifics. 

I still have not found a solution for the frequent network problems, where network-manager refuses to come up and suspend really doesn't work at all. There are bug reports with many followers filed, but no solutions yet.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1184262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1184262)

They have known about the bug since May 2013 and no one assigned to a fix yet.
I experience the same bug and the fan on the AMD x1300 video card sometimes does not spin up on awaken from suspend. 

The work around is to issue commands as shown in the bug reports to bring wireless up again.

---

### Post by grahammechanical on 2013-10-24
The things people say about 13.10 they or others said about 13.04 and 12.10 before that. Some here do not advise being quick to upgrade to a new release. The developers are now working on what they call Stable Release Updates (SRU). This is were they put into the update channel any fixes that were not ready in time for release date. Some of us do not advise upgrading at all but re-installing instead.

I have been running 13.10 since it was Saucy Salamander. Towards the end of the development cycle I did notice with a new install that sometimes the power/cog would not be in the global menu or the clock app indicator would disappear. Logging out or a reboot would fix it. I have not had that happen for days. It did not happen yesterday when I put in my first install of Trusty Tahr.

I have now moved on to what will become 14.04 (Trusty Tahr) and like other testers I find it stable enough to be boring. It is built on 13.10 code after all. Things will change. New kernels will come through and that can mess things up. So to can updates to the Gnome desktop. Not to mention proprietary video drivers.

What is happening? Linux is being developed. That is what is happening. We are not using a finished operating system. We will not get really, really stable with things 'working out of the box' until we buy Ubuntu machines. Then we will get complaints that Ubuntu has become like Apple and Microsoft denying users the freedom to modify the OS.  That freedom is also a freedom to break the OS, which commercial computer retailers will not want us to do.

Regards.

---

### Post by Wray on 2013-10-24
> **Johan De Cauwer said:**
> Default update of the system is once a week. I'd start in a terminal:
sudo apt-get update
sudo apt-get upgrade

On another partition of my system I did try out 13.10 (from scratch) and it worked without flaws of networking, clock, shutdown etc.. And the software center gives a large choice. So I wouldn't "blame" Ubuntu.

But on the system I work most on I stay with 12.04 LTS. 
Reading complaints like yours inevitably raises the question: why don't you install 12.04? It's nearly perfect.

I was running 12.04 and then rashly installed 13.10 AND  things promptly went to hades in a handbasket!
Browsing is almost impossible (thunderbird).  Where can i find/download 12.04?
Thanks in advance

---

### Post by rafe101 on 2013-10-25
I really wasn't complaining. I am confident things will get sorted out. For some reason, the network manager has even been behaving better. If I could just get suspend to work I'd be perfectly content. The computer I updated is our home office computer and we like to walk away from it and come back; suspend is a real convenient thing to have. I just didn't want the OP to become convinced that everything was attributed to installation problems, then spend more time reinstalling just to find the same problems waiting for him.

---

### Post by mc4man on 2013-10-25
The datetime & session indicators not showing up sometimes has been fixed, will show up at some point in 13.10
(whether that fixes an unresponsive session indicator you'll need to see..
[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1239710](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1239710)

---

### Post by ian-weisser on 2013-10-25
> **sdowney717 said:**
> [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1184262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1184262)

They have known about the bug since May 2013 and no one assigned to a fix yet.

Wow. What an amazingly unhelpful and polluted bug report.
I can see why nobody wants to try to fix it.

---

### Post by Johan De Cauwer on 2013-10-25
> **Wray said:**
> I was running 12.04 and then rashly installed 13.10 AND  things promptly went to hades in a handbasket!
Browsing is almost impossible (thunderbird).  Where can i find/download 12.04?
Thanks in advance

Sorry for a late reply: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by Johan De Cauwer on 2013-10-25
> **grahammechanical said:**
> 

What is happening? Linux is being developed. That is what is happening. We are not using a finished operating system. We will not get really, really stable with things 'working out of the box' until we buy Ubuntu machines. Then we will get complaints that Ubuntu has become like Apple and Microsoft denying users the freedom to modify the OS.  That freedom is also a freedom to break the OS, which commercial computer retailers will not want us to do.

Regards.

What you're saying is correct... for developpers. But Ubuntu has little or no meaning if it can't be used by... users. And users want to use a reasonably stable system. Not much, but a clock should work, a letter should be able to print and when one wants to log out... you get the picture. A user doesn't want to break the OS, and doesn't want it broken. Again, what's the meaning of your work if it can't be used?

With respect and kind regards.

---

### Post by Swagman on 2013-10-25
After Upgrading from 13:04 (64) to 13:10 last night I noticed the clock wasn't displaying. Going into clock prefs and everything was greyed out (unselectable) but I could see it was as I left it.

This morning I did an update and switched off & went shopping.  I've just switched back on and.... Yay... It's working again !! (clock/Calendar)

Thanks to these forums I've also got Google Earth back up and running again.

Can't keep a good O/S down for long !

---

### Post by mc4man on 2013-10-25
> **Johan De Cauwer said:**
> What you're saying is correct... for developpers. But Ubuntu has little or no meaning if it can't be used by... users. And users want to use a reasonably stable system. Not much, but a clock should work, a letter should be able to print and when one wants to log out... you get the picture. A user doesn't want to break the OS, and doesn't want it broken. Again, what's the meaning of your work if it can't be used?

With respect and kind regards.
13.10 had limited resources directed at the Desktop install so it's full of bugs & possible usability issues. No one should be installing it thinking otherwise.
I find it superior to 13.04 but there is some user side work involved to overcome the lack of attention during dev.  Otherwise a number of issues will eventually be fixed & make it to 13.10 though at the end of the day it's only got a 9 month lifetime 

However you can rightfully expect better work & product in 14.04, we'll see.

---

### Post by ian-weisser on 2013-10-25
> **Johan De Cauwer said:**
> [...] Ubuntu has little or no meaning if it can't be used by... users. And users want to use a reasonably stable system. Not much, but a clock should work, a letter should be able to print and when one wants to log out... you get the picture. A user doesn't want to break the OS, and doesn't want it broken. Again, what's the meaning of your work if it can't be used?

For most users, the clock *does* work.
For most users, printing *does* work.
For most users, logout *does* work.
For most users, the system is rock-solid and stable.
For most users who recently upgraded to 13.10, nothing broke.

I understand the frustration of key tasks reverting from working to non-working. Been there, too. It's a **terrible** feeling, like you are all alone and suffering and nobody will listen and nobody seems to care.
We will listen, we care, and we can help you solve those problems.

Not everybody has these problems. Not everybody has the same problems. They don't. Look at the wide variety of problems reported in this forum that you *don't* have.

---

### Post by Johan De Cauwer on 2013-10-25
> **ian-weisser said:**
> For most users, the clock *does* work.
For most users, the system is rock-solid and stable.
For most users who recently upgraded to 13.10, nothing broke.


I know that and I don't have any problems. (mostly because I stayed with 12.04, the first choice if one wants to download desktop ubuntu, but also in the 13.10 I tested)

My reaction came because I had the impression from that poster that instability is inherent in the not LTS Ubuntu and one better learns to accept it.

And if that's the case, if the Desktop is an afterthought, that fact merits better communication: wait before an upgrade or stay with the LTS.

But *my* experience is (nearly) perfect.

---

