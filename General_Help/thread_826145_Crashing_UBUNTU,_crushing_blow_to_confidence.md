---
title: "Crashing UBUNTU, crushing blow to confidence"
date: 2008-06-11
forum: General Help
---

### Post by mixtri on 2008-06-11
Hello guys!
I am starting a new thread here as i have previously posted problems before; piggy-backing other peoples threads that are similar in nature to mine but with no responses.

I recently reinstalled 7.10 after a few weeks using 8.04 (Hardy) due to hardy's incessant crashing. Here are the problems I had then which is now   occurring in 7.10 as well. It's driving me absolutely bonkers.

1. System crashes  - I'm logged out of a session and brought to the login screen where I have to log in again. All data and info in previous session is lost and I have to start again as if I was logging in for the first time. No pattern to this or reason that I can readily identify as it could happen whilst listening to music using rythmbox or exaile, surfing the net using firefox or just navigating the menu area attempting to carryout any mundane activity.

2. System Shuts down - This has happened 5 times today within the space of 3 hours. The most recent, midway through restarting the system from a previous unexpected shutdown.
Again no pattern to this behaviour. each time it happened I was doing something harmless as hitting the back button in firefox or navigating to another site. The other time i wasn't even doing anything; just reading an email.

3. Firefox Crashes - Firefox freezes and goes Grey sometimes for no apparent reason. Other times while navigating the web using hyper links on web pages. Again no pattern to this madness.

4. Firefox java applets freezes or doesn't load properly - This happened a lot in Hardy, not so much in 7.10 before the upgrade to 8.04. But now I'm back to 7.10 it happens all the time. I use chat sites that load java applets. It takes an average of ten tries to get it to function properly and when i do get it to load it freezes for ages before I am able to use it. So basically I cannot have more than one applet loaded at a time if and when i'm able to get the damned thing to work. 
This never used to happen as often as it does now, i can only attribute this to Java run time. Initially, I though it might be the newly released firefox 3, but no, it happens in firefox 2 as well.

All these issues are inherent in Hardy and Gutsy.
i can't count how many times I have scrubbed my HD and reinstalled the both 7.10 and 8.04 in an attempt to understand what is triggering this behaviour and why the same issues keep cropping up in both systems.

5. Streaming Audio/Video - I like to listen to music via the net but again this is a huge issue in both 7.10 & 8.04 with incessant crashing or freezing of firefox. 
I have followed a few how-to guides/instructions on the multimedia pages on this forum which seem to work for a short period but then the unpredictable behaviour reoccurs again. 
I've tried removing LibFlash support and Adobe flash 9 non free, installing flash 10 as per instructions on a thread i found on here to no avail.

At the moment, i feel like my PC is an alien to which I have no control over. I am spending time trying to avoid problems by not doing the things i would like to just so that i don't have to go through the problems ubuntu now regularly throws up on an hourly basis sometimes 3/4 times within the hour.

I'm seriously contemplating reinstalling windows on my system, literally weeks after expunging it from my pc, I really don't want to do that. As much as I dread going down that road, i feel it might be my only course of action or else I will become completely insane or do something as mad as throwing my PC out the front window into the path of a lorry or something.

This all happening at a time when I was beginning to feel comfortable using ubuntu. 

Can anyone help me please please please?

Are there others in a similar position thinking of going back to windows XP or looking for a more stable alternative Linux OS. please let me know. i really have just about had it with Ubuntu's weird behaviour.
I don' think its right that I should have to almost permanently be in a totally foul mood because of this. Not good for my health!! :mad:

All suggestions greatly welcome. Particularly about alternative Linux based systems that are stable and don't conspire to fill you with rage, sky rocketting blood pressure and the inevitable heart attack that could follow.

Ubuntu! you're about to be chucked big time!!

---

### Post by Het Irv on 2008-06-11
This is kinda weird, and while Ubuntu may be your problem, I am not convinced yet. You may have a hardware problem can you post your hardware specs, and what version of Ubuntu you are running (32 or 64 bit).  Also, is your computer running hot, the fans running louder, or anything like that?

I am thinking that you may have some hardware gone bad, because it did the same thing in both installs.

---

### Post by ladr0n on 2008-06-11
This might be a hardware issue.  What hardware are you using (and how old is it)?

Try running memtest 86+ from the grub menu.  That will help you diagnose RAM problems, at least (and your problems are symptomatic of bad RAM).

---

### Post by todak on 2008-06-11
Sounds to me like failing hardware (disk, memory, etc.) or overheating. Do  a memtest to check your memory. If it shows a lot of errors, bad memory is the culprit.

---

### Post by mixtri on 2008-06-11
Thanks for the speedy response Het Irv.

I'm a 32bit user. Cuurently using Gutsy 7.10

I do not think its got anything to do with hardware. As I have the same configuration settings as i did in Windows Nothing has changed.

Secondly I have had periods of relative stability using 7.10 prior to upgrading to 8.04 where everything worked fine, except of course the issues with firefox crashing which seems to be a known issue with ubuntu and definately no different from anybody else using Ubuntu. I know this from my research on this forum. A lot of other people seem to have the same issues. 

Here is a a few threads I read in an effort to fix this problem.
Admittedly since trying out one of the suggestions the problem seems to have increased in frequency. However the underlying issue remains the same

1. [http://ubuntuforums.org/showthread.php?t=816647](http://ubuntuforums.org/showthread.php?t=816647)

2. [http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html](http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html)

3. [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/)

4. [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/comments/218](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/comments/218)

5. [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453)

6. [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Just to add - I did not try every suggestions on these threads, just the odd one or two that seemed relevant to either Gutsy or Hardy depending on which version i had installed and was trying to fix at the time.

---

### Post by mixtri on 2008-06-11
Ok, I'll try the Memtest and see what I get.

However I feel very strongly that Firefox maybe even java have a big role to play in all this. As for the weird shutdown behaviour I have no clue.

---

### Post by mixtri on 2008-06-11
I forgot to mention that the PC doesnt seem to be overheating, as for memory,  I have 1.5 Gb worth which is a fairly new chip about 5 months old. I think i'll give ubuntu one more go. I'll reinstall the system but this time I won't mess around with multimedia configurations or fixes for firefox. The only thing tho is it means i won't be able to stream audio or have flash etc. is it worth using a system in that state? i should bl**dy well think not  :)

---

### Post by todak on 2008-06-11
If your computer restarted in the middle of a previous restart, it certainly cannot be software related! Random system restarts are the result of one of three things: bad memory, a bad power supply or overheating. My problem a few years ago was the latter. I wanted to heave the computer and anything associated with it into the burn pile. :evil: But logic prevailed and I opened up the case and discovered that one of the ears that hold the processor heatsink/fan assembly in place had popped off and hence caused the CPU to overheat and exhibit random crashing/restarting behavior. I repaired the ear, put on a dollop of thermal paste between heatsink and processor and attached the heatsink to the ear. While the case was opened, I also cleaned out the dust from all heatsink vanes, all fan blades and all openings that contributed to airflow. After reassembly I had no further problems. :) Another time later on a different computer, same behavior. I checked all cooling-related possibilities and all was okay. I did a memory test and found it was bad. Replaced memory and no problems since. \\:D/ Chances are, if you reinstall Windows now, the same thing (random restarts) will happen. :(

You may also want to check your power supply. Substitute yours with one that is known to be good. My wife had the same symptoms as you, so I checked cooling and memory and found no problems. Her computer then suddenly quit. I opened the case and and discovered a hole in the motherboard chipset processor. I immediately removed the power supply and looked at it and sure enough, it took a dump! Luckily it screwed only the motherboard. The main processor, memory and all attached hardware were still functional. So with the purchase of a new power supply and motherboard all was well again.

---

### Post by mixtri on 2008-06-11
IC. I hope its not the memory as I only recently bought a new chip.
I will have to do a test for that.
The weird thing is i have these periods of relative calm with regards to the weird shutdown behaviour. Teh all of a sudden it goes mad.
As for the firefox misbehaving well thats always ongoing. Any solutions for that. Well actually, prob not, as I have scoured the forums and not yet come up with anything that fixes the problem.
I'll shutdown do the memtest upon reboot 
Thanks for your help.

I thought i might post some more details. let me know if there is anything interesting you can glean from these screenshots.

---

