---
title: "Hardware Enablement Stack (LTS)"
date: 2015-01-09
forum: General Help
---

### Post by craig10x on 2015-01-09
Hi: I just installed 14.04.1 LTS and i know that 14.04.2 is supposed to be released on Feb 5th (according to the schedule)...At that point, how would you get the 14.04.2 HWE (Hardware Enablement Stack)?

1) I have heard that you don't automatically get it in the software updater, and need to install it manually...How is that done?

2) Those who run LTS and have added HWE in the past (as each new incremental version of LTS comes out)...do you get automatic updates on the new kernel that is installed with HWE?

3) I understand that HWE installs both kernel and xorg stack...what does the xorg stack do?

Thanks in advance for all feedback...Hope you guys can help get me clarified on this... ;)

---

### Post by deadflowr on 2015-01-09
From here
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
Something like this
```
sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic
```

Yes, you'll get updates for the new kernel and the new X stack, until 14.04.5 is released, then you need to update again to whatever kernel and X stack 16.04 will be running.
(14.04, and 14.04.1 will get the full five years of support, but the point release stacks only run until the next lts comes out)

The new xorg stack installs a newer version of the xorg stack; Which include any number of things from bug fixes to newly supported devices, or better support for new devices.

Sidenote, if you do a fresh install of 14.04.2 when it comes out you will get the new stuff automagically.

---

### Post by mc4man on 2015-01-09
I would also suggest that smooth sailing with mesa upgrades isn't 100% assured so best to read the terminal output carefully, both before agreeing & then again after the upgrades.

---

### Post by craig10x on 2015-01-09
Thank you very much, deadflowr...so helpful as always ;)
And mc4man as well...if anyone else has an pointers or tips...feel free to post...Thanks :D

---

### Post by Bashing-om on 2015-01-09
craig10x; My 2 cents worth.

If it ain't broke, why fix it ? .. What is broke that you desire to go to the newer kernels and Xserver ? .. That is not always a good thing to do.
Maybe another level of complexity when in times of trouble.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by craig10x on 2015-01-09
Bashing-om:  Actually, the 3.13 kernel causes multimedia instability problems for my hardware...early in the release of 14.04, some change was made to it that forever made it "cursed" on my hardware. Despite numerous updates after that, the problem continued, but all kernels since then (including 3.16) are rock solid on my system...So, i had upgraded to 14.10 and was running it for quite some time...

I came back to re-installing 14.04 now because i figured i would prefer to stay on an LTS to LTS cycle and figured that in a month's time i could get the 14.04.2 Hardware Enablement Stack which will give me the 3.16 kernel i need to make 14.04 stable...and then i'd do each new stack until the next LTS when i will do an upgrade then...I just figured less upgrading then going to each new version in between...

The instability i have is sometimes a little glitch when playing mp3s or watching you tube music videos for example and also, when listening to talk radio streaming, a word will get doubled, which is also annoying as heck...Other kernels do not have the problem...3.13 is bad for me, unfortunately...

So, yeah...it actually is a bit broke and i need to fix it ;)

---

### Post by Bashing-om on 2015-01-09
craig10x; Yepper.

Ya got cause ..

Fingers crossed that HWE does you good.
good things do happen

---

### Post by craig10x on 2015-01-09
True, that ;) :D
When does the new enablement stack usually become available?  before...after...or at time of: the point release of LTS?
When would you know when to run the command to get it?

---

### Post by deadflowr on 2015-01-09
For the original stacks on 14.04 I don't think you'd ever get a notification of the newer hwe.
At least I never got one for 12.04's original stacks...
And if like precise, you'd most likely only get a notification when that kernel stack went EOL; like the quantal,raring, and saucy stacks did.

That said I see packages in trusty's repos for linux-image-generic-lts-utopic and linux-generic-lts-utopic.
Also see xserver-xorg-core-lts-utopic, but 

I don't see xserver-xorg-lts-utopic or libgl1-mesa-glx-lts-utopic.

So I think the whole stack will be ready when the point release comes out, if not a little earlier.

---

### Post by craig10x on 2015-01-09
Thanks, deadflowr: Yeah, i checked that in the package manager and i see what you mean...ok...will figure on doing it around the time of the point release (maybe even wait a couple of days after)...Have you found (from past experience) that they go smoothly when you installed them?

---

### Post by deadflowr on 2015-01-09
For me, they went fine.
But they were on an old intel system; intel processor and intel gpu, super old.
Upgraded from the 12.04.1 stack (The 3.2 kernel and X) to the quantal stack (The 3.5 kernel and X)
Didn't need them, so there that point. (Things tend to work well when you don't *need* them to work well, I guess)

I had purged that system and did a reinstall; hard drive failure = new hard drive new system, etc etc.
So never did the upgrade mid-release; aka lts-saucy to lts-trusty, which I guess a few users had problems.

Safest way, with no worries, will always be a fresh download/install when the point release comes.
As always.

Edit:Ah ( I remember why I upgraded the hardware stack on that machine.
I have kworld pci-150u tv tuner card which didn't have support with the 3.2 kernel, but did have support for 3.5 and up(i think support came with 3.4)
Lucky happenstance, really, as the card was meant to be used only to transfer old vhs tapes via windows(Bought it before I was really into linux, and ran in a windows only machine for a while.). So added bonus when I saw the card got support.

---

### Post by craig10x on 2015-01-10
Thanks...When i did upgrade from one 6 month version to another, they went very smooth.  So, i was hoping that if i now go on an LTS to LTS cycle instead, that i will be able to add each stack as they become available with the point releases, so that i can run the newest kernel and stack until the next LTS arrives...My plan is to then upgrade into the next LTS, but will have a clean install iso of the next LTS just in case things do not go smoothly...

---

