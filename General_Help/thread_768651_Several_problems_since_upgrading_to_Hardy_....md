---
title: "Several problems since upgrading to Hardy ..."
date: 2008-04-26
forum: General Help
---

### Post by cyclingman on 2008-04-26
Until Thursday, I was using Gusty Gibbons, with everything working pretty much fine. But now I have a few problems:

1) The wireless card was not installed (it had been un-installed or something) so I  went to the same HOWTO as when I installed it for Gusty: 
> [http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)
I now found a helpful section for Hardy telling me to go to System>Administration>Hardware Drivers. I then went to this a ticked the box to install my card but got the following message:
> W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb) 
  Could not resolve ‘gb.archive.ubuntu.com’

Which I presume is because I don't have an internet connection, obviously without my Wireless card installed, duh.

2)And now, when I click on Hardware Drivers the program doesn't show up at all :(

3)When I load up my machine and desktop I receive several messages saying
> The panel encountered a problem while loading ... Don't Delete. Delete. 

Are problems 2 & 3 linked? Any help appreciated, on any of the problems. Sorry this is so long ...

---

### Post by Novus on 2008-04-26
what I would try (Im far from an expert in this but I think it makes sense :) ) is to manualy download the .deb and run it..

---

### Post by cyclingman on 2008-04-26
I did think of that too. But when I open it I get the message > You are recommenced to install the software from the channel instead
Then I just wasn't sure if I should go ahead with it, should I?

---

### Post by cyclingman on 2008-04-26
Ok, I did it, and nothing happened, just like when trying to open the Hardware Drivers program.

Should I do a complete clean install? Because it seems that I have a lot of problems. Does it just involve downloading from site, burning to disc, and then put it into my ubuntu laptop? Or is it more complicated? Because last time it was from windows to Gusty. Is there a HOWTO?

---

### Post by GuitarRocker2562 on 2008-04-26
do you have a seperate /home parition? If not, find a guide on how to switch form a folder to partition (should not require reinstall) after you have done this successfully, reinstall and make sure that your /home parition is mounted as such and NOT marked to format, do format your root (/) partion though.

---

### Post by cyclingman on 2008-04-26
What are the advantages of doing it this way?

---

### Post by meharts on 2008-04-26
Hi cyclingman, sorry I haven-t got any answer to your problems, but I posted [http://ubuntuforums.org/showthread.php?t=768054](http://ubuntuforums.org/showthread.php?t=768054). There are major problems as I see it with the latest version.

The fact that certain administration links die when trying to access them as user - but works from root - leans towards a privileges problem?

There are so many posts without people looking around - me included:)
that we don't see the real picture.

As yet, no one has replied to my post, but I don't think I am the only one having problems opening links in admin.

Just thought I'd let you know that you are not alone.

meharts

---

### Post by mikepry on 2008-04-26
Well I'm glad I'm not alone here. My son's dell is a ubuntu only machine and we upgraded to hardy yesterday and we have lost our wireless AND ethernet both! Now what to do? This is a bummer. I knew Ubuntu was to good to be true. Major hassles ahead to be sure. If we can't even hook it up with a wire to the internet I'm at a loss here. Hopefully someone will have a workaround soon.

---

### Post by cyclingman on 2008-04-26
Yes, a solution please, it seems to be us beginners who are suffering. 

Meharts, explain, how do you run each program in terminal from root, because if I run, for example:
> gksu /usr/sbin/synaptic
in the terminal, it gives me no reply, not even my name (as it normally does when I open the terminal). Like what it does as if it were running a program, only I can't see anything

???

---

### Post by cyclingman on 2008-04-26
If it helps anyone to find a solution, here are the lists of the programs from my System>Administration panel that work, and do not work:

_Work_
Authorizations 
Language support 
Network
Network tools
Printing
Samba
Services
System Log
System Monitor
Time and date
Update Manager
Users and groups

_Do not work_
Hardware Drivers
Hardware Testing
Software Sources
Synaptic Package Manager

These programs that do not work get as far as "starting Administarati..." and then show nothing. I can also see that they  are to do with Hardware or Software.

Another thing I noticed (as mentioned previously, was when I first tried these programs (after upgrading) they worked, but I HAD to click them twice (the first click would give me nothing). The next time I booted, I received the above, no matter how many times I clicked.

---

### Post by cyclingman on 2008-04-26
bump

---

### Post by cyclingman on 2008-04-27
???

---

### Post by danwood76 on 2008-04-27
Do a fresh install and your problems will go away.

Make sure you backup your home folder if you dont have a seperate /home partition.
It also helps to save the contents of your /etc folder aswell just incase you want to keep your samba/fstab/... configs.

---

### Post by cyclingman on 2008-04-27
Completed the clean/fresh install as a work around to the problem, and it did solve the administration problem.

However, the wireless card is still causing me problems; the Hardware Drivers program opens up and allows me to click on my driver (after allowing resporitries in synaptic, and clicking on the cd), and after the first run, of attempting to install, it gave me an error. The second time I tried it, the whole system crashed (unusually for Linux) about 3 seconds after clicking install. This has happened every time since.

Has anyone got any ideas on this topic?

---

### Post by danwood76 on 2008-04-28
No real ideas, have never run a broadcom wireless card.
I would file a bug report on launchpad, that way some devs might be able to help you out.

---

### Post by meharts on 2008-04-29
Hi cyclingman, sorry been a bit busy of late. If you are still having problems with synaptic, then all you should need to do is open a terminal and su to root and run #synaptic as the code.

The others I had gone the long way round by first finding the command for each program. There is almost certain someone who will shoot me down in flames - but here goes:

&#340;ight click on System and Edit Menus. That will give you everything that is installed. Go down the list to admin and click on that to expand the tree. Right click on Hardware Drivers (for example) and chose properties. The window that opens gives you the command for running that utility. Copy that command to a terminal and as root run it. It should open the Hardware Drivers window:)

Please say if that you don't follow what I have written. I have tried a new install and this problem still exists - maybe a bug in the works?

meharts:)

---

