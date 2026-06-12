---
title: "fan on all the time, slow machine and slow internet Ubuntu 16.10 vs live Wifislax"
date: 2016-11-27
forum: General Help
---

### Post by thosecars822 on 2016-11-27
Hello

For some reason the computer's fan is on all the time. The sound is pretty noticeable. This is so only when I boot with the Ubuntu 16.10 installed  in this computer's hard drive. The fan does not make however almost any sound when the computer gets booted from a live distribution of wifislax installed in a USB pendrive. And I said "almost" because when the computer has much work to do, for example several windows opened at the same time in the internet broswer, then the fan gets on for a while.

But as I said, with Ubuntu 16.10 the fan is alway on as if there were processes running the whole time even if no application gets launched manually by the user after booting.

Moreover, I have also seen that the same wireless Internet connection with the same computer's wifi adapter is much slower in Ubuntu 16.10 for streaming videos or just pulling a website open than with the live Wifislax. I also reported that problem in the corresponding Networking section of this forum though.

The only thing, that I can come out with as far as performance is concerned, is that may be the live Wifislax is not so heavy for the computer and may be the computer is old enough so that it needs a light weight operative system. But I am not sure whether this is the real cause for this problem.

Thanks for your ideas.

---

### Post by dragonfly41 on 2016-11-27
I followed the notes in this blog to install i8kmon on my old Dell laptop (Ubuntu 14.04) which has fans running full whack.

[http://thesmallsecurity.weebly.com/linux/install-and-configure-i8kmon-for-configurable-automatic-fan-speed-control](http://thesmallsecurity.weebly.com/linux/install-and-configure-i8kmon-for-configurable-automatic-fan-speed-control)

If you are using Chromium Web Browser with many tabs open you can see in System Monitor > Processes that this consumes memory and kicks the fan.

It may be that you are short on memory.   Monitor your running processes/memory using System Monitor.
Or I use Docky which has an enabled docklet - Computer Monitor - which shows Cpu and Mem usage at any time.

---

### Post by thosecars822 on 2016-11-27
> **dragonfly41 said:**
> I followed the notes in this blog to install i8kmon on my old Dell laptop (Ubuntu 14.04) which has fans running full whack.

[http://thesmallsecurity.weebly.com/linux/install-and-configure-i8kmon-for-configurable-automatic-fan-speed-control](http://thesmallsecurity.weebly.com/linux/install-and-configure-i8kmon-for-configurable-automatic-fan-speed-control)

If you are using Chromium Web Browser with many tabs open you can see in System Monitor > Processes that this consumes memory and kicks the fan.

It may be that you are short on memory.   Monitor your running processes/memory using System Monitor.
Or I use Docky which has an enabled docklet - Computer Monitor - which shows Cpu and Mem usage at any time.
1. My computer is an HP laptop. That is to say, it is not a Dell laptop.
2. The fan is on all the time even if I do not open any application after booting.
3. I have 1GB ram memory acording to the application called "top".

---

### Post by dragonfly41 on 2016-11-27
You will find a score of possible factors to investigate if you dig further.


update bios in laptop - [http://support.hp.com/us-en/document/c00042629](http://support.hp.com/us-en/document/c00042629)
check running processes - [http://support.hp.com/us-en/document/c01007591](http://support.hp.com/us-en/document/c01007591)
check air flow
clean out dust from vents
overheating - [http://askubuntu.com/questions/400942/overheating-laptop-hp-pavilion-g6-with-amd-8-ubuntu-13-04](http://askubuntu.com/questions/400942/overheating-laptop-hp-pavilion-g6-with-amd-8-ubuntu-13-04)
check drivers - [http://askubuntu.com/questions/207733/why-does-my-laptop-with-amd-radeon-hd-76xx-graphics-get-overheated-when-using-ub](http://askubuntu.com/questions/207733/why-does-my-laptop-with-amd-radeon-hd-76xx-graphics-get-overheated-when-using-ub)


[http://askubuntu.com/posts/207733/revisions](http://askubuntu.com/posts/207733/revisions)


Just keep searching and experimenting.

But I do think that 1GB ram memory is too low.

---

### Post by thosecars822 on 2016-11-28
Hello

I just found this problem might have to do with these threads' problem because my gpu is amd as well:

[URL="http://forumubuntusoftware.info/viewtopic.php?f=45&t=9074"]http://forumubuntusoftware.info/viewtopic.php?f=45&t=9074
[/URL]
[http://askubuntu.com/questions/815591/ubuntu-14-04-5-16-04-16-10-and-amd-graphics](http://askubuntu.com/questions/815591/ubuntu-14-04-5-16-04-16-10-and-amd-graphics)


lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS482M [Mobility Radeon Xpress 200]


Would you suggest to look for and download drivers from

[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)
  
 for my GPU? What driver do you recommend? It would be great if you could post a link to a driver for this gpu that would fix this problem.

Thanks

---

