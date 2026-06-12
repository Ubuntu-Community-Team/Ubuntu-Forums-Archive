---
title: "Remove w10 completely."
date: 2016-10-07
forum: General Help
---

### Post by dtree46 on 2016-10-07
How does one completely remove W10, then install Ubuntu?

After several crashes using different software, I've had it.

Windows 10 goes.

Any help appreciated.

dlw

---

### Post by QIII on 2016-10-07
Hello!

Although I would recommend shrinking your W10 partition (so you can keep Win10 just in case ...) and installing Ubuntu in its own partition (you can ask about that, too), if you want to install Ubuntu and completely wipe Win10, all you need do is start the Ubuntu installation media and choose "Use Entire Disk" or "Something Else".  "Something Else" gives you more control, but bears some explanation.  "Use Entire Disk" uses some defaults, but is simpler.

Cheers!

---

### Post by Bashing-om on 2016-10-07
dtree46; Hello; Welcome to the forum.

Look. 1st up - going cold turkey off Windows may not be the best approach; There is a learning curve for operating in a linux environment .
See:
[http://ubuntuforums.org/showthread.php?t=2201432](http://ubuntuforums.org/showthread.php?t=2201432) <- ian-weisser; new user frustration
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://ubuntuforums.org/showthread.php?t=2125370](http://ubuntuforums.org/showthread.php?t=2125370) <-ubuntu ain't Windows, DuckHook treatsie
[http://ubuntuforums.org/showthread.php?t=2200144](http://ubuntuforums.org/showthread.php?t=2200144) <-ubuntu ain't Windows, DuckHook treatsie #2, no one says it better !

Now with this in mind, if it is still desired to put Windows behind you it is as simple as on the verified install medium choose:
"erase disk and install ubuntu" .. the install wizard will do just that . You can then be a happy camper .

[INDENT][INDENT]ain't nothing put a thing
[/INDENT][/INDENT]

---

### Post by Impavidus on 2016-10-07
Are you sure you want to wipe Windows? Your software that crashes on Windows may not work at all on Ubuntu. Actually, for sure it won't work on Ubuntu, but there may be an alternative.

But if you want to wipe Windows and install Ubuntu, just create a live disk, boot from it, start the installer and set it to use the entire drive. It will wipe whatever is there and install Ubuntu.

It's not guaranteed everything will work at once, but usually it will in the end.

---

### Post by QIII on 2016-10-07
The fact that you've quickly gotten three suggestions against completely wiping Windows from three Linux users should say something to you!  :)

---

### Post by dtree46 on 2016-10-07
I've had Linux for years. The last several was Ubuntu. Latest (on another box) 14.04LTS.
Bought a new PC with W10. Tried it and as many years ago, do not want it.
This new boot system in W10 has prevented its removal thus far.
After reading these links, I should be able to get rid of it.

Thanks for the info.
dlw

---

### Post by colmax on 2016-10-07
I'm with you Dtree46 as far as windows frustration goes
Figure 2 operating systems are better than 1 until another BeOs comes along
Windows does seem to flash android devices well from what i've read
So maybe it has a place
Still think i'll go winfree in the near future as well
Cheers

---

### Post by MartyBuntu on 2016-10-07
I'm a "Linux Only" person, so if I am to take you at your word about being done with Windows...I say go for it.

Disable Secure Boot in UEFI. If you're only installing a Linux distro on the machine, Secure Boot is more of a hindrance than a benefit.

---

### Post by RobGoss on 2016-10-07
I'm only a Linux user here and have no regrets at all, with 6 machines all running some form of Linux I'm very happy i ditched Windows. I don't hate Windows just because it's Windows I don't care for it any more because you can't enjoy the operating system at all. You spend more time trying to keep it virus free and using it. I can just on any of my Linux machines and actually enjoy a operating system that works

I would advise make sure this is something you really want and have a restore disk handy just in case you change your mind. Good luck and welcome to the Linux world

---

### Post by colmax on 2016-10-07
Hi MartyBuntu great avatar/icon :)
How is phone syncing using linux only
I'm waiting for the next ubuntu phone to be realeased then i'll drop windows
Spose just use cloud storage so os shouldn't matter
Microsoft just went too far with anniversary edition & i'm not gonna accept that
Cheers

---

### Post by kurt18947 on 2016-10-08
One of the nice things about Windows 10 IMO is the ability to restore using media downloaded from Microsoft (make sure you pick the right one - 32 bit vs. 64 bit, home vs. pro, it won't activate otherwise)and it will activate automagically. Doing so should get rid of the shovelware found on new machines. Touch wood but so far no problems dual booting *BUT* my machines are conventional BIOS, not UEFI. I partition my hard drive first using Gparted running from a live distro then install Windows in a 50 GB. NTFS partition.  I believe UEFI machines need a FAT32 /boot partition in addition to the main NTFS partition and I'm sure there are other additional requirements. I also install Windows first then Linux OSs.

---

### Post by dtree46 on 2016-10-08
Update:
Ubuntu starts installing with UEFI mode.
However, my Nividia GTX-745 doesn't play well with Ubuntu.
An Nvidia driver needs installed. That means Ubuntu has to be installed.
Since Ubuntu will not install because of the Nividia card, how, or can this be accomplished.

Any help appreciated.
dlw

---

### Post by Kris_M on 2016-10-08
Just my 2 cents:
I install BIOS, not UEFI because I find it much easier to modify things later. UEFI wants to own things, like your mobo, which I change as needed.
I run win7 and Ubuntu 16.04.1 because I very rarely need win for something. Like the occasional cat scan CD.
If you ever need to flash an android device, win7 is the win of choice.  I stopped that a couple years ago from boredom and the flashes just don't work well.
I run FF, TBird and some old games in wine and dosbox. NWN 1+2, UUW1+2, Stonekeep.  Little stuff like Skype.
I'm a relative noob to Linux and I find this easy with a little help from the folks here.  Google is your friend!
Tried win10, 8.0, 8.1 - btdt - not for me.  Been a win person since win3.1
Just my 2 cents.

---

### Post by colmax on 2016-10-08
Ran nvidia display but it ran too hot so went back to xserver
i don't run anything graphic intensive so xserver will do
Can't believe how hot the nvidia driver ran
gt 740m

---

### Post by Bashing-om on 2016-10-08
dtree46; Hey;

> **dtree46 said:**
> Update:
Ubuntu starts installing with UEFI mode.
However, my Nividia GTX-745 doesn't play well with Ubuntu.
An Nvidia driver needs installed. That means Ubuntu has to be installed.
Since Ubuntu will not install because of the Nividia card, how, or can this be accomplished.

Any help appreciated.
dlw

A common kernel (boot)parameter is nomodeset, which is needed for some graphic cards that otherwise boot into a black screen or show corrupted splash screen. See : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter .
From here one can install the needed proprietary graphic's driver .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by dtree46 on 2016-10-09
Success, Thanks guys.

dlw

---

### Post by RobGoss on 2016-10-09
That's great if you were able to fix your issue and are content with the out come you can mark this thread as solved. You can use the **Thread tool** at the top of this post. thanks

---

### Post by Bashing-om on 2016-10-09
dtree46; Great !

Pleased ya up and running :)

As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]we look forward to the next adventure
[/INDENT][/INDENT]

---

