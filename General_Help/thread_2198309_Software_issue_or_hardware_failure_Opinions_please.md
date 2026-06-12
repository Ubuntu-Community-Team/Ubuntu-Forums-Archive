---
title: "Software issue or hardware failure? Opinions please ..."
date: 2014-01-08
forum: General Help
---

### Post by Bucky Ball on 2014-01-08
Hi all,

Regarding my mother-in-law's desktop which I built for her some years ago. Started on Ubuntu 8.04 LTS>10.04 LTS and I installed Xubuntu 12.04 LTS from a USB drive at christmas (the optical drive no longer works). She's been happy as with it and is now more familiar with *buntu than Win (father-in-law is Mac only so no Win in the house).

The problems started three days ago. She booted and black screen with cursor blinking. I advised to hit ctrl+alt+F1, login, issue 'startxfce4'. This worked and got her to a desktop. All good. Still unsure why this strange behaviour at boot, but I'm 750Kms away so all I'm interested in is that she can get to a desktop and get on with it.

Last night it was panic stations. She lets me know the computer has pretty well locked up. Just talked to her on the phone and, while I could fiddle and it might be obvious if I was there, I am fairly bamboozled by this list of symptoms:

- Needs to login then 'startxfce4' to get to desktop (the initial problem).
- Next couldn't close/minimise windows;
- Couldn't open email from yahoo;
- On shut down, scrolling text and only way to switch off is hard shutdown;
- Internet stopped working;
- Click on a document in the home folder asks you to choose application to open with (was automatically opening files with the correct app previously);
- Reboot and takes her back to the same stuck clutter on the desktop with games and documents open and no way of closing/minimising.

I have suggested checking that the 'Save Session for future login' box isn't ticked on shutdown, but apart from that, I'm confused. My mother-in-law at first thought she had a virus (her original SMS last night). Guess she might have clicked on something as she has a lot going on with Firefox and emails, but she's managed to escape danger for the last five or so years. Perhaps her number was up.

I'm leaning toward hardware failure, perhaps graphics, but I could be off the money. Any advice for checking either theory or any new theories gratefully accepted. 

TIA ;)

PS: I will add that the machine was working faultlessly when I drove away on the morning of the 23/12/2013. We were well pleased with how Xubuntu was running and I was particularly happy with the way my mother-in-law had quickly adapted to xfce4 in place of Gnome.

PPS: As I say, the optical drive no longer works. I can't see how that would be bringing down the machine, though, but I'd like to be there to remove it.

---

### Post by Tony Flury on 2014-01-08
A virus on Linux is highly unlikely.
It could be a corrupt sector on a disk which has somehow "stomped" on some config files. It could be a bug deep in something which has decided to ignore settings. It could be a failed graphics card, or a driver. I don't think there is enough info to diagnose as yet.

I am sure someone with a lot of troubleshooting knowledge will come along and help. If you don't get a reply - maybe a thread with a more specific title will help - for instance - window manager not starting by default.

---

### Post by mark65ak on 2014-01-08
I would definately lean toward hardware failure, a corrupt file, or even a stuck key on the keyboard before a linux virus.  I won't say there are no viruses for linux but they are few and far between because you have to have root priveleges to install it.  Theoretically someone could trick you into installing some 3rd party software but even then it takes a level of skill to add repositories or install deb packages.  

Things to consider:  Unix and Linux are generally coded secure with the exception of a few dist that are coded for windows similarities  The exception here is Macintoch
Mac and Windows are coded as money makers far moreso coded for security.  Before Mac's caught a couple of widespread viruses Unix had a total of 5 viruses that never left the labs they were created in.   Linux has never had a widespread virus.   Windows has had then into the 100s of thousands.

---

### Post by Bucky Ball on 2014-01-08
I have changed the title of this thread as people seem to be veering down the wrong path. I do not want to get into the 'how secure is Linux' and can it get a virus/worm/trojan debate and don't need a lesson on that. I've heard it all. 

The only reason I mentioned virus at all is because that is what my mother-in-law jumped to. I am well aware they are as rare as hen's teeth and this being the cause is highly improbable, but clicking the wrong links or opening unsolicited emails can still cause issues and my mother-in-law having done something like that is not an impossibility.

End of debate and back on topic, please. 

As I clearly stated in the first post, I am leaning toward hardware failure. Software seems unlikely as she did nothing specific, it just happened after booting the machine to a desktop. Just wondering if anyone can recognise anything about the symptoms the machine has that might ring a bell as to what could be failing. Shot in the dark because it is going to be hard to get to the bottom of without being there.

---

### Post by coffeecat on 2014-01-08
> **Bucky Ball said:**
> 
I'm leaning toward hardware failure, perhaps graphics, but I could be off the money. Any advice for checking either theory or any new theories gratefully accepted. 

I'm sure you've thought of this, but get your mother-in-law to do a memtest from the grub menu.

I once - perhaps naively - believed that RAM was either OK or faulty from the time of manufacture. I had a stick go very wrong after about a year of satisfactory use, which taught me a thing or three. As did the fact that memtest threw up a mass of errors after a few seconds once I'd realised it could be the RAM that was causing the problems, but on another run it didn't complain at all even after an hour or so.

---

### Post by Bucky Ball on 2014-01-08
> **coffeecat said:**
> I'm sure you've thought of this, but get your mother-in-law to do a memtest from the grub menu.



I will add that to my list of things for her to try. RAM, of course! Why didn't I think of that? And these look like they might be the symptoms of a dodgy stick. 

About the oddity that she can switch the machine off (or restart) and the windows that were open on the desktop previously are still open. I've got my fingers crossed that she has the 'Save Session' ticked at shutdown. Unticking that might at least kill all the windows and create a bit of normality. 

The other idea was to killall apps in a terminal one by one. Is there a command to killall open apps at once?

---

### Post by tgalati4 on 2014-01-08
How old is the machine?  I would suspect the power supply over RAM.  Capacitors age and leak causing all sorts of problems.  Inspect the motherboard.  Oh, have your mother-in-law move in so she is not so far away.  Linux does allow you to get extra life out of old machines, but it does not solve the mother-in-law problem.

---

### Post by oldos2er on 2014-01-08
> **coffeecat said:**
> I'm sure you've thought of this, but get your mother-in-law to do a memtest from the grub menu.

I'd add a [SMART]("https://help.ubuntu.com/community/Smartmontools") check for any hard disks too.

---

### Post by Bucky Ball on 2014-01-08
> **tgalati4 said:**
> I would suspect the power supply over RAM. 

In any other machine I would jump straight there, but I have a thing about PSUs. I advise people when building or buying a laptop to take the generic silver box PSU out for a spare and put in a brand name, 80+ or 85+ PSU with lots of life and a ton of safety switches. This machine has an 80+ Antec Earthwatts 430W with enough safety switches to sink a battle ship and some ridiculous amount of life expectancy so I am really doubting that. Generally, the PSU sparks, pops, smokes and flames when it goes, taking out all or some other components with it. This PSU can't do that. It will switch off automagically at the first sign of trouble. ;)

For the moment I have asked her to shutdown and make sure 'Save Session' is unticked, remove all USB and other devices from the machine and plug the keyboard and mouse directly in, reboot and see what happens. Failing there, I am going to ask her to go for the memtest. Trying to rule out software, but I can't see software being the issue. Trying to get to a stable state so she can run 'sudo apt-get update/upgrade' which might go some way to ruling that out. 

Thanks for the input people. Mother-in-law rang before so ringing her back and will report on her progress ... if any. 

@tgalati4: Much as I love her, mother-in-law just fine where she is, thanks! Funny you should mention it as she's been trying to get us to move there as brother-in-law and two kids have just moved near her and so B-I-L, S-I-L and four grand kids are all now living in same town. That leaves us 750Kms away, but we're good with that. ;)

---

### Post by monkeybrain20122 on 2014-01-08
Saw this earlier [http://ubuntuforums.org/showthread.php?t=2198358](http://ubuntuforums.org/showthread.php?t=2198358)
Not as bad as what you described but some similarities?

---

### Post by Bucky Ball on 2014-01-09
> **monkeybrain20122 said:**
> Saw this earlier [http://ubuntuforums.org/showthread.php?t=2198358](http://ubuntuforums.org/showthread.php?t=2198358)


Similar. MIL was getting a blinking cursor so ctrl+alt+F1 to a CLI then 'startxfce4' as she is using Xubuntu. This appears to have been resolved now (see end of post).

This is what we tried:
- Unplugging all USB devices, ticking off 'Save Session' at logout, update and upgrade (fully done with no errors).

No different. 

When she clicks logout icon she is not getting the options to shutdown, restart, logout, etc., but one single box asking if want to log out, cursor turns to a cross and says shutting down in 30 seconds and the option to 'Quit'. If she hits quit error message saying saying she doesn't have permission.

Is this perhaps to do with an Nvidia graphics setting I wonder, or the graphics card packing up? 

There is also no grub menu at boot and no way of getting it up. I even guided her through editing /etc/default/grub so the menu would appear at boot and nothing. No difference. I thought perhaps she could run recovery and 'Fix broken packages'. Not a possibility, but we did it via a command line (when she boots she can get to a desktop but the open windows are still there and can be resized but not closed). No difference.

As we can't get to the menu at boot and run memtest, is there a way it can be run via a terminal? I'll have a dig round after ...

PS: She seems to lack permissions for everything except when she's in a terminal and 'sudo'. She can then, of course, put the password in manually. What has me really bamboozled is that my wife is using the same Xubuntu release (but diff hardware), and it is problem free. 

Which leads me back to the hardware ...

And also, is there a command she can stick in a terminal that will close all open windows? I have given her 'sudo killall aisleriot' to kill the card game windows which won't go away. 

PPS: She could only shutdown with the power button previously. I talked her through rebooting via a terminal and that is taking her to a regular login screen on reboot now, so that is a step forward I suppose. Despite this, no selection list. She has tried hitting shift at boot and the /etc/default/grub is correct. ;)

PPPS: Internet seems to be working, at least it was when I talked to her on the phone a couple of hours ago.

---

