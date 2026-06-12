---
title: "Upgrading Weirdness"
date: 2015-09-26
forum: General Help
---

### Post by arsenic-creed on 2015-09-26
Okay, so I'm terrible at asking for help for anything from anyone ever and dreadful at being concise so bear with me for a minute. 
I've just gotten a new computer. I currently have my previous computer and the new one hooked up to the same monitor, keyboard, and mouse via a KVM switch. That's working fine now. I installed Ubuntu on the new computer via an USB because it didn't already have an operating system. With me so far?
The USB was for 14.04 or thereabouts so I upgraded to 14.10. After the computer restarted itself (I don't know if it had run through then, I'm afraid, because I went away to make dinner while it was going) it booted up fine and the resolution was set for my monitor (it hadn't been previously) but when I tried to run the updater it said there was a problem and suggested partial upgrade (said something about an upgrade failing?) so I hit the partial upgrade button and it ran for a little bit and then logged me out. I logged back in, it ran like it'd never started. It did that about three times before it stopped trying to upgrade. Now I can't open the software updater, the system monitor, or the update settings thingy I can't remember the name of and I'm not sure what to do now.
I'd like to get up to 15.04 but I don't know what to do. 
I actually just checked to see if it'd tell me what I'm at now and I can't open the system info from the top bar either.
Oh dear.

---

### Post by arsenic-creed on 2015-09-26
I can't restart it through the OS either. I have to hard restart or terminal restart if anything. Clicking shut down brings up the option but neither shutdown nor restart do anything.
EDIT: Forget terminal restart, can't open a terminal either. This is quite unpleasant.

---

### Post by arsenic-creed on 2015-09-26
Well, I just hard restarted because it was the only way to restart and it won't boot at all now so I guess it was super broken. Good thing I didn't have anything on there yet, huh? 
Guess I'll be reinstalling (and staying right here during the upgrade).

---

### Post by Mike_Walsh on 2015-09-26
Mm. Sounds like an re-install is about your best option.

It takes many people quite a while to get used to just how fast the 'buntu family installs are. By the time they're up & running, Windows has managed to slog its way through the partitioning, and is getting ready to inform you that it can't continue because it can't find a network driver..! 

I well remember an XP Pro install from a few years ago. It was, quite literally, **painfully** slow. Cringe-worthy. 47 minutes to format a brand-new, 500 GB Sata HDD. Paint **dried** faster...

I've never yet had a 'buntu-family install take any more than 27 minutes. Honest Injun.

In all honesty, with the speed and simplicity of 'buntu installs, it's often far simpler to 're-do' from scratch than it is to mess around trying to fix problems that crop up, often one compounded upon another...

Yep, it's a good idea to keep an eye on things. It starts slow, but things happen fast toward the end!


Regards,

Mike. ;)

---

### Post by arsenic-creed on 2015-09-26
Yeah, I'm going to reformat the USB and try using unetbootin or however it's called outside of package managers and seeing if I can get 15.04 on using that instead of start disk creator like I was before. I just did 14.04 earlier because start disk creator kept giving me a 'cannot install bootloader' error.

---

### Post by Mike_Walsh on 2015-09-26
Apparently, 'Start Disk Creator' has had a bug for years that would never allow it to finish what it started. I, too, have never been able to make it work; not for lack of trying!

On the other hand, I have always been successful with UNetbootin, on the occasions where a USB flash drive was simply more practical than a CD/DVD. As in 'non-existent'.....

A couple of other options you could explore are [PenDrive Linux]("http://www.pendrivelinux.com/"), and [MultiSystem]("http://liveusb.info/dotclear/"). Both of these work equally as well.  You'll need to translate from the French for MultiSystem, but it's a brilliant solution for some 'awkward' distros. I used it install Zorin OS a while back; it's what the Zorin Forums recommend.

sudodus currently has a thread running in the 'Ubuntu, Linux & OS Chat' sub-forum about this very subject:-

[http://ubuntuforums.org/showthread.php?t=2291946](http://ubuntuforums.org/showthread.php?t=2291946)


Regards,

Mike. ;)

---

### Post by grahammechanical on 2015-09-26
There is something that you have not been informed of and you do need to know it.

You installed Ubuntu 14.04 LTS, which is supported until April 2019 and that was working fine. Then you upgraded to Ubuntu 14.10 which has by now reached the end of its support period. That is why Software Updater hit a problem. Each version has its own software repositories and when a version reaches end of life those repositories are closed. There will be no more updates to that version. Also, at some future point in time the repositories are relocated. So, all the URLs to the servers then become inaccurate.

When you reinstall do it with Ubuntu 14.04.3 and leave the default setting as to be notified of the next LTS release. Then when 16.04 is released at the end of April 2016 the OS will offer you an option to upgrade. Oh, by the way, a partial upgrade will not upgrade us to the next version. 

Regards.

---

### Post by Mike_Walsh on 2015-09-26
That's very good advice from Graham.

Practical, as always. Where would we be without him? :)

And quite correct, of course; that hadn't even occurred to me. Graham has a **wee** bit more experience with Ubuntu than I do, you can tell... ;)


Mike.

---

### Post by arsenic-creed on 2015-09-26
I hadn't heard about that bug or I'd have tried unetbootin to begin with.
I had set the software sources to notify me of any update at all before I started it but I thought I could just upgrade through the distributions, didn't occur to me that it being at the end of it's support series would mean I couldn't use it as a stepping stone up to 15.04. I'll have to remember that. Thank you both.

---

### Post by arsenic-creed on 2015-09-26
15.04 went onto the USB fine and installed fine but now my screen resolution is wrong again and it won't let me fix it. It should be 16:9 but the highest I can set it in the display settings is 4:3. It was like that on 14.04 too but then fixed itself on 14.10.

---

### Post by arsenic-creed on 2015-09-26
Ah! Nevermind, I just had to switch the drivers and restart.

---

### Post by Mike_Walsh on 2015-09-27
Glad to hear it worked out. It's surprising how often it's the **little** things that catch you napping...

I've been using these things for almost 35 years; you get complacent after a while, especially when you've not had any problems.....and everything's behaving itself. Which **is** what they're **supposed** to do...

But, this being Linux..... Nah, I shouldn't complain. It's a computer. Doesn't matter what O/S it runs, something'll go wrong eventually. In that one respect, they're **all **the same..! :lol:


Regards,

Mike. ;)

---

