---
title: "Upgrade to 8.04 - trully disappointed"
date: 2008-04-27
forum: General Help
---

### Post by s-lime on 2008-04-27
[http://shrani.si/f/J/iN/ADjmRZ2/screenshot.png](http://shrani.si/f/J/iN/ADjmRZ2/screenshot.png)

- a lot of programs are "closing unexpectedly", even those I didn't even run!
- lm_sensors applet is not working properly.
- System needs like 3x more time to start up
- In FF3, all of addons stopped working. How can I degrade?

I'm trully disappointed. From my experience, windows is a lot faster.

---

### Post by pbpersson on 2008-04-27
You said you upgraded to Hardy Heron.  What were you running before? 

How did you upgrade, and were there any error messages displayed during the upgrade?

---

### Post by Seks on 2008-04-27
Agree, but hopefully they will weed out the bugs soon enough.

I can't even use it right now, it crashes after a few minutes of web browsing.

---

### Post by s-lime on 2008-04-27
Upgrade went through just OK... No error messages...

How can I degrade from FF3 to FF2.0.0.14?

I'm questioning myself why is LTS version so buggy?

---

### Post by FredB on 2008-04-27
For "downgrading", just do a search, you will find it.

And your bugs stinks upgrade above a kinda "dirty" previous version : install / uninstall frequently done, 3rd party repositories, and so on...

So, I want to know on 100 upgraders, how many get into such troubles...

---

### Post by FredB on 2008-04-27
> **Seks said:**
> Agree, but hopefully they will weed out the bugs soon enough.

I can't even use it right now, it crashes after a few minutes of web browsing.

Just try a clean install, after you backup your datas... Best cure I know...

---

### Post by chrisccoulson on 2008-04-27
> **s-lime said:**
> [http://shrani.si/f/J/iN/ADjmRZ2/screenshot.png](http://shrani.si/f/J/iN/ADjmRZ2/screenshot.png)

- a lot of programs are "closing unexpectedly", even those I didn't even run!
- lm_sensors applet is not working properly.
- System needs like 3x more time to start up
- In FF3, all of addons stopped working. How can I degrade?

I'm trully disappointed. From my experience, windows is a lot faster.

- Are there actually any crash reports in /var/crash? I would try clearing all these files from /var/crash first and see if your problem goes away. Maybe the problem is with Apport (although Apport should be disabled). Did you upgrade or do a clean install? If you did an upgrade, did the upgrade go ok? There are some important logs in /var/log/dist-upgrade which can indicate if the upgrade went badly and might help diagnose a problem. Also, do you have any third party repositories in your /etc/apt/sources.list (please post it), and did you have a lot of software installed from third party repositories?

- Have you configured lm-sensors properly?

- Install bootchart, and post the bootchart image here, so we can get an idea what is holding up the boot process

- Firefox add-on developers are still catching up with FF3, so some add-ons won't be compatible yet. Which addons are you having issues with? Sometimes it is just the version checking which fails, and the add-on would actually work otherwise. In this case, you can actually modify the add-ons install manifest (install.rdf) and change the MaxVersion from '2.0.*' to '3.*'. Have a look through the folders in your ~/.mozilla/firefox/<*random_number*>.default/extensions

---

### Post by the_darkside_986 on 2008-04-27
I'm kinda disappointed as well. The new packages are very nice, but the whole system is completely slow and stutters constantly, even startup time is unbearable. I've looked in top and there is no specific process that consumes CPU, but loading programs and running programs seems to cause the system to freeze momentarily.

I've disabled compiz, trackerd, anything I can think of. It doesn't even do this on the Live CD session, only after I install it. I suppose my hard drive isn't failing because the Windows XP partition runs as it always does. Gutsy doesn't do this either.

I have no idea what to do. I would get a SATA drive instead of this old ATA junk if I knew that would fix the problem, but I'd rather continue using my 500 GB drive and get this fixed because I've already bought a new LCD for Gutsy to work right (without manual xorg.conf tinkering). But I have no idea how to fix this. I think it is a kernel problem or something in the system is misconfigured for my hardware.

Everything would be fine if it weren't for the constant stuttering and lagging of every task that makes using the system nearly unbearable. I did a clean install.

---

### Post by ludovicc on 2008-04-27
To keep using Firefox 2, which should be stil installed on your system after the upgrade, edit the Firefox launcher in the menu (right-click, select Properties), and replace 'firefox' by 'firefox2'

Firefox 3 is still a bit new, and quite a few plugins are not working on it still. Wait a bit until they are fixed, or better help us to fix them if you have any computer skills!

Ludovic.

---

### Post by meho_r on 2008-04-27
> **FredB said:**
> Just try a clean install, after you backup your datas... Best cure I know...

I agree. And if you have config files in your home directory left from previous version of Ubuntu, they can be the cause of crashing/instability/etc.

---

### Post by danwood76 on 2008-04-27
I have just upgraded both of my machines to hardy.
But not through the upgrade path, I did an almost fresh install and just retained the config files I wanted.

I think if your going to upgrade your OS you may aswell start afresh and install only the apps you use regularly.
You always end up with a cleaner faster system.

I think I have only added a couple of seconds to the boot time on my laptop and my desktop is about the same as gutsy.

---

### Post by ghost_ryder35 on 2008-04-27
i'd back up your '/home' directory and then do a clean install to fix the laggy system.  8.04 itself is very good, just the upgrade process messed things up thats why the system now is disappointing

---

### Post by FredB on 2008-04-27
Thanks for the people who said : do a fresh install after a data backup. Nearly 50% of the complaining could disappear this way...

---

### Post by s-lime on 2008-04-27
I have so many programs installed (i need them all)... How can I keep their configuration data?

---

### Post by ghost_ryder35 on 2008-04-27
> **s-lime said:**
> I have so many programs installed (i need them all)... How can I keep their configuration data?
backing up the /home directory does this

---

### Post by hatewindows on 2008-04-27
I guess each and every machine has its problems--Because i installed 8.04 the day it came out and today it runs FLAWLESS! Firefox 3 runs flawless--In fact everything i open and play with--Runs 100% and very fast! I couldnt ask for a faster boot time--In seconds--from a Turned off PC the ubuntu login screen is up--Blows XP and VISTA off the map!

I hope everyone gets the problems fixed--as for me--I installed 8.04 clean on a formatted :popcorn: hard drive--and its been running 100%!!!!!!!!!!!!!!  Thanks everyone at the ubuntu team...  Great job...  Bill Gates--will never get a penny from me again!!!!!!! XP vista---Never again!

Everyone have a great day!!    Mark

---

### Post by NOLU on 2008-04-27
> **the_darkside_986 said:**
> I'm kinda disappointed as well. The new packages are very nice, but the whole system is completely slow and stutters constantly, even startup time is unbearable. I've looked in top and there is no specific process that consumes CPU, but loading programs and running programs seems to cause the system to freeze momentarily.

I've disabled compiz, trackerd, anything I can think of. It doesn't even do this on the Live CD session, only after I install it. I suppose my hard drive isn't failing because the Windows XP partition runs as it always does. Gutsy doesn't do this either.

I have no idea what to do. I would get a SATA drive instead of this old ATA junk if I knew that would fix the problem, but I'd rather continue using my 500 GB drive and get this fixed because I've already bought a new LCD for Gutsy to work right (without manual xorg.conf tinkering). But I have no idea how to fix this. I think it is a kernel problem or something in the system is misconfigured for my hardware.

Everything would be fine if it weren't for the constant stuttering and lagging of every task that makes using the system nearly unbearable. I did a clean install.

I also have had nothing but trouble with it being very slow and often folders will hang before opening it's so slow.

---

### Post by jeyaganesh on 2008-04-27
I am using Heron from its beta version. It is working very smoothly and faster as like it was with other old versions. For me FF3 working faster in ubuntu but not in my vista. You can still install FF2 from synaptic package manager. Heron is the best of Ubuntu hierarchy, because it well cooperate with my belkin wireless adapter and nvidia graphic card. Last version needed some suggestions from the forum. But there is good understanding between them in Heron.:)

---

### Post by jeyaganesh on 2008-04-27
None of my program close itself in Heron.

---

### Post by adityakavoor on 2008-04-27
even I am very dissapointed with hardy.

Just 5 mins of browsing anf off it goes. System goes black

---

### Post by ssadhale on 2008-04-27
I would like to answer some of your questions - 

1. Did you have Automatix installed in your previous version? - I have heard reports of systems getting messed up if you install anything through automatix. It used to be a culprit in breaking upgrades.
 
2. Do not upgrade at least for now - instead back up all your data and do a complete fresh new install. I did the same and I have had no problems whatsoever. Not even with FF3 b5. Everything is working just fine.

3. If you still would like to resolve FF3 problems - then go to synaptic. Search for firefox, mark for complete removal, apply changes. This will remove FF3 and then reinstall. If that doesnt help, then again remove completely from synaptic. Download the stable 2.0 version from mozilla.org and install that on your machine.

4. If you do face any problems - then please do the community a favor.. click on Applications -> Systems Tools and then click on Report a problem...

---

### Post by Thanh-BKK on 2008-04-27
Hello.

Linux-newbie here - i am *somewhat* happy with 8.04 - fresh install on virgin HDD. Runs ok, not too fast but certainly faster than XP/Vista on the same machine (different HDD). The usual problems (TV-Out - the neverending story) and the dependency hell of getting AWN to work......

Samba crashes as soon as it's started, EVERYTIME

One of the NTFS partitions refuses to mount (the other 3 work!)

Can't get Bluetooth dongle to work

IrDA dongle ditto

But apart from that - happy guy here :) FF3 is faster than FF2 for me......

Best regards....

Thanh

---

