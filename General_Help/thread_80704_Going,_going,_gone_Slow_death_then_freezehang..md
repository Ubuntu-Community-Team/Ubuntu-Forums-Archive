---
title: "Going, going, gone? Slow death then freeze/hang."
date: 2005-10-22
forum: General Help
---

### Post by JordanH on 2005-10-22
Hi All,

I'm a little bit stumped at the minute.  I've been running 5.10 (prerelease) for just a short while now and left my PC up and running while away on a business trip.  When I returned home, I hit play in xmms.  The song started then stopped... the started... clearly having a hard time either reading or processing the data.  I noticed gkrellm was not updating and any action I took was extremely slow... i.e. trying to launch a terminal took about 10 minutes.

I also attempted to switch to a virtual console but after logging in, any command I typed would take ages... ls of my home directory was ~5 minutes etc.  Eventually all stopped responding.

A hard reboot (ugh) later and it came up fine... after about 15 minutes of sitting idle, the above scenario repeated.  Only I was able to shutdown -r now before it was too late.

Today, everything was fine for hours.  I worked on it all day, upgraded all packages, installed some software I wanted and then the slow-death happened again ugh.

I don't even know where to start fixing this...  Any thoughts?
(my thoughts were either power, disk or video settings but I can't see anything.)

My last comment is that shutdown -h now gives a lonnnng system beep.

System
IBM.  P4 2.8GHz 768MB

---

### Post by Iandefor on 2005-10-22
I've heard that GNOME tends to take up more and more system resources with time, but you seem to have a particularly bad case, considering your system specs. If the problem is with GNOME, hitting [control]+[alt]+[backspace] is easier than rebooting.
Try KDE and/or XFCE4 and see if you have the same problem. I dunno how to help with the shutdown -h thing.

---

### Post by vrecan on 2005-10-22
I have the same problem over time XORG ends up taking up my entire 512mb of ram & my 2.5G swap!  This has been an issue since breezy was released...

---

### Post by JordanH on 2005-10-22
I appreciate the responses guys, but I checked my free mem and I'm barely scratching the surface of available RAM.

I thought it might have been my NVidia driver but I checked all that and it looks to be installed correctly.  I did try to restart X and I even killed off X the hard way (at least kill -9 still worked even if it took a while...)

The strangest thing is even after I've killed everything except my ssh server, shutdown STILL doesn't work.

I thought it might be a RAM issue so I pulled them both out... both are PC2100, ddr266.

The system had been running RHEL4, FC1/2/3 and WinXP just fine...  hmmm. I thin this is ubuntu 5.10 specific or a hardware issue.

---

### Post by Ocxic on 2005-10-23
Go into your system->Prefrenceses->screensaver->advanced tab   and disable the power managment. obviously it's trying to iether gointo or come out of standby and it's obviously not agreeing with your system. try it out and let me know.

---

### Post by JordanH on 2005-10-23
Ocxic, I was thinking something along those lines although I was blaming the screensaver, not power settings.  Hmmm.... I'll give it a try today.

---

### Post by rickwood on 2005-10-24
I've got a similar problem (never, ever had this with hoary or any other distro).  After a while of running just fine, my system gets really, really slow.  From the time I notice the lack of responsiveness, I've got about 15 seconds until it becomes almost completely unresponsive.  So once it starts, it escalates very rapidly.  The first time this happened, gtkpod was indexing about 3,000 music files.  So I assumed the problem was related to lots of disk i/o.  But the other night it happend again and the only application open was firefox (4 or 5 tabs open).  So I have started leaving the system monitor running so that I can see if a program has a memory leak.  But this doesn't appear to be the case.  The one symptom that is always the same when this starts is endless disk activity.

This is really an interesting problem.  I'm not sure how to find what is causing this.  The other day when I noticed the slowdown starting, I quickly hit Ctrl-Alt-Backspace to kill X.  This seemed to work.  When I logged back in, everything was OK.  But a few other times I've been too slow and Ctrl-Alt-Backspace won't even work (at least within the 1-2 minutes I'm willing to wait) and I end up hard resetting the machine.

I'll have to mess with the screensaver and power settings to see if this might be the culprit.

---

### Post by JordanH on 2005-10-28
*ugh* Just returned home.

Screen saver was turned off.
Power management was disabled.

I was able to type "su -" <enter> in a previously open terminal.  System became unresponsive to the keyboard.  Via the GUI I was able to try to restart the system...  screen goes wonky and there I sat looking at a garbled display of colours and text.  (text was from an underlying virtual console).  A hardboot was required to get her going again.

The interesting thing is, I checked /var/log/messages and the last entry was from Oct 24 (the day I left) and it says,
"Oct 24 11:58:58 outback shutdown[6065]: shutting down for system reboot"
But... then nothing.  No boot messages, no messages that the system was even turned on since then.
The next entry is
"Oct 28 11:22:40 outback syslogd 1.4.1#17ubuntu3: restart."
Note that I actually tried to restart the whole machine (see above) at roughly Oct 28 15:00. The time was accurate when I left.

It looks like it's not even keeping correct time when it freezes...

---

### Post by Efwis on 2005-10-28
Jordan H,

that almost sounds like a mobo starting its death dance. but I'm not sure. There is a possibility that your CMOS battery is almost dead, depends on how hold it and/or you mobo is.another possibility is you might have one if not both sticks of ram goin out on you. i would recommend , just to make sure, that you reboot your computer then do the memtest that is listed in the Grub screen. this is a long process, so be patient.

Other than that I have no other ideas as to what it might be.

hope this helps

---

### Post by kurtkraut on 2005-10-28
Check if your problem is somehow close to this: [http://www.ubuntuforums.org/showthread.php?t=82494](http://www.ubuntuforums.org/showthread.php?t=82494)

---

### Post by JordanH on 2005-10-29
[QUOTE=Efwis]Jordan H,

that almost sounds like a mobo starting its death dance. but I'm not sure. There is a possibility that your CMOS battery is almost dead, depends on how hold it and/or you mobo is.another possibility is you might have one if not both sticks of ram goin out on you. i would recommend , just to make sure, that you reboot your computer then do the memtest that is listed in the Grub screen. this is a long process, so be patient.

Other than that I have no other ideas as to what it might be.

hope this helps[/QUOTE]
Well, my PC is only ~2-3 years old?  It's been running many different OS's just fine.

The problem seems to happen distinctly on 5.10 in a reproducible manner so I'm confident this is something specifically to do with ubuntu.  I have almost convinced myself it has something to do with power management.  I did a test yesterday where I queued up a bunch of songs in xmms and let it sit.  The reason being is that when the music stopped I'd know exactly when the system quit.  I didn't time it, but it was roughly half an hour or 45 minutes of sitting idle.  On the other hand, after a reboot, I can use it indefinitely as long as it doesn't sit idle.

idle hands...

Perhaps I should try an earlier kernel to rule that out of the equation.

---

### Post by JordanH on 2005-10-29
[QUOTE=kurtkraut]Check if your problem is somehow close to this: [http://www.ubuntuforums.org/showthread.php?t=82494](http://www.ubuntuforums.org/showthread.php?t=82494)[/QUOTE]
Thanks for the reference.  I'm not sure if it fits the bill, but I will definitely check my xorg.conf.

The differences between my problem and that one are
1. My CPU usage is nil.
2. My RAM usage is < 300MB (of 768 )
3. I personally edited the xorg.conf file to remove my load dri line.

---

### Post by JordanH on 2005-10-30
*nnerrrrg* I thought I had it fixed.
1. I turned off powermanagement in the bios.
2. I disabled my onboard sound card.
3. I removed a pci NIC (thought it might be a conflict).
4. I disabled the screen saver and powermanagement via Gnome.
5. Installed lm-sensors and all temperatures and fans are within reason.
6. I removed acpid from startup.

I proceeded to use the 'puter all day with no errors.  Even with long idle times.  There's no way my machine should have even tried to slip into sleep mode... I even left Azureus running to ensure there was constant disk reads happening. *neeeeerghh*  It still froze up over night.

---

### Post by Efwis on 2005-10-30
the only other thing that I can think of is to make a bug report of this. or even check the ubuntu bugzilla and see if there has been mention of this before with a fix possibly stated. 

it would also be a good idea to get a dmesg log right after boot and another one after one of your crashes and post both in the bug report so they have a comparison of before and after. that might help the devs, or whoever, in figuring out the problem.

---

### Post by ariel on 2005-11-04
I have exactly the same problem with my breeze installation. If I leave the computer idle for more than 1 hour or so it becomes totally unresponsive. even the ssh terminals become unresponsive. I it not dead however. a "top" in a terminal produces a display 10 minutes later. 

Curiously the clock in gnome panel shows the time the computer got sick.

My pc is an ibm netvista, p4 2.6mhz, 1GB ram. This never happened to me with winxp. I have seen similar reports all with ubuntu breeze. any clue anyone? this is very frustrating!

---

### Post by clueless on 2005-11-04
I have had the same problem too. Athlon 2500+ with 512MB RAM and I always had CPU usage at 100% and almost all RAM taken up by something I couldn't identify. It seems a metacity problem. I switched from metacity to expocity and the computer is running just fine.

If you would like to try and see if this helps take a look here: 
[https://wiki.ubuntu.com/Expocity](https://wiki.ubuntu.com/Expocity)

---

### Post by rickwood on 2005-11-06
Well, I found a way to fix this problem, but I don't like the solution.  I used synaptic and installed kubuntu-desktop, switched to kdm, and started using kde instead of gnome.  Problem solved!  Only problem is that I much prefer gnome!  So I guess I have a choice -- use what I like (gnome) and live with slow death, or use kde and try and get used to it again (I used to use it for years as a Mandrake user before switching to Ubuntu and gnome).

If nothing else, I've narrowed the problem a bit.  It isn't the nvidia driver, it isn't powernowd, it isn't the kernel, and it isn't xorg.  It's either gnome or metacity.  Now if I could just find a fix!

---

### Post by JordanH on 2005-11-27
[QUOTE=rickwood]If nothing else, I've narrowed the problem a bit.  It isn't the nvidia driver, it isn't powernowd, it isn't the kernel, and it isn't xorg.  It's either gnome or metacity.  Now if I could just find a fix![/QUOTE]
That seems reasonable, I'll have to agree with that.  I have been able reproduce the problem only if I am logged into Gnome.

... if I can get xfce4 installed this afternoon, I'll let you know if I can reproduce the problem there.

---

### Post by JordanH on 2005-11-27
*bump*  I left the PC running for over 4 hours under XFCE4, screensaver and music playing, a feat not able to occur while logged into Gnome. No problems.

Anyone know how I can narrow down where exactly the problem occurs in Gnome/Metacity/???

---

### Post by rickwood on 2005-12-14
OK, I think I've got this one fixed.

I did a clean reinstall of Ubuntu (yes Gnome, not KUbuntu).  I installed a few apps and everything seemed to work fine.  Then I changed to my preferred theme and installed a few more apps.  Then it happened again -- the slow death!  Maybe it's just a fluke, I thought.  But no.  Over the course of a week the machine experienced the slow death several times.

I began wondering exactly which application could have caused the problem.  I've only installed things from the ubuntu repositories except for a few multimedia things I got using Automatix.  Then the thought came to me that maybe my preferred theme is the problem.  Doesn't sound probable, but hey I've tried everything else.  So I swithched back to the Human theme.

Guess what?!  NO MORE SLOW DEATH!!!  I've left my machine on for a week straight without rebooting.  I've run several applications.  Then I decided after a week of uptime it was time to really test my machine.  So I ripped two DVDs at the same time using dvdbackup (I've got two optical drives).  Also at the same time, I surfed the net using Firefox.  Also at the same time I installed crossover office and dvdshrink.  Not so much as a hic-up!  The system remained totally responsive and solid as a rock.

Can you belive this?  It's very hard for me to believe that a mis-behaved theme could completely destabilize my system and make it lock up!  I've still got a bit of detective work to do.  I don't know yet which of the following is the culprit:

Controls:  RPanther3
Window Border:  RAuqa
Icons:  d3a-icons

I'll do a bit of testing over the next few weeks to see if I can narrow it down further.  But for now I'm just happy that my beloved Ubuntu Gnome system is back to its rock solid self!

---

### Post by billd on 2005-12-14
rickwood,
May I ask what kind of system you have?  Because I've got the same symptoms described by you, jordan and ariel.  And it's interesting because jordan described his system as "IBM. P4 2.8GHz 768MB", and Ariel said "My pc is an ibm netvista, p4 2.6mhz, 1GB ram."

My system is also an IBM Netvista (specifically the M42), P4 2.6MHz, 1GB RAM.  It would be interesting if yours was also an IBM.

One thing about my IBM is this: Ubuntu didn't recognize its onboard video -- I had to do something manually to get the drivers for the Intel 82845G "Brookdale" installed and running.

thx,bill

---

### Post by rickwood on 2005-12-15
Sorry, my system isn't an IBM.  It's an e-machines 2.6 GHz Celeron.  It's got on-board video, but I've plugged in an NVidia GeForce FX5200 card that I use instead.

---

### Post by ariel on 2005-12-16
[QUOTE=billd]rickwood,
May I ask what kind of system you have?  Because I've got the same symptoms described by you, jordan and ariel.  And it's interesting because jordan described his system as "IBM. P4 2.8GHz 768MB", and Ariel said "My pc is an ibm netvista, p4 2.6mhz, 1GB ram."

My system is also an IBM Netvista (specifically the M42), P4 2.6MHz, 1GB RAM.  It would be interesting if yours was also an IBM.

One thing about my IBM is this: Ubuntu didn't recognize its onboard video -- I had to do something manually to get the drivers for the Intel 82845G "Brookdale" installed and running.

thx,bill[/QUOTE]


in my case the video chipset was correctly detected, i810; i tried recompiling different driver versions, even removing the driver and using plain vesa, no way... even vanilla kernels with lots of different boot time options, then kubuntu instead of ubuntu, no way. finally i installed kanotix and it is a bit of a pain to get everything working but once i had it, it's been on for more than a month now, and it's also debian. I have ubuntu @ home, and i hope dapper drake will fix this strange problem so i can have it at the office too...

---

### Post by JordanH on 2006-01-14
Hi rickwood, I got your e-mail a while back but I can't remember if I responded.  I've tried your trick of switching themes but nothin'.  I've learned to cope with the problem... by leaving my computer off 24x7 and going on a road trip. :rolleyes: 

I'm still hunting for a solution...

[QUOTE=rickwood]OK, I think I've got this one fixed.

I did a clean reinstall of Ubuntu (yes Gnome, not KUbuntu).  I installed a few apps and everything seemed to work fine.  Then I changed to my preferred theme and installed a few more apps.  Then it happened again -- the slow death!  Maybe it's just a fluke, I thought.  But no.  Over the course of a week the machine experienced the slow death several times.

I began wondering exactly which application could have caused the problem.  I've only installed things from the ubuntu repositories except for a few multimedia things I got using Automatix.  Then the thought came to me that maybe my preferred theme is the problem.  Doesn't sound probable, but hey I've tried everything else.  So I swithched back to the Human theme.

Guess what?!  NO MORE SLOW DEATH!!!  I've left my machine on for a week straight without rebooting.  I've run several applications.  Then I decided after a week of uptime it was time to really test my machine.  So I ripped two DVDs at the same time using dvdbackup (I've got two optical drives).  Also at the same time, I surfed the net using Firefox.  Also at the same time I installed crossover office and dvdshrink.  Not so much as a hic-up!  The system remained totally responsive and solid as a rock.

Can you belive this?  It's very hard for me to believe that a mis-behaved theme could completely destabilize my system and make it lock up!  I've still got a bit of detective work to do.  I don't know yet which of the following is the culprit:

Controls:  RPanther3
Window Border:  RAuqa
Icons:  d3a-icons

I'll do a bit of testing over the next few weeks to see if I can narrow it down further.  But for now I'm just happy that my beloved Ubuntu Gnome system is back to its rock solid self![/QUOTE]

---

### Post by JordanH on 2006-01-14
For what it's worth, my system is an IBM NetVista A Series P4 2.8GHz 768MB with an NVidea GeForce4... uhm... I don't remember my video ram off the top of my head but whatever.
[QUOTE=billd]rickwood,
May I ask what kind of system you have?  Because I've got the same symptoms described by you, jordan and ariel.  And it's interesting because jordan described his system as "IBM. P4 2.8GHz 768MB", and Ariel said "My pc is an ibm netvista, p4 2.6mhz, 1GB ram."

My system is also an IBM Netvista (specifically the M42), P4 2.6MHz, 1GB RAM.  It would be interesting if yours was also an IBM.

One thing about my IBM is this: Ubuntu didn't recognize its onboard video -- I had to do something manually to get the drivers for the Intel 82845G "Brookdale" installed and running.

thx,bill[/QUOTE]

---

### Post by Bruce Adams on 2006-01-14
I wonder if the problems described in this thread are the same as what I was experiencing (see: [http://www.ubuntuforums.org/showthread.php?t=109901](http://www.ubuntuforums.org/showthread.php?t=109901))

The fix for my problem turned out to be the "noapic" kernel parameter. This Wiki page: [https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto) talks about how to set kernel parameters.

---

### Post by freemag on 2006-04-30
Interesting,  I have an IBM Netvista 2.4Ghtz 1gb Ram etc.  Am having the same issue as described in this thread using 5.10.  However, I am trying to set it up as a proxy server and will need to have it running 24/7.  Tried the noapic kernel para and still having the same issue.  Has anyone found other solutions?

---

### Post by ariel on 2006-04-30
[quote=freemag]Interesting,  I have an IBM Netvista 2.4Ghtz 1gb Ram etc.  Am having the same issue as described in this thread using 5.10.  However, I am trying to set it up as a proxy server and will need to have it running 24/7.  Tried the noapic kernel para and still having the same issue.  Has anyone found other solutions?[/quote]

apparently the latest dapper beta no longer has these problems. You still need the nolapic & no acpi kernel switches. Check this thread where this is reported:

[http://ubuntuforums.org/showthread.php?t=47330&page=4](http://ubuntuforums.org/showthread.php?t=47330&page=4)

If you try it, please post back your results... 

This is 

AR

---

### Post by freemag on 2006-05-02
[QUOTE=ariel]apparently the latest dapper beta no longer has these problems. You still need the nolapic & no acpi kernel switches. Check this thread where this is reported:

[http://ubuntuforums.org/showthread.php?t=47330&page=4](http://ubuntuforums.org/showthread.php?t=47330&page=4)

If you try it, please post back your results... 

This is 

AR[/QUOTE]
The "nolapic acip=off" tag locks up the start process right after the grub loads.  I created several startup menu choices in the grub menu including noapic.  The noapic tag seems to be working in conjuction with removing the ntp sync at startup using:

sudo update-rc.d -f ntpdate remove

In testing this solution, either by themselves didn't do the trick.  Together works like a champ (So far).  Usplash also seems to load much quicker now as well...  Thanks for the help....

---

### Post by telepathetic on 2006-06-07
I am having the exact same issues with my NetVista.  I just installed the latest Dapper.  However when i try to add the "nolapic apic=off" to my grub menu, it hangs on bootup just as freemag says.  But when i try his solution of removing the ntp sync-- it doesn't fix it.

Please help-- how can i turn off the apic without hanging the boot sequence?
(when i add those "nolapic apic=off" switches it hangs right after printing the first status line about loading drivers)

---

### Post by Bruce Adams on 2006-06-07
I'm running fine with Dapper (as I was with Breezy) with the just the "noapic" boot parameter. I'm not sure what "nolapic" or "apic=off" do. See: [https://wiki.ubuntu.com/GrubHowto]("https://wiki.ubuntu.com/GrubHowto")

---

### Post by Mattias on 2006-06-07
Hello
My netvista works with the line quoted below, I have not seen any freezes after settling on this menu.lst  grub line

    kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro quiet noapic nolapic pci=noacpi splash vga=792

Bruce is probably right about the nolapic parameter but i don't fix what's not broken 
//Mattias

---

