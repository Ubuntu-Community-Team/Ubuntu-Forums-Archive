---
title: "restoring / enabling terminal beep / system beep"
date: 2016-05-12
forum: General Help
---

### Post by rifter on 2016-05-12
Years ago, someone made a decision to quiet system sounds and beeps in Ubuntu, and there was much wailing and gnashing of teeth on the part of people who needed those beeps.  At the time, it was supposed to be that eventually some configurable system sound would be available for terminal beeps.  Meanwhile, the bugs from the links in my sig were filed and the workarounds from my sig were followed by people like me who wanted some beeps.  And here all these years later, it seems that never happened.

It seems those steps no longer work.  The solution was substandard, anyhow, because it relied on the pcspeaker.  It would be nicer to have some normal system sound for error beeps and terminal beeps.  In any case, after following those steps as I normally have done, the "beep" command makes the pc speaker beep but echoing ^g doesn't.  When I ssh to a chat system I have been using for almost 20 years now that uses terminal beeps for alerts, it doesn't beep either (does on Mac OS X and Windows, where you have a working and configurable system beep).  I installed putty and configured it to beep using the default system alert sound, but that doesn't work, either.

Alsamixer no longer has a "beep" line that I can see.

Is there any way to get a system alert beep anymore in Ubuntu? Can I get that to work in any terminal program? (I have been using whatever the default terminal program is, gnome-terminal, and xterm).  I am currently using Xubuntu 14.04 LTS 64 bit.

---

### Post by QDR06VV9 on 2016-05-12
Have you had a look in /etc/inputrc

For the terminal not sure if you have seen this one or not but: [http://askubuntu.com/questions/19906/beep-in-shell-script-not-working](http://askubuntu.com/questions/19906/beep-in-shell-script-not-working)

---

### Post by rifter on 2016-05-12
> **runrickus said:**
> Have you had a look in /etc/inputrc

For the terminal not sure if you have seen this one or not but: [http://askubuntu.com/questions/19906/beep-in-shell-script-not-working](http://askubuntu.com/questions/19906/beep-in-shell-script-not-working)

Thank you for your swift reply.

Yes, as in that post, I have enabled the pcspkr module and installed the beep program.  (beep is just a means for testing - it isn't what makes beeping work).  I also used 

xset b 100

to set the system bell volume to full within the xterm/terminal program and 

xset q

to make sure that was set.  Under those conditions, 

beep 

produces a pc speaker beep.  These steps used to be enough to make ^g emit a beep from the pc speaker, but aren't enough now.  Within Ubuntu there have been over the years things added within layers of sound programming to suppress any beeping.  That's part of why going around it to the pc speaker was easier to do.

In case anyone wonders

printf '\a'

as suggested in that post, also does not emit a beep of any kind.  Back in the early 2000s, gnome allowed the setting of any sound you wanted for just about any event.  I'm not using that now, but I do know when I was, after these changes, that there were no event sounds anymore.  I kind of hoped by now there would be configurable event sounds or at least a system alert sound.  This being linux, though, there has to be some solution.

---

### Post by danthonyd on 2016-07-05
I lost the system bell after installing Ubuntu 16.04. The "beep" command is installed and works, but **echo -e '\a'** and **printf '\a'** make no sound. I did the modprobe unblacklist routine and all the other steps which used to work, but I suspect something new in 16.04 runs after you login which turns off the standard beep. Pressing down in Gedit and the terminal also used to make the beep, but something is telling it not to anymore. The speaker works of course, as the alternative beep command proves.

Interestingly, Ubuntu can and does produce the system beep in two instances:
1) Edit the grub menu at /etc/default /grub and remove the # hash at **GRUB_INIT_TUNE="480 440 1"** and you will get a beep when grub loads.
2) Press Backspace without entering your password at login, and you will get the error beep.

I think we need to find whatever it is that loads and nullifies the beep after you log in. 
I wish there was a standardized name for this particular system beep/bell to make searching about it easier.

---

### Post by banceu_sergiu_ione on 2016-07-05
Before doing any changes or install anything, had you guys check the Alert Volume in Sound Settings/Sound Effects ?

---

### Post by danthonyd on 2016-07-05
> **banceu_sergiu_ione said:**
> Before doing any changes or install anything, had you guys check the Alert Volume in Sound Settings/Sound Effects ?

We are talking about the beep made by the tiny internal speaker integrated or connected to the motherboard, not the sounds emitted through the soundcard. You cannot control the volume on this. In older computers BIOS would beep for errors and other things

---

### Post by banceu_sergiu_ione on 2016-07-05
> **anthonyanthonydd said:**
> We are talking about the beep made by the tiny internal speaker integrated or connected to the motherboard, not the sounds emitted through the soundcard. You cannot control the volume on this. In older computers BIOS would beep for errors and other things

Oh.. my bad. 

Had you check /etc/modprobe.d/blacklist.conf for blacklisted module to see which one is on blacklist ( pcspkr is the one i have )and try to loud it? Ain't ^g work after? 
I suppose you are sure and had checked your MoB have a speaker, mine dont have :)

---

### Post by danthonyd on 2016-07-06
Alright. So, I loaded the Ubuntu 14.04 LTS DVD and chose "Try Ubuntu", then opened a terminal, typed **sudo modprobe pcspkr** and it worked. Pressing down, back, etc. caused a beep in the terminal and Gedit. The terminal bell/system beep is good in 14.04. 
This proves something is up (or down) with Ubuntu 16.04 LTS.

Just for the record, loading the pcspkr.ko module, unblacklisting it, trying in vain to turn up the volume, blah, blah, blah, these are no longer relevant at this point. We are way beyond that now. Something very, very elusive in this 16.04 distro is blocking the bell. 

I ran modinfo pcspkr on the current machine with 16.04, and another machine with 14.04. Maybe these outputs will call attention to something.

Ubuntu 16.04 LTS (beep: bad)
```
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/input/misc/pcspkr.ko
alias:          platform:pcspkr
license:        GPL
description:    PC Speaker beeper driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
srcversion:     70DA5303FF822CCBD45FF6D
depends:        
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions
```
Ubuntu 14.04 LTS (beep: good)
```
filename:       /lib/modules/3.16.0-71-generic/kernel/drivers/input/misc/pcspkr.ko
alias:          platform:pcspkr
license:        GPL
description:    PC Speaker beeper driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
srcversion:     686B6CB8D4953F3B1372210
depends:        
intree:         Y
vermagic:       3.16.0-71-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2A:DF:46:ED:E6:3C:FA:EC:30:DD:73:0F:D3:B8:2E:C8:AF:FD:F9:61
sig_hashalgo:   sha512
```
Also, this was a problem in the past with new distro releases such as Karmic. Same behaviour. The beep speaker works with beep command, but not as an error as we are accustomed to. See these links:

[http://ubuntuforums.org/showthread.php?p=8903493#post8903493](http://ubuntuforums.org/showthread.php?p=8903493#post8903493)
[URL="https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154/comments/50"]https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154/comments/50

[/URL]If you ever tried to tab complete with a typo in the terminal, that beep would remind you of your mistake. That's what we want restored.

---

### Post by danthonyd on 2016-07-06
I submitted a bug about this, albeit very awkwardly as it is my first ever.

See [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1599599"]Bug #1599599
[/URL]Also see the incredibly long comment details on [Bug #486154]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/486154") this resurrected.

---

