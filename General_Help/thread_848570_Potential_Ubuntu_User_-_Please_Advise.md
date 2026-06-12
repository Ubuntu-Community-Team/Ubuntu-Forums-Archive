---
title: "Potential Ubuntu User - Please Advise"
date: 2008-07-03
forum: General Help
---

### Post by i-Set on 2008-07-03
Hey there guys im going to keep this short and simple. Basically im currently with windows and have looked into Ubuntu as a new OS. Please answer my questions accordingly.

1. Playing around with the live cd is awfully slow, am i to expect this when full installation has taken place? I have 256mb ram.

2. Hardware -  do i have to install hardware drivers as I am not very technical with this stuff. I have Via Rhine II Fast Ethernet Adaptor and a Creative External Soundblaster 24bit, also will my USB ports work. Please note that my VIA ethernet can be seen on my windows add/remove programs, so does that mean i will have to install drivers for it when i install Ubuntu. 

3. On windows I am able to increase virtual memory thing so it uses my hard drive ram to make it a bit faster, can i do this on Ubuntu.

4. Finally is there any common installation faults that stop many people from installing properly?

As long as my internet and music is working after installation without downloading anything, im happy.

---

### Post by Pjotr123 on 2008-07-03
Read a bit here:
[http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/)

That will help, I think.  :-)

---

### Post by oldos2er on 2008-07-03
Minimum RAM to run the Livecd is 384MB, so it's not surprising it's slow for you.

 Is your ethernet wired or wireless? If wired, it should work "out of the box." Yes, your USB ports will work. I have no experience with SoundBlaster cards under Linux, so I can't comment on that.

---

### Post by viciouslime on 2008-07-03
The live cd will be slow on any system, there is a LOT more than 700mb of data on the live cd, but as cds only hold 700mb it has to be compressed. This means your computer is constantly having to decompress vast amounts of data on the fly, add to that the fact that cd read speeds are considerably lower than hard disk read speeds and the fact that lots of extra ram is being used for storage as well as running programs and it's no surprise that the live cd is slow.

Chances are all of your devices will be supported out of the box on linux, but the live cd will show you this, if it works on the live cd, it'll work when you install it too :)

On linux based systems you have what's called a swap partition. This is the equivalent of "virtual memory" in windows. You can make a swap partition as big or as small as you like, but the general recommendation for 256mb of ram would be a 512mb swap partition. You'll find that linux is much more efficient with memory management.

As to point number 4, nothing i can think of, but if you have any problems, post back here and i'm sure the community will do their best to help you :D

---

### Post by i-Set on 2008-07-03
i thank all the above users as it has really helped me into deciding to move over to Ubuntu...basically i tried firefox 3 and the internet works..so that concludes that my VIA network ethernet adaptor is working. However when i tried playing a music mp3 from my hard drive, it mentioned me to install codecs. so im still unsure whether my creative soundblaster 24bit is going to work. if it isnt im not going to install ubuntu as this is the only form of sound card I have. 

Any more help from you helpful people... :)

---

### Post by bluepowder7 on 2008-07-03
1 - if you only have 256megs of ram, probably best to swing to the Xubuntu side of the fence.  on just about any system, the live CD is gonna be much slower than the final real install on a hard drive, so ignore that aspect while you check it out.

2 - most stuff just works without having to install drivers, reboot, install another driver, reboot, and so on.  some things might need an extra step (like nVidia graphics), but those are much less frequent than on windows.  usb will work.  some stuff will work surprisingly easily, too!  however, some codecs need to be manually installed since they're not "free".  it's a legal limitation.  quite simple to actually do, but it's not there by default.

3 - right, as said before, virtual memory in windows is now a swap partition on your hard drive in linux.  and yeah, make it at least as big as your ram, and double isn't a bad thing (esp if you have low ram).

4 - dual booting and partitioning are the things that get most first-timers.  if you want to dual boot (to use windows), then it'll take a bit more work up front.  if you're going all-ubuntu, then it's dead easy.

other - it's free, so don't be afraid of breaking stuff and having to reinstall it all over again.  you don't need to buy a new copy, or buy licenses for software you wanna use.  realize that there's usually at least 2 applications for even the most basic innane task.  for example - the default Network Manager can be replaced with WiCD (an especially good idea if you use wireless / laptop, and quite honestly even for desktops)

more other - the eye-candy that is compiz-fusion is fun and great, but unless you're actually making good use of the functionality, you'll get tired of it after a few weeks.  i know i did.  and besides, it might not even be on Xubuntu.

---

### Post by i-Set on 2008-07-03
again thanks for the above informative post, I have decided to install Ubuntu tomorrow before I go off to work. I will get an external usb hard drive and save all my songs and files on there. But I have few more questions.

[B]1. At first I did not hear any sounds on live cd, so i went into system i think, and went into sound section, there i was able to see various playback option and test them, at first I tested the standard one but it didnt work, so i clicked on list and looked for USB sound and tested and it beeped non-stop until i pressed okay. Does that mean my External Soundblaster card works? (sorry if that sounds silly to you experts)

2. I have seen you tube videos of installation and when it comes to choosing the partioning bit with the guided and manual option, if i click on guided option, will that delete everything on my hard drive? p.s i do not want windows anymore, just ubuntu on its own.

3. Finally touch wood that nothing goes wrong, but say for instant there is an error after installation, will i be able to revert back to windows and if i cant go back to windows. will my cd drive still work which will allow me to try and install ubuntu again?[/B]

Thanks in advance and sorry if im pestering you guys. :D

---

### Post by bluepowder7 on 2008-07-03
i assume you have win95 / win98 / win2k, since winxp or vista would be molasses-slow on your machine.  i assume you have an original install CD (or floppies!!!) for windows?  if so, there's no harm in letting the installer use the entire hard drive, blow away windows.

2 - yes, if you click on guided, it will almost definitely format the drive (or at least partition) that it's installing to.  if you have documents or movies or songs, best to back them up.  or, score yourself a second hard drive, and install ubuntu onto the "new" drive (physically remove the old drive from the computer and store it safely).  anything over 10gigs will be enough for the system, many installed programs, files, etc.

3 - yeah, no matter what, your CD-ROM drive AND the ubuntu cd itself will continue to work for a while.  i've reinstalled stuff on my machine 2-3 times because i...  um... totally borked it.

---

### Post by kevdog on 2008-07-03
Just go for it -- don't be scared.  I have a laptop with 256 mb ram, 1998.  Ethernet worked out of box.  You may have problems with video resolution at first -- which is a pain which may require editing of the xorg_conf file.  Wireless is also kind of painful but definitely doable if this is your situation.  Old soundblaster cards should be supported, newer x-fi cards have a problem -- lack of driver support.  

If you want to delete everything on your drive - an installation option will prompt you.  As far as partitioning, this is personal preference.  I used to partition a lot, then not at all.  I think if next time I will only stick /home on a different partition so when I install a newer ubuntu version, personal settings will be preserved.  Partitioning is a controversial subject, so don't take what I say as the word of god.  If in doubt, just put everything in one big partition.  I stressed about this at first, but later found its not really a big deal.

---

### Post by flytripper on 2008-07-03
you will have to install drivers/codecs for media playback as they are owned by a capitalist who wont allow them to be packaged freely in a Linux distribution (the cost of these are included in the windows price (for windows that is)). Actually i cant remember if mp3's are supported out of the box in windows. mm the olden days :)..

```
sudo apt-get install ubuntu-restricted-extras
```

enter the above in the terminal window in mainmenu>accessories>terminal and you should be the shizzle mate.

---

### Post by rainwalker on 2008-07-03
After you get Ubuntu installed, check this out for all the multimedia-related stuff (stupid companies won't let it be included for free): [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by GuitarRocker2562 on 2008-07-03
exactly as flytripper said, that command will get all your audio and video working, i think you will like ubuntu and you seem to already have some troubleshooting skills, congrats.

---

### Post by GuitarRocker2562 on 2008-07-03
Oh yea, and please know that all your data will be erased during install, backup anything important!

---

