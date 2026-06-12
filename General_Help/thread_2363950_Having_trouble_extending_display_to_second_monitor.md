---
title: "Having trouble extending display to second monitor. Stretches screen"
date: 2017-06-16
forum: General Help
---

### Post by csmadden on 2017-06-16
I just bought a new computer(MSI GS63VR) and I've set up a dual boot with Ubuntu 16.04. The graphics card is an Nvidia GeForce GTX 1060. I have a second monitor(HP) that I want to use as my primary monitor at home and to the left of my laptop. I had trouble even getting the system to recognize the monitor plugged into the HDMI port in the first place. After a lot of googling and following all the "solutions" I could find, I've finally gotten the closest I've been with two monitors, but I can only view them in mirrored mode. If I uncheck the Mirrored Mode box in the Ubuntu display settings then it gives me this weird stretched out version of my screen across my laptop screen and external monitor and it's hard to click on anything because the screen shows the cursor in one spot, but when I click it will click on something else instead. It appears as though the graphics card isn't recognizing the laptop's monitor as another screen, but adding it to the dimensions of my external monitor, because when I initially unapply Mirrored Mode it will show the monitor identifier in the top left and only the external monitor has an identifier. This question([https://askubuntu.com/questions/845686/graphical-streching-and-offset-cursor](https://askubuntu.com/questions/845686/graphical-streching-and-offset-cursor)) seems to relate to this problem, but like many of the questions I've come across that match my problem, there are no answers... This worked fine on my last computer(Lenovo Yoga 710) on Ubuntu 16, but I had a bunch of other problems and it was time to upgrade.

Things I've tried:

xorg-edgers and graphics-drivers PPA's. I tried installing all the different drivers that were available to me under these and one other PPA that I can't remember. I ran `sudo apt-get purge nvidia*` after every driver change and rebooted the machine. The drivers attempted include all of the open source, proprietary, and X-Org options.

Downloaded drivers directly from Nvidia in the form of a .run file and installed that. Well, tried to. That failed every time, but didn't give me any reasoning.

I've found that if I run the Nvidia X Server Settings app I can select the PRIME monitor, which I believe is my built-in display, but I'm unable to do anything with it. 

I even went so far as to reinstall Ubuntu...

Here are some more unresolved questions that seem to be related:

[https://askubuntu.com/questions/914198/how-to-use-my-dual-monitors-seperately](https://askubuntu.com/questions/914198/how-to-use-my-dual-monitors-seperately)

[https://askubuntu.com/questions/865215/extending-monitors-on-ubuntu-16-04-causes-distortion](https://askubuntu.com/questions/865215/extending-monitors-on-ubuntu-16-04-causes-distortion)  (same laptop)

I also used the search function on the forums here.


I also noticed that before logging in it looks like it's working correctly. Like if I move my mouse between monitors the little login password box will switch monitors and the resolution looks good.

---

### Post by dragonfly41 on 2017-06-17
When my laptop main monitor failed (totally blank screen) I had to add a second terminal to continue working.

Now when booting up I see the same symptoms you describe above
> [COLOR=#000000]stretched out version of my screen across my laptop screen and external monitor and it's hard to click on anything because the screen shows the cursor in one spot[/COLOR][COLOR=#000000]
I can get to a working remote terminal by using [Windows icon] +[ P] keys .. I believe that there is a cycle of three options.

So in summary  ..

boot up
[/COLOR][COLOR=#000000]move the cursor in second monitor until you can view login[/COLOR][COLOR=#000000]
after some time cycle through [Windows icon] + [P] until your second monitor displays desktop.

I have to hit this two key sequence twice but if you cycle through you will return to the beginning of the cycle

I have unticked "Mirror Displays" box  in System Settings > Screen Display and it shows my second monitor (a Philips monitor).

[p.s.]

Adding this reference which might help with further explanation ..
[URL="https://askubuntu.com/questions/544921/is-there-an-equivalent-to-windowsp-hotkey-change-between-mirrored-extended-mon"]
[/URL][/COLOR][https://askubuntu.com/questions/544921/is-there-an-equivalent-to-windowsp-hotkey-change-between-mirrored-extended-mon](https://askubuntu.com/questions/544921/is-there-an-equivalent-to-windowsp-hotkey-change-between-mirrored-extended-mon)

I installed arandr.

---

### Post by csmadden on 2017-06-17
Thanks, dragonfly41. I just tried that, but still gives me the same problem. I'm glad I know about the Windows key + P now, though. It's very difficult to get out of the stretched screen without it. The three options that were cycled through were Mirrored Mode, laptop screen off/external monitor on, laptop screen on/external monitor off. I tried using the arandr tool, too, but my laptop screen and the HDMI port overlap each other and if I try to move the laptop screen next to it, then it becomes stretched out.

---

### Post by dragonfly41 on 2017-06-17
You might have to try a different driver ...

[https://bugs.launchpad.net/unity/+bug/1404147](https://bugs.launchpad.net/unity/+bug/1404147)

They are found in System Settings > Software & Updates > Additional Drivers

I switched from X.Org X Server
to
Using NVIDIA Binary Driver

[p.s.]

More here ...
[URL="https://askubuntu.com/questions/573465/14-04-nvidia-dual-display-externallaptop-stretched-display-offset-desktop"]
https://askubuntu.com/questions/573465/14-04-nvidia-dual-display-externallaptop-stretched-display-offset-desktop[/URL]

---

### Post by csmadden on 2017-06-17
Yea, I already tried all of the drivers available. As I mentioned in my original post I tried both graphics-drivers and the xorg-edgers PPA's. I'm currently using nvidia-381 from graphics-drivers and it allows me to work in mirrored mode. It looks like this is a confirmed bug as this post([https://bugs.launchpad.net/unity/+bug/1404147/comments/13](https://bugs.launchpad.net/unity/+bug/1404147/comments/13)) is experiencing the exact same issues and no one is doing anything about it. I wish I knew what I was doing, but I'm just a web developer so I wouldn't even know where to start with fixing it. As awesome as this computer is, I may need to return it if I can't use extended mode...

---

### Post by dragonfly41 on 2017-06-18
From what I have read from those links I posted, with your PC, can you disable Optimus in BIOS?

---

### Post by csmadden on 2017-06-18
Nope. I've toggled just about every BIOS setting I could, too.

---

### Post by dragonfly41 on 2017-06-18
I screwed up my own ageing Dell installation by installing nvidia-381 and uninstalling nvidia-340 but through Synaptic.

I was faced with two black screens. One had already failed.
Puzzle. How could I get out of this hole?
Remember that I was driving blind having to remember keystroke sequence in navigating grub menu!

I ended up using an internal OS version 14.04 (which was working) as a live OS
installing a script in external drive /etc/rc.local (the screwed up 16.04 version).
This script reversed my last installation of driver importantly runs before login.

I had to add the -y arg to ensure that questions were answered automatically as y since I could not observe progress in terminal.

Finally resumed service and removed the recovery script from /etc/rc.local.   
Lost a few hours with this error.   But gained some experience in recovery.

[https://askubuntu.com/questions/760997/how-to-recover-from-a-nvidia-fail-on-ubuntu-16-04](https://askubuntu.com/questions/760997/how-to-recover-from-a-nvidia-fail-on-ubuntu-16-04)

[https://superuser.com/questions/164553/automatically-answer-yes-when-using-apt-get-install](https://superuser.com/questions/164553/automatically-answer-yes-when-using-apt-get-install)

...

Now back to your problem.

I've read this below and it is not good news.

[https://www.reddit.com/r/MSILaptops/comments/51taj7/gs63vr_beware/](https://www.reddit.com/r/MSILaptops/comments/51taj7/gs63vr_beware/)

> the GS63VR and GS73VR only support a single display over TB3.

---

### Post by csmadden on 2017-06-19
Yea, it's always a blast setting up a new system with Ubuntu. I ended up giving up and trying two other laptops(thank you, Best Buy return policy) and settled on the slightly cheaper Dell Inspiron 15 7567 and used some of the money I saved on getting a big 27" monitor and ordering some new RAM. It'd be nice if I could extend my monitor still, but the graphics card is also a GTX 10 series. Unfortunately I couldn't find any other laptops online or in-store with the processor and specs I wanted that had an Intel graphics card. I tried the Yoga 720 first, which had the right processor(7700HQ) and an Intel graphics card, SSD, 15" screen. It was perfect. I got home and started hooking it up when I realized there wasn't an HDMI port. I was frustrated that there were only two USB ports to begin with, but no HDMI port? What's next, no keyboards?

---

### Post by janey66778899 on 2017-11-24
one 0f my college has met the same [COLOR=#000000]situation[/COLOR],  I can ask him about how to deal with that. or you had to buy an new monitor for mac, some good choice: [https://pc4u.org/best-monitor-for-macbook-pro-retina-mac-mini-macbook-air/](https://pc4u.org/best-monitor-for-macbook-pro-retina-mac-mini-macbook-air/)

---

