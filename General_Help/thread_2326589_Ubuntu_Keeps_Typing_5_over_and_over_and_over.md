---
title: "Ubuntu Keeps Typing 5 over and over and over"
date: 2016-06-02
forum: General Help
---

### Post by SkOrPn on 2016-06-02
Hello,

I tried searching for this topic, but it seems many people have similar issues, but with different keys, and some people use multiple letters and or numbers to represent their issue, so trying to use a search feature to find something that can be worded in a thousand different ways is near impossible.

My problem is every time I log in my new cleanly installed 16.04 install starts typing the number 5 the very moment any input screen pops up. ANYTHING that you can type into immediately starts typing a 55555555555555555555555555555555........... and it doesn't stop typing 5 until I hit the back key. VERY annoying, and it seems to only occur after resuming from suspend, but I have not had this build up and running for long, so not sure exactly whats going on. I left Windows 10 on Friday, and then on Saturday morning downloaded and installed Ubuntu 16.04 server (I needed the extra partitioning features so I could do a proper raid setup) and then immediately installed ubuntu-desktop and using it just like a desktop.

Anyone know what causes the untouched keyboard to start typing rapidly for no reason? After stopping the insanity of rapidly repeating 5's it does not occur again until after I log back in, at least that is how it seems to me so far.

Any idea what causes this? Just a bug on the new Ubuntu maybe? :confused:

---

### Post by QIII on 2016-06-02
Hello!

If it were a bug, all of us using 16.04 would be posting the same question.

The first thing to do, although it may sound silly, is to eliminate a hardware issue by using a different keyboard to see if the behavior continues.

---

### Post by vasa1 on 2016-06-02
Logitech keyboard?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1580732](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1580732)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579190)

---

### Post by QIII on 2016-06-02
Nice catch, vasa1!

---

### Post by SkOrPn on 2016-06-02
> **QIII said:**
> Hello!

If it were a bug, all of us using 16.04 would be posting the same question.

The first thing to do, although it may sound silly, is to eliminate a hardware issue by using a different keyboard to see if the behavior continues.

Bud you been busted. I have 30+ years of IT experience under my belt with some of the worlds most advanced companies so please don't spread that BS with me. I would fire my IT interns if they spoke stupid nonsense like that.

Bugs almost always affect a small minority of users, so NO, not everyone would have the same bug, that is NOT how bugs "generally" work in the world of computing. Sure, it is sometimes true that some very rare bugs get by and are massive enough to affect nearly a 1/3rd or maybe even half of all users but that is so extremely rare because bugs of that magnitude are ALWAYS found during beta testing.... ALWAYS, simply because your talking about a bug that affects nearly everyone, thus can't get by the beta teams in the first place. I've seen bugs on seemingly identical setups affect one computer and NOT the other. And if it did work like you claim, lol which is 100% false, this world would be in utter severe Computing Chaos, until a near perfect OS was released with zero issues. Bugs in code usually only affect certain hardware/software configurations in a small minority of systems. 99% of the time, especially with major companies such as Logitech, hardware is tested on many different systems and the hardware released with firmware that has been certified on many platforms. With literally hundreds of millions of different hardware configurations world wide, a little known bug could affect my particular setup on my computer and not affect yours because your not using the exact same hardware+software setup I am. **And further If it were a hardware issue, the issue would continue on "permanently regardless of the OS used".**

However, It is not happening in elementary OS Freya (just tested), it is not happening in my Windows 10 (just tested), and it is not happening in my Ubuntu MATE 14.04 (just tested), and it is not happening in the latest Fedora distro either (just tested). AND, It's NOT happening on any of my VM guest systems (I just tested Windows 10 build 14352 Preview and nope not happening there either). When I physically switch this keyboard (new logitech K800) over to another machine entirely (only tested on my laptop so far), running a different OS (elementary OS freya) it is not happening there either. Definitely not hardware related, that is absolutely obvious. And this K800 is a well known high quality keyboard with hundreds of thousands of units sold worldwide.

**It is only happening on THIS Ubuntu 16.04 install**, but not on any other OS. Hardware bugs would happen regardless of the OS being used. I been using Linux since the mid 1990's and can't remember this ever happening before this week.

No, It obviously has something to do with the way Ubuntu is waking up from suspend and thus causing the underlying keyboard input drivers to start typing the number 5 and probably only on systems with my particular keyboard model, or type of keyboard. Which is a BUG that would only affect people using this exact OS server setup, with this exact keyboard, and my exact kernel.

I wonder if it's happening on normal Ubuntu 16.04 LTS or only on this Server install? I will test the other keyboard to see.

This did NOT happen in Ubuntu MATE 16.04 either (which I still have installed in VM for testing purposes), so maybe the new kernel 4.4.0.22 Ubuntu update installed a few days ago introduced the issue? I will switch the keyboard to my old Logitech diNovo to see if it still occurs. If it does, I will boot to the older kernel and see if it happens there too.

Anyone else with a wireless Logitech keyboard see this issue yet? Testing my diNovo now.

Thanks

EDIT: Read below a weird discovery.

---

### Post by SkOrPn on 2016-06-02
OK

Just discovered that my Ubuntu system is somehow damaged with keyboard/mouse input. Just tried THREE different keyboards and two different mice (all wireless types), and only the K800 and my Performance MX combo is working (yes the one I get the 5555555555's on). All the other input devices (including my $200 diNovo) isn't even being detected by this newly clean Ubuntu install. My diNovo has NEVER failed on all the hundreds of systems its been attached too in the past.

So something is broken in the new Ubuntu. Any ideas?

I am a Windows IT guy working for the Federal Government, so I do not have much deep Linux experience although I have used it on and off for 20 years (just for the faster browser experience mostly), I never really got serious with Linux until this year thanks to my employer requiring only Microsoft products to be installed on our machines (IT users do not have a say in what systems are used at their work environment). However, I personally hate the direction Microsoft is taking with Windows 10 (don't we all?) so that is why I am adopting Linux 24/7 here at my home. Any help from a "real" Linux guru would be much appreciated. I'm sure it could be fixed in the terminal so I will do some research myself. Maybe I just need dedicated software for this wireless keyboard? Maybe I should go find a old wired keyboard too and test that. I don't ever use wired keyboards on my personal computers and haven't in over 10 years, so it could be an issue with wireless only probably.

Will test a wired kb and report back.

Thanks

---

### Post by SkOrPn on 2016-06-02
OK, just had my Dell supplier loan me a brand new fresh out of the box usb wired keyboard meant for Dell Workstations, and it did NOT type 5's after the first resume test. However, I need to use it for a few days I guess to be sure. Going to suspend several times today to see what happens.

Looks like my Ubuntu wireless drivers are the culprit, or I failed to install something needed for the new wireless Logitech keyboards. Guess my next step is to see if I can refresh the wireless keyboard drivers my K800 uses?

Oh well, a bunch of repeated 5's isn't too much of a deal breaker, at least the backspace key stops it from occurring. Haha

---

### Post by QIII on 2016-06-02
When you have as many years in as me, you may feel welcome to discharge me.  Until then, it would probably be safe to avoid antagonizing the Staff.

Tip:  teach your interns to rule out hardware first.  Troubleshooting 101.

Then take the time to look on launchpad.

---

### Post by mc4man on 2016-06-02
try the 4.6+ kernel as outlined in either of those 2 listed bugs (now just one as I duped the other

---

