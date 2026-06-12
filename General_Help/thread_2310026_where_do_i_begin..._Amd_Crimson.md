---
title: "where do i begin... Amd Crimson"
date: 2016-01-15
forum: General Help
---

### Post by sleepystoner420 on 2016-01-15
Computer Specs:
I7-3770k 4 core (8 thread) 3.5 ghz Processor @4.0ghz
8 GB Ram
100GB partition (1TB HDD Dual Booted w/ W7)
Asrock Z77 Pro Motherboard
AMD MSI R9 380 GPU (4GB VRAM)
Razer Deathstalker / Mad Catz S.T.R.I.K.E. TE keyboard
MadCatz R.A.T. TE Mouse
750W PSU
Emerson 32" TV via HDMI (1920x1080 @60hz)
Ubuntu 15.10 / Windows 7

Hi, I've been having issues with re-installing Ubuntu, but i've been having a run of bad luck.
with Ubuntu 15.10 the first error i notice is My mouse stops working by time i open a program, the sidebar continues to work but within windows (such as chrome) it'll refuse to click. I found a temperary fix by 
using the Terminal and applying the "sudo service lightdm restart" command

I later fixed it by modifying the button mappings of the mouse via writing to the /etc/X11/xorg.conf config file

my main issue at this point is that when i try to install AMD Crimson 15.12 via the Linux option (.run not .deb) i end up with what looks to be gibberish the words are semi-readable but very scrambled preventing me from properly installing i've followed many guides to no avail installing dependencies and trying various methods. at this point i'm frustraited enough to actually ask for help on a forum

---

### Post by sleepystoner420 on 2016-01-15
well things took a turn for the worse, i managed to by-pass the install and build packages for ubuntu but upon reboot i got a black screen, and continues to stay black in safe mode guess i gotta start over :(

---

### Post by sleepystoner420 on 2016-01-16
No answers??? :(

---

### Post by Bucky Ball on 2016-01-16
Have you tried another release? I would to check that this is not release specific. Create a 14.04 LTS and try that, perhaps on a different partition or in a live session.

Did you try 15.10 from the install media prior to installing and did it have these same issues? Did you check in Additional Drivers after install and that was the driver offered or did you install manually from somewhere? Are you positive that is the right one?

[See here]("http://askubuntu.com/questions/681029/display-issues-with-ubuntu-14-04-with-amd-r9-380-graphics-card"). Might give you some clues ...

PS: I have changed your thread title for clarity. One issue a thread, please. This will help your chances of support. Post separate threads for the other things if they're still issues.

---

### Post by maxinstuff2 on 2016-01-16
Is there a reason you aren't just installing fglrx-updates from the repos?
I have an R9 270X and the drivers from the repos have been fine since about mid last year - but in the beginning the drivers from the AMD site were required and it was a fiddly, delicate process getting them installed.
You might find the guide I wrote back then helpful, much of it will be applicable if your card is not yet supported by the drivers in the repos.
[http://ubuntuforums.org/showthread.php?t=2244651](http://ubuntuforums.org/showthread.php?t=2244651)

I happen to use a similar mouse to you too, so have a tip on that as well - you can drop the config that applies to the mouse in a text file in the folder xorg.conf.d and it will still apply but wont be messing up your "core" xorg.conf file.
This is extremely handy when you are going through a saga such as yours where you might be regenerating xorg.conf several times in a short space of time trying to get something to work.

The folder is in the same place as xorg.conf itself: /etc/X11/xorg.conf.d
Config files placed there can be called *whateveryouwant*.conf and will be applied as if they were part of the core file.
Mine for example is /etc/X11/xorg.conf.d/rat7.conf

---

### Post by sleepystoner420 on 2016-01-16
on 14.04 i get a black screen before i can see the option to install on the disk so i haven't bothered with it beyond that. I've tried swapping the connection with HDMI to the GPU and the onboard, sadly i think a VGA would clear it up but i have no method atm.

as for the AMD crimson issue, it's pretty isolated to 15.12. I've been able to install version 15.11 but don't like the version was riddled with bugs and glitches, and even a fatal flaw in which the GPU would overheat from lack of proper fan control.

---

### Post by maxinstuff2 on 2016-01-17
Can you get into BIOS?

Have you tried physically removing your GPU completely and then installing the OS from there?

**EDIT:** You could also try manually installing a newer kernel that has better support. You could try kernel 4.4 that *buntu 16.04 LTS is shipping with in a few months time. If that works you could run it in the interim and then upgrade to 16.04 when it drops in April?

It does look like you will get some live by mid-year: [http://www.phoronix.com/scan.php?page=article&item=amdgpu-2016-details&num=1](http://www.phoronix.com/scan.php?page=article&item=amdgpu-2016-details&num=1)

---

### Post by jeff158 on 2016-03-02
> **sleepystoner420 said:**
> Computer Specs:
Hi, I've been having issues with re-installing Ubuntu, but i've been having a run of bad luck.
with Ubuntu 15.10 the first error i notice is My mouse stops working by time i open a program, the sidebar continues to work but within windows (such as chrome) it'll refuse to click. I found a temperary fix by 
using the Terminal and applying the "sudo service lightdm restart" command

I later fixed it by modifying the button mappings of the mouse via writing to the /etc/X11/xorg.conf config file



I got the same problem. It started, when I began to use the Strike T.E. Keyboard. I can reproduce this Bug in Ubuntu/Mint and Manjaro. 
Could you please describe how you fixed this bug? 

Thanks and greetings
Jeff

---

### Post by Bucky Ball on 2016-03-02
> **jeff158 said:**
> I got the same problem. It started, when I began to use the Strike T.E. Keyboard. I can reproduce this Bug in Ubuntu/Mint and Manjaro. 
Could you please describe how you fixed this bug? 

Thanks and greetings
Jeff

Welcome. Advise you start your own, new thread. What makes you think the OP fixed their issue?

This hasn't been touched for a month and the OP gave a description of where they got to with it. You'll greatly improve your chances of support by outlining your problem on a thread with a title describing your problem. Good luck.

---

