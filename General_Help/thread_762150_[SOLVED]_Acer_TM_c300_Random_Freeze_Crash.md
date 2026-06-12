---
title: "[SOLVED] Acer TM c300 Random Freeze/ Crash"
date: 2008-04-21
forum: General Help
---

### Post by fooby12 on 2008-04-21
Hi all,
     After adoring Ubuntu since November I have encountered 2 problems. The first is unrelated to Ubuntu, but may be related to the current (and more serious) problem.

     1) Dead HDD - While running Ubuntu 7.10 the 40Gb HDD reached about 70% capacity and started a reboot cycle. Eventually I received a Kernel Panic while booting. I understand that this is typical with HDDs that have bad sectors etc. So, failing any other HDDs I Gerry-rigged my MP3 player and re-installed Ubuntu 8.04b.

     2) Random Crashes - After a few weeks running this "new" system and continually skipping the HDD check as Ubuntu booted, I began to experience random crashes. It might be a freeze as I am unfamiliar with the meaning of either word. So, I will explain. All hardware instantly stops responding, the mouse will typically center itself on the screen, and the CAPS lock LED flashes. Sometimes the screen will go black after a little while, other times the whole system will shutdown. The only remedy is holding the power switch for 5 seconds and starting again.
     With the occurrence of crashing becoming so frequent and another Kernal Panic error, I reinstalled Ubuntu. This item from a CD. I used a brand new HDD. Two or three times during the install process the same type of crash occurred. Nonetheless, the system installed. However, the crashes still happen, and there seems to be little correlation with what I'm doing.
     I have learned a few things about this problem. It happens sooner if I use my bluetooth mouse. It has happened more frequently while a package update is going on.

Here is some information about my system:

Acer TravelMate c300
1.7Ghz PentiumM
1Gb RAM

Ubuntu 8.08
All recent updates
Tablet Features Enabled
No effects running

Any help would be great. The problem has taxed my search-fu because it is difficult to explain. My current hypotheses in order of likelihood are: Graphics Drivers, Wireless Card, Dying RAM, Dying CPU, Dying MoBo. I did not experience any sort of random crashing until I upgraded and was running a huge number of effects before I upgraded.

Thanks,
Travis

---

### Post by fooby12 on 2008-04-22
I think I got jipped by the forum update and this is a legitimate...

Bump

---

### Post by fooby12 on 2008-04-22
bump

---

### Post by beameup on 2008-06-21
I'll give you a "bump" and a question here.

I just installed 8.04 on an Acer TM C302XCI Tablet 512b RAM, using the WUBI installer and so far it's been working fine. What exactly did you have to do to "enable all Tablet features"?
I found this here: [http://www.tabletpcreview.com/default.asp?newsID=679](http://www.tabletpcreview.com/default.asp?newsID=679)  but havent't tried it yet. 

The Tablet belongs to my daughter. We can't locate the restore discs for it. The Windows side is having some slowness issues(still the original install)and needs to be reformatted, but that's not gonna happen anytime soon, so I thought I'd give Ubuntu a shot at it. Figured it was best to use the (WUBI) windows install first to make sure it works OK. Haven't really pushed it much yet, so I can't make a good review, but initially it's looking good and runs faster than Windows even though it's not installed straight up. I browsed across a couple of articles where folks were having trouble with this model using 1GB of Ram or more, so that's a possibility.

Good luck.


Edit: Look at the bug about the power supply for the C300 here (6th from the top):  [http://www.tabletpctalk.com/bugs/index.shtml](http://www.tabletpctalk.com/bugs/index.shtml)

---

### Post by fooby12 on 2008-06-21
Hey,
     Thanks for the bump. I did figure out the problem and I will detail the troubleshooting process below. Your question about the tablet features is off topic for this thread so I will send you to this one: [http://ubuntuforums.org/showthread.php?t=232250](http://ubuntuforums.org/showthread.php?t=232250) . That thread is where I found all of the answers for the TMC300 exclusively.

Now for my troubleshooting:

1) I attempted to install another distro, ZenWalk and maybe one other. None of them would even finish installing before the computer would shutdown. Typically with the same symptoms as detailed above.

2) I gave up. I decided that the computer was dead and the only thing to do was run it as is.

3) So I installed DSL onto the hard drive and for 3 whole weeks it worked wonderfully. It ran very fast and never crashed. One observation I made was the total lack of ram used by the OS, 23Mb after booting. This gove me an idea.

4) I removed a RAM DIMM and tried to install Ubuntu 8.04. The installer worked fine. So did everything else. Thus I deemed the RAM dead after 4 years of heavy use and ordered a new 1Gb DIMM. This actually upgraded the computer to 1.5Gb RAM total.

5) The computer has not crashed since.

Based on the nature of the crash I believe that the RAM had gone corrupt and that the crash was not a result of the DIMM over heating. Had it been over heating I would expect a complete shut down as opposed to the strange every-thing-stays-on-the-screen behaviour. Nonetheless, the prom has been solved and the mystery of the flashing caps lock is no longer. Thanks for the bump and I hope this helps anyone with an old Acer TMC300

Fooby

---

### Post by beameup on 2008-06-21
Ok Thanks, I'll have a look. It sucks they put that 2nd stick of RAM under the keyboard with NO documentation of it. This one came with 2 256MB sticks. The one under the keyboard is 133mhz, the one that's accessible from underneath is 166mhz. If I remember correctly, the PC will run the RAM at the slower mhz when in pairs. 

Thanks again.

---

