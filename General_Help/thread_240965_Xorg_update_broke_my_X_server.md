---
title: "Xorg update broke my X server"
date: 2006-08-21
forum: General Help
---

### Post by pain of salvation on 2006-08-21
I have just updated the xorg core, and now I can't start my X server. I get a kind of BSOD ( ](*,) ), and now I'm using ubuntu Live cd to write this..

Can anybody help me :confused:

---

### Post by hakune on 2006-08-21
Same here and no idea what's wrong

---

### Post by alex1973 on 2006-08-21
Same here - posting from ... windows :(

---

### Post by kinematic on 2006-08-21
happened here to and got this solution form another related thread.
Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version.

---

### Post by abelthorne on 2006-08-21
> **kinematic said:**
> When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10


I've had the problem too and fixed it with your solution. Thanks a lot.

After I managed to restart X, I got an upgrade message saying that version 1.1.0.2-0ubuntu10.3 of Xorg is available. Is it the bad update (I didn't look at the version number when installing it) or a quick fix already available ?

EDIT : ok, found the original thread. Current update that ends with 10.3 is BAD version. Boo ! Get away, bad update ! Don't come back to my computer ever again.

---

### Post by rantak on 2006-08-21
> **abelthorne said:**
> 

After I managed to restart X, I got an upgrade message saying that version 1.1.0.2-0ubuntu10.3 of Xorg is available. Is it the bad update (I didn't look at the version number when installing it) or a quick fix already available ?

I too had the problem and fixed it with the instructions in this thread. But to answer your question the 0ubuntu10.3 was the bad one at least for me, so don't install that.

---

### Post by Turgon on 2006-08-21
Had this problem too. Thanks for the fix. You saved my day:)

---

### Post by marianoi on 2006-08-21
Thanks for the fix...

I got used to it during the beta testing cycle, but I think this is too bad for the stable LTS version of Dapper...

Suppose you have 20 machines running Ubuntu in your Company, all at sudden you have to fix them all! It does not give a good impression about Ubuntu...:( 

Cheers

Mariano

---

### Post by wh0rd on 2006-08-21
Why would an update do that, anyone have an idea?

---

### Post by compwiz18 on 2006-08-21
Same problem, I'll try the solution, thank you.

---

### Post by wh0rd on 2006-08-21
The solution definitely works. I was wondering is there a way to disable that update from even showing up?

---

### Post by compwiz18 on 2006-08-21
> **wh0rd said:**
> The solution definitely works. I was wondering is there a way to disable that update from even showing up?
Same.  is there somebody who is king of the repos that can disable it or remove it or something?

---

### Post by Mustard007 on 2006-08-21
Inaceptable !!!!!

What this update do here at this time !  
2 stations broken because of that !!

Hummm...

Thanks for the fix.

---

### Post by Ragazzo on 2006-08-21
Broke mine too... thanks for the solution.

---

### Post by peabody on 2006-08-21
Mine is busted too.  Thanks for the info, I'm fixed again.

I did this to prevent the package from upgrading.  From a terminal, type the following:

```
$ sudo editor /etc/apt/preferences
```

Copy and paste the following into it:

```
Package: xserver-xorg-core
Pin: version 1.0.2-0ubuntu1
Pin-Priority: 1001

```

Save.  Apt should now keep the package back.

Out of curiosity, is anyone here NOT running the xgl/compiz repository stuff?  Is the package from the official repos?  If so, the lack of testing on this update was criminal.

---

### Post by compwiz18 on 2006-08-21
> **peabody said:**
> Mine is busted too.  Thanks for the info, I'm fixed again.

I did this to prevent the package from upgrading.  From a terminal, type the following:

```
$ sudo editor /etc/apt/preferences
```

Copy and paste the following into it:

```
Package: xserver-xorg-core
Pin: version 1.0.2-0ubuntu1
Pin-Priority: 1001

```

Save.  Apt should now keep the package back.

Out of curiosity, is anyone here NOT running the xgl/compiz repository stuff?  Is the package from the official repos?  If so, the lack of testing on this update was criminal.
If a later/better version comes out, will apt upgrade to that or will it never upgrade xserver-xorg-core again?

---

### Post by peabody on 2006-08-21
> **compwiz18 said:**
> If a later/better version comes out, will apt upgrade to that or will it never upgrade xserver-xorg-core again?

When the forums say it's safe, just delete /etc/apt/preferences.  If you don't yes, you'll never upgrade xserver-xorg-core again, which may keep other packages back.  However, keeping it this way is likely to never break anything provided the dependencies are correct in the repositories; you'll just be kept back feature/bug-wise.

---

### Post by mattlach on 2006-08-21
> **wh0rd said:**
> Why would an update do that, anyone have an idea?

It looks like the new Xorg version has some PCI/AGP problems.

I started trouble shooting it thinking I could fix the newer version.

Do all of you here have Nvidia cards?  Because the error that crashed mine was that when the nvidia module was loaded by Xorg, the module couldn't find my video card, thus disabling the screen, leaving Xorg with no screen to load and it failed.

At first I thought it was the nvidia driver, but I found that it was the same version as before I upgradeded xorg, so my guess is that the new xorg does something screwy with the PCI/AGP subsystem causing the driver module to not find the video card.

---

### Post by peabody on 2006-08-21
> **mattlach said:**
> It looks like the new Xorg version has some PCI/AGP problems.

Do all of you here have Nvidia cards?

Nope, ATI Radeon 9000 here.  Fglrx version 8.28.8 drivers.  I had the same error as you.  My guess is this update breaks proprietary driver users.  Anyone here running on completely open source drivers?

---

### Post by mgpower0 on 2006-08-21
> **peabody said:**
> Mine is busted too.  Thanks for the info, I'm fixed again.

I did this to prevent the package from upgrading.  From a terminal, type the following:

```
$ sudo editor /etc/apt/preferences
```

Copy and paste the following into it:

```
Package: xserver-xorg-core
Pin: version 1.0.2-0ubuntu1
Pin-Priority: 1001

```

Save.  Apt should now keep the package back.

Out of curiosity, is anyone here NOT running the xgl/compiz repository stuff?  Is the package from the official repos?  If so, the lack of testing on this update was criminal.

No pretty sure the update was from one of the Backport repo's & unsigned from memory. I didn't select it the first time it showed then about 5 min later thought stuff it and updated.](*,) Noticed on another thread sugestion to reinstall the nvidia driver is this required?

---

### Post by JedV on 2006-08-21
> **peabody said:**
> Nope, ATI Radeon 9000 here.  Fglrx version 8.28.8 drivers.  I had the same error as you.  My guess is this update breaks proprietary driver users.  Anyone here running on completely open source drivers?

I am running the default drivers, just installed Ubuntu for the first time last night, then ran into this error this afternoon.  My video card is an ATI Radeon 9500 Pro (AGP).

---

### Post by peabody on 2006-08-21
> **mgpower0 said:**
> No pretty sure the update was from one of the Backport repo's

I don't use the backport repos.  This isn't from the compiz repos either according to other threads.  Looks like core devs f*** this one up by not thoroughly testing.  Oh well, the pains of proprietary drivers.

---

### Post by tofuconfetti on 2006-08-21
Broke mine here also, the fix posted above worked fine.  I do have an Nvidia 6800 video card, but I removed the nvidia module (rmmod) and changed the driver from nvidia back to nv it still wouldn't start.  When I changed instead of the "(EE) device not found" message from the xserver output, I got a "no screen found" error message.

---

### Post by Ragazzo on 2006-08-21
> **peabody said:**
> Nope, ATI Radeon 9000 here.  Fglrx version 8.28.8 drivers.  I had the same error as you.  My guess is this update breaks proprietary driver users.  Anyone here running on completely open source drivers?

I got "Fatal server error: no screens found". I have an ATI Radeon Xpress 200 and I haven't installed any extra drivers for it.

---

### Post by TheForkOfJustice on 2006-08-21
Got the xserver update through adept.

Xserver is now busted.

I can't get into X when booting normally. Everything 'loads' but then there is a blink and the screen freezes (the load screen between the login and grub splash) but I can reboot is I hold down CTRL-ALT-DEL.

When booting in root 'safe' mode I get a kernel panic and have to use the power button.

I cannot therefore get into Linux.

Using Kubuntu on a laptop (now in my WinXP dual boot) and my vid card is ATI Xpress M200 with proprietary drivers and K8 kernel.

Using the LTOOLS program I can view and edit some files on my linux partition from windows.

Can I fix any of this from Windows XP.

And repos people: for SHAME! You fell asleep at the switch!

---

### Post by mattlach on 2006-08-21
> **mgpower0 said:**
> Noticed on another thread sugestion to reinstall the nvidia driver is this required?

that should only be required with a kernel update, but since the kernel driver is packaged with the binary kernel in ubuntu, I don't think we need to worry about that...

---

### Post by peabody on 2006-08-21
> **Ragazzo said:**
> I got "Fatal server error: no screens found". I have an ATI Radeon Xpress 200 and I haven't installed any extra drivers for it.

You're the second person, so there goes my theory.  Weird.  Apparently a guy/gal running an i810 was just fine with the update.  Hmmm.

---

### Post by mattlach on 2006-08-21
> **peabody said:**
> You're the second person, so there goes my theory.  Weird.  Apparently a guy/gal running an i810 was just fine with the update.  Hmmm.

Well then...  New theory..  What platform are you all on?

I'm on an NForce3 AMD64 platform.  Maybe the module Xorg uses to handle our mobo chipsets (specifically the PCI / AGP portions) is messed up in the new version, not allowing the driver to find our cards?

---

### Post by ThrobbingBrain66 on 2006-08-21
> **peabody said:**
> You're the second person, so there goes my theory.  Weird.  Apparently a guy/gal running an i810 was just fine with the update.  Hmmm.

im running an i915 chipset with the i810 drivers and xorg updated without a problem.  sorry to all you guys that had trouble.

---

### Post by marianoi on 2006-08-21
Here is the info about the package

It seems to be an official update...and you can find the email of one ubuntu guy..

Cheers

Mariano

---

### Post by TRAVISL on 2006-08-21
I tried the mentioned fix and I get "Version '1:1.0.2ubuntu10' for 'xserver-xorg-core' was not found.  Any ideas?

---

### Post by kblood on 2006-08-21
Yes, it looks like you mistyped it. Please check again:

```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```

---

### Post by GameGod on 2006-08-21
Any idea what the scope of this is? (ie. How many users are going to be affected?)

Is it people with certain hardware or everyone?

---

### Post by SeanCM on 2006-08-21
This hit me too.  I am new to Ubuntu...linux in general, and was about to reinstall thinking I did something bad.  Thanks for the fix.  I have a lot I need to learn.

Sean

---

### Post by TRAVISL on 2006-08-21
> **kblood said:**
> Yes, it looks like you mistyped it. Please check again:

```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```

Thanks I guess I'm zero blind lol.  Works great if I type the right command.;)

---

### Post by pokpig on 2006-08-21
For those who are really lazy, after downgrade xorg-core by

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

you may try

dexconf

and it generates auto-probe xorg.conf for you, 

may help you to get something to see before you get back your 3d

thx again for the fix

---

### Post by amgeex on 2006-08-21
> **peabody said:**
> Mine is busted too.  Thanks for the info, I'm fixed again.

I did this to prevent the package from upgrading.  From a terminal, type the following:

```
$ sudo editor /etc/apt/preferences
```

Copy and paste the following into it:

```
Package: xserver-xorg-core
Pin: version 1.0.2-0ubuntu1
Pin-Priority: 1001

```

Save.  Apt should now keep the package back.

Out of curiosity, is anyone here NOT running the xgl/compiz repository stuff?  Is the package from the official repos?  If so, the lack of testing on this update was criminal.

I'm not running the xgl/compiz repositories. After using xgl for a while, I think is more trouble than what I bargained for, it's nice, but not for me yet. Anyway, yeah, that update made me reinstall ubuntu... I thought it was something else, and then the automatic updates screwed up my install again. (Sounds a bit like windows? ](*,) )

---

### Post by Mr_Congeniality on 2006-08-21
I just looked into the problem.  It seems as though everyone in the known ubuntu world is being effected with this problem.

This is a horrific problem.  There could be people like beginning users who completely stop using Ubuntu because of this.


Do the people who manage the repositories know about this yet?   This is [COLOR="Red"]**CRITICAL**[/COLOR].

---

### Post by JimmyJazz on 2006-08-22
yes it broke my Xorg also, this is a not a good thing for a stable release!

---

### Post by caserio on 2006-08-22
Hi,

This simply should not happen. This is *untested* software !

---

### Post by JimmyJazz on 2006-08-22
launchpad seems to be down too, has the world gone mad!!!

---

### Post by TheForkOfJustice on 2006-08-22
World has gone mad.

Skynet has launched the nukes.

Giant killer robotic rainbow butterflies have begun slaughtering penguins by the thousands.

Personally, I blame Mac adopting the x86 standard.

---

### Post by TheForkOfJustice on 2006-08-22
BTW how in the hell do I fix this if I can't even get into my linux console?

---

### Post by K.Mandla on 2006-08-22
I had the same problem: xserver-xorg-core 10.3 crapped out my HP Pavilion I was troubleshooting. Which was all the more confusing, since I was trying to get the native ATI drivers to work ... :confused: 

I fixed it by using *sudo aptitude remove --purge xserver-xorg-core*. One of the options was to downgrade, which I did, and it did, and now I'm back to where I started. 

Methinks this needs corrected pronto.

---

### Post by TheForkOfJustice on 2006-08-22
I wonder if I post again will it get me a solution faster?

Or will it just get one more guy saying he has the same problem and managed to fix it, therefore infuriating me further...

...ahem...

I HAVE NO WORKING LINUX CONSOLE!


I HAVE A SCREEN FREEZE ON THE FULL BOOT AND A KERNEL PANIC ON THE CONSOLE BOOT!


DAMN YOU ALL!!!!



goin' to bed...'night :D

---

### Post by Ramaddan on 2006-08-22
Hi,

Was this from the normal dapper-updates,
or the backport?

If it was from the normal updates, isn't that bad?

People will then easily point out that Windows
never crashed to the gorund from an update before.

Yes, it turned crazy sometimes, but not halted...

I really hope it was not in the normal updates.
If it was, then serious thought and testing has to take place
for future updates.

Dapper has a good chance at replacing many other OSes, so I hope
more testing takes place next time.

---

### Post by peabody on 2006-08-22
> **TheForkOfJustice said:**
> I wonder if I post again will it get me a solution faster?

Or will it just get one more guy saying he has the same problem and managed to fix it, therefore infuriating me further...

...ahem...

I HAVE NO WORKING LINUX CONSOLE!


I HAVE A SCREEN FREEZE ON THE FULL BOOT AND A KERNEL PANIC ON THE CONSOLE BOOT!


DAMN YOU ALL!!!!



goin' to bed...'night :D

Night, sleep tight, don't let the bed-bugs byte (bite?).  When you get up in the morning, if you use Grub, try hitting ESC when it starts and selecting the recovery kernel.  That should get you to a root prompt.  May the force be with you.

---

### Post by Gomek on 2006-08-22
He gets a kernel panic on recovery mode.  I dunno...is there any way to mess around with installed packages from a live CD?

---

### Post by peabody on 2006-08-22
> **Gomek said:**
> He gets a kernel panic on recovery mode.  I dunno...is there any way to mess around with installed packages from a live CD?

Yes actually.  Make sure the root partition is mounted, then mount proc and sysfs under /mnt/root/proc and /mnt/root/sys or wherever the heck it is.   Then chroot into the folder.  This sets up an environment that makes it look like you're booted into your system.  This all has to be done from the console as root and I'm way too tired to go into details tonight.  Maybe tomorrow.

---

### Post by Boukyaku on 2006-08-22
This just hit me as well. I just came from gentoo and i was thinking "god, not here too" :p. I was also thinking it was very similiar to windows in terms of trying to shove an update down my throat and once it did things break.

Anyway thanks for the fix! And yes on the livecd, don't forget to cp /etc/resolve.conf!

edit: mepis has the same problem. Look at mepis.org

---

### Post by Obor on 2006-08-22
The fix kind of worked for me but not quite. I get the login screen and after that just some of my desktop blinking. 

If I didn't have a Windows PC next to me I'll be busy reinstalling now :-k 

This is not cool. How could this get to offical repos? Not nice at all.

---

### Post by abelthorne on 2006-08-22
> **Obor said:**
> The fix kind of worked for me but not quite. I get the login screen and after that just some of my desktop blinking.

Maybe you should try to reconfigure X : **sudo dpkg-reconfigure xserver-xorg** (make a backup of your /etc/X11/xorg.conf before).

---

### Post by th3james on 2006-08-22
This hit me too, running a Nvidia mx440, no usual hardware.

This really is pretty poor that such a massive bug could slip thru.

The only good thing is it made me realise im getting better at using terminal, i managed to install lynx, learn to use it, find this thread, and apply the solution from terminal, and im now very proud of myself!:D

---

### Post by Obor on 2006-08-22
> **abelthorne said:**
> Maybe you should try to reconfigure X : **sudo dpkg-reconfigure xserver-xorg** (make a backup of your /etc/X11/xorg.conf before).

Thanks, didn't help. I can login and everything is fine in safe mode but if I go back to normal mode I can login, get the splash screen and then its just the desktop background colour and the top panel flashes few times (with nothing on it) and thats it.

Its on my spare PC so I think I'll leave it for a day and hopefully  a new package will be released soon. 

Note to myself: Remember to never install new packages on the first day when they come out.

---

### Post by dcstar on 2006-08-22
> **Obor said:**
> 
.......
Note to myself: Remember to never install new packages on the first day when they come out.
Well, given the number of security issues you really have to keep up with these days it can be tough to leave things too long.....

Anyway, thanks to those in the thread who provided the solution to this disastrous release, because I can guess that most of the user base who aren't resourceful enough to get to these forums and find the solution are really stuffed now.

I can see a lot of people either reinstalling from scratch or giving up on Linux (for a time, at least) because of something like this which is very, very difficult for a novice user to recover from.

---

### Post by jsully1 on 2006-08-22
> **SeanCM said:**
> This hit me too.  I am new to Ubuntu...linux in general, and was about to reinstall thinking I did something bad.  Thanks for the fix.  I have a lot I need to learn.

Sean

Same exact thing here - thank you for the fix though!

---

### Post by ubuntu_demon on 2006-08-22
I've closed this thread. 

Let's keep this discussion in one place :
[B]
PLEASE READ: The Latest Updates Break the Xserver!
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)[/B]

---

