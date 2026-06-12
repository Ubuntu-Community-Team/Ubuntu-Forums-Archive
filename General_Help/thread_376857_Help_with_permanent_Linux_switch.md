---
title: "Help with permanent Linux switch"
date: 2007-03-05
forum: General Help
---

### Post by Zeromaru on 2007-03-05
I've decided that I want to be done away with Windows XP forever, and upgrading to Vista is unfortunately not an option right now (I live on-campus, and certain wireless access points deny Vista, some don't, and computing department won't do anything about it). So that leaves either Linux or a hacked OS X install, and given that I hate the Dock I'm going with Ubuntu 6.10.

Now, I'm no stranger to the system. I've tried numerous times before to make a switch (with Fedora 2 and 5 and later Kubuntu), but always something held me back. I also use Linux quite extensively in my courses, and because of which, I know far more now than I did the last time I attempted a switch. And now I have a brand new custom-built computer with uber-compatible hardware and the biggest game I play is World of Warcraft (which works perfectly through Wine anyway), so I figured now is the best time to try again.

But, alas, there are a couple pieces of hardware I have that aren't quite so easy to get along with. The first is my Bluetooth USB dongle, which has a Broadcom 2045 chip. I haven't been able to find much information about this chip on Linux, so any help here would be greatly appreciated.

The second is my TV tuner, an ATI Theater 550 Pro chip (PCI Express x1 interface). I'm aware that there is no official driver, but I can't seem to find anything about a reverse-engineered third-party driver or using the Windows driver through Wine. Running a trimmed-down Win2k install in virtualization is a viable option here as well, but I don't know if this is at all possible (I know VMware can tunnel USB devices into a virtualized OS, at least in Windows, but I don't know if it's only because the devices are working fine in the host OS or not, and I'm even more on the dark with doing it with PCIe devices). Available software isn't an issue, since I already use VLC to watch TV anyway.

I use my Motorola RAZR V3c as a digital camera, and I'm always transferring pictures from my phone to computer. I already use BitPim, but does one need particular drivers for the phone (I had installed the Windows drivers, but don't know if they were required or not) or will Bitpim automatically connect using it's own methods?

My printer is a Canon i350 printer. Again, I know there's no official driver, but it seems that the only third-party one I can find costs money. Any free ones available? Again, this is one option where I wouldn't mind using virtualization, since I don't print regularly.

My apologies if I sound rather uneducated, but I do know a lot of what I'm doing (I'm fairly comfortable with command line, editing config files, compiling source packages, etc.), and honestly it will take just as long for me to research and trial and error to get these things to work as it will to ask the experts who already know how. Thank you muchly to anyone who could help me settle these issues!

---

### Post by rsambuca on 2007-03-05
Welcome back!  I can't help you with much, other than to say that unfortunately your ATI 550 is a brick in linux.  I ended up giving mine to my mom and stuck in a Hauppauge.

---

### Post by Zeromaru on 2007-03-05
I only bought it back and December, with the rest of the computer. My old card was a Winfast TV2000 XP card (which I did get working in Linux... sorta), but it was a cheap card, no S-video, but it worked. So I figured I would get a new TV card, PCI Express x1 (to use the slot since nothing else would), and I trust ATI chips. But this one doesn't work with Media Center for some reason (it says it does), and on top of that there's about a 3 second delay from input to output (though audio/video stays synced), which makes it impossible to play games on, as well as composite/S-video in not working in PowerCinema (does in VLC though). But it works for watching TV, which is what I use it for 99.9% of the time. Probably this summer I'll get a new one, if I can find a cheap 480p (maybe 720p for future digital broadcasts) Hauppage tuner (with at least component in, I plan on getting a Wii).

But now the TV thing is settled, what about the rest? Any help would still be great.

---

