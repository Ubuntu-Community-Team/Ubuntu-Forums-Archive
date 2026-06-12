---
title: "Feisty + torrents = Oops!"
date: 2007-05-07
forum: General Help
---

### Post by strixy on 2007-05-07
My wife has an interesting problem with her computer.

After about 6 months, her Internet stopped working. I tried fixing her Windows system but what do I really know about Windows? I could get it to work for a period of maybe an hour or three. I don't know... I did something different every time. There wasn't anything consistent about what I did or how the internet came "unstuck". I blamed it on Windows and tried for weeks to get her to switch to Linux.

Finally, I got her using Linux, Ubuntu's Feisty Fawn. (big victory, let me tell you!)

So far she loves it! In fact, she's wishing she could use Linux at work too. Wicked!

The only problem is that even under Feisty the same problem happens - still.

I hack at the problem, it crashes... I try again, it crashes... I get it working and it crashes again. Every time, I try something differnet so It's not like I can just repeat what I did last time to get it working. 

We finally figured out that it's a problem relating to torrents. For example, she ran without downloading any torrents for 3 days. About an hour after she ran Ktorrent, her internet went kaput and her computer is now slower than molasses in a Canadian winter (We're now in Spring). Example, I can count 60+ seconds to open a terminal.

I keep tweaking things and eventually it comes back on. The problem is, every time it goes down I spend an hour researching the problem, trying that fix and then rebooting her computer. That doesn't work, so I reset her computer back to where it was before and then start all over again at the researching for an hour part.

Well, I'm stumped. I'm asking the community here, what's going on and how can I fix it?

OPI (Other Pertinent Information): None of the other computers on the network are affected. Her Windows is still fubared - like I care to try and fix it (dual hard drives, 1x IDE for WinXP, 1x SATA for Feisty). The last time I got it working I turned off ACPI 2.0 support on the MoBo (Asus A8N-VM-CSM). As per advice on the ASUS web page. I tried disabling ACPI entirely. (maybe turning it back on ?? silly ;) But that's the kind of story I have been seeing with this computer. It might be hardware related as it happens in WinXP and Linux. 

What else have I tried??... um, I thought it was the on board network card (Nvidia drivers required, craptastic!) I once got her computer to work fine when I disabled the on board network card, But then there is definately no Internet! (HA!) So I tried to install a new network card, woah, was that a horrid waste of a weekend! Alas, no Internet and the problem continued. I doubt it's the network card.

I don't know... I've been hacking away at this for weeks now. Any suggestions, questions  or advice?

Once I get it to work, it will stay working just fine - until she tries to download a torrent.

:confused:

---

### Post by Happy_Man on 2007-05-07
Perhaps there is something wrong with your internet connection at the ISP end? Some ISPs like to kill internet when they detect torrents. And also, what is your computer's RAM?

---

### Post by strixy on 2007-05-07
I'll check with my ISP. The computer has 1 Gig of ram.

Of course, the Internet works fine for all the other computers running on the network here. If it was the ISP, wouldn't their influence mess with the other computers as well? None of them are downloading torrents... If it was the ISP, then I don't think there would be such a massive hit to the system responsiveness. (it's super sluggish).

PS. love your sig.

---

### Post by orb9220 on 2007-05-08
> Some ISPs like to kill internet when they detect torrents.

True

Also there is a new ktorrent version which fixes the ktorrent crashing all the time.
The current release is 2.1.4  [http://ktorrent.org/](http://ktorrent.org/)

---

### Post by strixy on 2007-05-08
Nope, that didn't help.

This may be a hardware issue?

---

### Post by Jaza on 2007-05-09
I had some small torrent problems in previous releases when using default torrent application (Bittorrent).
It used too much cpu power when i had more than 2 torrents open, and was fixed by installing other torrent program Transmission, but i think you could try out Deluge too (Azureus uses too much memory). =)

---

### Post by kd7swh on 2007-05-09
you could use top or htop to see what processes are using the most ram. make sure that after ktorrent is closed that it is no longer using ram (running in the background). Torrents have really killed my computers too. Try different clients and see what works. Freeloader is a simple downloader that I keep on hand. Also, if you are using a router it might be worth checking to make sure that it is not affected by the traffic. Sometimes those torrents do strange things to my router too.

---

### Post by strixy on 2007-05-09
> you could use top or htop to see what processes are using the most ram.

That's a good idea. Although I have completely removed / uninstalled ktorrent and rebooted the box, would / could there still be an issue? I'll check anyway when I get home to make sure.

> ... was fixed by installing other torrent program Transmission,

I'll give Transmission a try, but I have to get the Internet working first. This problem occurs in Windows as well as Linux, though I don't know what she was using as her torrent manager.

> if you are using a router it might be worth checking to make sure that it is not affected by the traffic.

I've tried plugging this computer directly into the cable modem (bypassing the router and switch) and the issue persisted. I've also bypassed the switch and used only the router... I've swapped out the cables for new ones. Changed ports, DMZ hosts, DNS config, port forwarding, etc... changed the network card... Nothing in those settings have changed in the last 9 months and this computer was working fine up until about a month ago with no changes to the router settings. Maybe it's just time for a new router? It is 7 years old. Couold this be a sign that it's going belly up? Even if the other computers running off of it are still running fine?

I've tried disconnecting the other computers, but that didn't help and the other computers couldn't get any internet either! (ok... that was a bad joke ;)  )

---

### Post by strixy on 2007-05-09
I think I got it.

Following Fragos' advice in another post, I completely powered down the computer - right down to the power bar - and it's working. I don't know for how long, but I'll do some testing to see if it works again. OoOoOooo the fun part = now I get to TRY and break my wifes computer on purpose! he he he...

Fragos post: [http://ubuntuforums.org/showthread.php?t=433426](http://ubuntuforums.org/showthread.php?t=433426)

---

### Post by QwUo173Hy on 2007-05-14
For anyone else who is having similar problems; I used to get disconnected some time after boot up and wouldn't be able to get on again - even with a reboot!

I turned out that unplugging the router for 30 seconds did the trick every time. Then I just had to issue
> sudo ifdown wlan0
sudo ifup wlan0

to get reconnected.

From the linux side, if I keep my torrent downloads under 30Kb/s I'm okay. I also need to keep uploads under 3Kb/s or the internet slows down for everyone else. I have a wireless connection.

---

### Post by strixy on 2007-05-16
Everything seems to be working fine. Powering down did the trick. Avoiding ktorrent completely has kept the problem from popping up again.

I'm currently trying to get Azureus to work.

---

### Post by jallain on 2007-05-17
I want to add my experience. I too installed ktorrent and started to download some files. It took me a few days to figure out how to get the speed up to something beyond 20-30kbps. This means that I did not shut down and reboot every morning. By the fourth or fifth day, I was downlading at over 130 kbps; however, my computer was completely filled with molasses. I never lost my internet like the original poster, but it would take over a minute just to open a command window. I tried to open virutal box and it plain would not load. My download however would keep rolling right along at a decent speed. What is strange is that this sluggishness seems to have infected my machine after I started downloading torrrents. Before that, it was fine. Does this make sense to anyone? Is this related to torrents or is it because my machine was left up longer than five days without a reboot?

---

### Post by strixy on 2007-05-18
> Is this related to torrents or is it because my machine was left up longer than five days without a reboot?

No. I had the same experience. Once I uninstalled ktorrent and powered down my computer went back to normal.

---

