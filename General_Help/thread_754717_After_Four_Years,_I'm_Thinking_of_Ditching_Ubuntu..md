---
title: "After Four Years, I'm Thinking of Ditching Ubuntu..."
date: 2008-04-14
forum: General Help
---

### Post by talkingwires on 2008-04-14
So after dual-booting Linux for four years and then booting Ubuntu exclusively for four, I'm thinking of jumping ship. Why? A number of reasons, the biggest being that suspend/resume [do not work on my laptop]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34155") (a two-year old confirmed bug), which basically turns it into a tiny desktop. I could type up a whole list, but it basically boils down to a bunch of little quirks and frustrations that have built up over time. Maybe I'm getting tired of babysitting my OS.

So, I wiped my HDD and installed XP, and was kind of surprised  at what I found: the UI was snappy, Winamp is even better than I remembered, and Firefox flies. I had forgotten about the transparency effects and drop shadows, too, which are nice since the developers have blacklisted the open-source ATI drivers in Hardy. Even with the required AV and firewall software running the background, everything was much more responsive than my Hardy installation every was. Plus, being able play games without jumping through hoops was nice. :)

There is just one problem, and it is kind of a deal-breaker: my wireless card (Intel 2200) runs horribly in Windows. I can barely get a signal from my neighbor's router (he knows I'm borrowing his connection:)), and using the Internet just isn't possible. But it works flawlessly in Ubuntu and the signal strength is good. This might be related to Ubuntu ignoring the fact that I only have one of the two antenna wires connected.

So I guess I have two questions. First, does anybody that has experience with the Intel 2200 wireless cards have any tips for getting it to function properly in Windows? Of course, answering that question means I'll jump ship to Windows on my laptop, but my desktop will remain a Linux system. :) Second, does anybody know, for certain, of a Linux distro that works on a Dell C640?

Bonus Round - Get suspend/resume working with a Dell C640, and I'll stay. :)

[Mods: I couldn't figure out how to classify this post. Is it "Other OSes"? Is it a "Testimonial"? "General Help"? Sorry if I posted in the wrong forum...]

---

### Post by colo on 2008-04-14
I don't like the somewhat "blakcmailing" style of the post, but if you don't tell HOW EXACTLY suspend/resume fails for you, there's not much chance for any of us to help you.

---

### Post by Sef on 2008-04-14
The problem with suspend/resume goes back to the BIOS being proprietary.

General Help is fine since you are using Ubuntu.

Read [this blog]("http://untitledfinale.wordpress.com/2007/10/22/update-ieee-80211-and-ipw2200-on-ubuntu-gutsy/").

If that doesn't help, check out [these links by google]("http://www.google.com/search?q=Intel%202200%20wireless%20card%20and%20Ubuntu").

---

### Post by trippinnik on 2008-04-14
I don't know about that particular laptop, but since gutsy suspend fails on my IBM X22.  Since then I tested with a few different distros and had good luck with Mint and Debian 4.0 (it's got debian 4 now).  It is unfortunate that suspend keeps breaking with new releases of Ubuntu though. I'd like to see things that work stay working ...

---

### Post by GCoffee on 2008-04-14
Ah yes, Suspend.... I can't get it working on my desktop pc either.:(  It just hangs on a black screen so i have to turn off the power at the wall.

A annoying bug but I wouldn't remove ubuntu just for that. I highly prefer ubuntu without suspend than XP with it.

---

### Post by klybear on 2008-04-14
> **talkingwires said:**
> There is just one problem, and it is kind of a deal-breaker: my wireless card (Intel 2200) runs horribly in Windows. I can barely get a signal from my neighbor's router (he knows I'm borrowing his connection:)), and using the Internet just isn't possible. But it works flawlessly in Ubuntu and the signal strength is good. This might be related to Ubuntu ignoring the fact that I only have one of the two antenna wires connected.

I don't know, but I have the same thing here. I can get a lot better reception using Ubuntu than I ever did with XP. Coincidently, I had the same excellent reception with Fedora. I was wondering if the Linux drivers for Intel dapaters are more efficient?

That's the sad thing. There is no perfect OS. I loved the boot speed of Fedora, but I never really got used to the RPM system. I really liked the Free Philosophy of Debian, but I really need Ubuntu's restricted drivers.

---

### Post by HunterThomson on 2008-04-14
Ya, what is with the updates braking things all the time???

I installed Hardy and GRATE the desktop effects work!!!! Update broken........
I installed Hardy and GRATE Suspend works!!!! Update broken........

But back to your post. I agree I have hard grate things about Mint. As for window$... I just spent all day trying to get rid of viruses on a friends computer and it is 11:30pm work tomorrow and still running anti-virus programs.... Almost fixed.... I can boot into window$ now and not just safe mode. If your going back to window$..... Make sure to get COMODO Firewall and don't forget that window$ just troughs things all over the hard drive so defrag once a week... we will see you back in a month or two:lolflag: Every OS needs at lest a little babysitting but window$ needs life support.:lolflag:

---

### Post by Tews on 2008-04-14
Sorry about your problems ... have a nice day .

---

### Post by vanadium on 2008-04-14
Your wireless story confirms my experience: wireless worked so much better for me when I switched to Ubuntu. My wireless controller is  Intel Corporation PRO/Wireless 2200BG.

I am in the belief that hibernate not working is mostly an ATI issue. It worked somewhat in Ubuntu 7.4, and the alternative approach, uswsusp, worked well although it is not very fast. No way of hibernating worked anymore with the current Gutsy, and I was silently hoping that things would get better again in Hardy.

---

### Post by talkingwires on 2008-04-14
> **colo said:**
> I don't like the somewhat "blakcmailing" style of the post, but if you don't tell HOW EXACTLY suspend/resume fails for you, there's not much chance for any of us to help you.I don't really get what you mean by "blakcmailing"[sic], but if you had bothered to click the [link to the Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34155") in the original post, you would see exactly how suspend/resume fails. It's a real great read, with several people trying different approaches to narrowing it down. Towards the end of the report, you can see where I suggest that it's kernel/ACPI bug and not related to the ATI drivers at all.> **Sef said:**
> Read [this blog]("http://untitledfinale.wordpress.com/2007/10/22/update-ieee-80211-and-ipw2200-on-ubuntu-gutsy/").

If that doesn't help, check out [these links by google]("http://www.google.com/search?q=Intel%202200%20wireless%20card%20and%20Ubuntu").The 2200 works great in Ubuntu. I was writing about a Windows problem.

> **GCoffee said:**
> Ah yes, Suspend.... I can't get it working on my desktop pc either.:(  It just hangs on a black screen so i have to turn off the power at the wall.

A annoying bug but I wouldn't remove ubuntu just for that. I highly prefer ubuntu without suspend than XP with it.I still use Ubuntu on my desktop. But if I'm going to lug a laptop around, I'd like to be able to pop it open and look something up real quick without waiting a minute for it to boot. Plus, my laptop runs very hot since I had disable the powersaving features, which led to it overheating one night. When I got to it the next morning, the fans where in overdrive and the keyboard had actually been damaged by the heat ([there is a bug report on this]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/95537")). The only application I had running was Firefox with three tabs. This can't continue.

---

### Post by konungursvia on 2008-04-19
I agree with the austrian guy that your style is very pointed and pressures good ubuntu people to help. However, I'd say this: hardy beta is the wrong place to jump ship from. It's a LTS release, so you can count on its community doing a hell of a lot to solve all issues. It isn't even out yet, give it a chance. I boot windows too, but only for Warcraft (slow in wine) and Kyodai Mahjong (won't even run in wine).

---

### Post by ./. on 2008-04-19
Ironically, I could never get Suspend / Resume to work on my Windows machine.  Perhaps it was just the combination of hardware, but it always left me a black screen that never resumed from suspend.

Given the choice of paying for broken software or having broken software at no cost, I'd take the latter option ;)

---

### Post by eldragon on 2008-04-19
this is the first jumping back to windows kind of post that didnt sound like a threat to me. it seems reasonable that after years of waiting and filing bug supports (or adding some insight to existing ones) someone would want to give up on it. i would.

my resume / suspend works with some glitches too. (once i get back from resume, ctrl-alt-f1~f6 give a white dead screen), but i hardly use the feature. (resume suspend)

wireless, its a first timer that it works better on ubuntu than windows. its usually the other way. good to hear that. i still get a hard lock after 100megs wireless xfer if using some kind of encryption. but thats ralink. i decided to do all my xfers through ssh and get on with my life :D

about speed. you might have a point there. somewhere in the way, gtk got slow. there should be a way to dumb the tooklit down to make it more resource friendly. (it takes 30secs to get to the login screen, and 2minutes to get a working desktop here).

anyway, every os will have issues. its just what you are willing to put up with what will make you keep one and ditch the other. 
id rather have to load the wireless network every time i turn the notebook on, or live without suspend/resume than to deal with all the glitches ms or apple brings. (im a privacy, free rights manifestator). i hate wga, drm, and every form of access restriction that restricted software sets upon me. 

have a nice day.

---

### Post by Eisenwinter on 2008-04-19
> **talkingwires said:**
> Bonus Round - Get suspend/resume working with a Dell C640, and I'll stay. :)
Just because you said that, I think you should move back to Windows.

---

