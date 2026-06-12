---
title: "Keyboard layout doesn\t apply or change_"
date: 2007-11-11
forum: General Help
---

### Post by nooby on 2007-11-11
I am on WUBI Kubuntu and try to do keyboard layout to be compatible with Scandinaian layout. That worked in Wubi 7.04.04 but now I am on 7.1 build 385. and I choosed Kubuntu instead of ubuntu that uses GNU. 

I fail to do the chars I need like the apostrof you need for I am shorten to I m where itdo a I\m instead for the little tic. 

I told it to use se as in Sweden layout and clicked on Apply but it didn\t change. 

Am I supposed to restart something. Do I have to reboot

---

### Post by nooby on 2007-11-11
I managed to get the tick in I'm now but not the quotes chars and Dash is absent too, 

I fail to do edit here but it worked in the Kubuntu forum. Different board system using different Edit requirements on installation. 

äö but not the a with a ring. 

Could someone help?

---

### Post by ago on 2007-11-11
Not really familiar with kde, but as far as wubi go you can check the top of ubuntu/install/preseed.cfg whether the keyboard is correct. The file is generated when you run wubi.

---

### Post by nooby on 2007-11-11
Ago, yes but too late now. The unclean shutdown forced me to use the power button of my XCCube and that operation killed my LAN card. So I need to buy a new LAN card that fit in the small format of this mini barebone. 

Linux has to warn about which Hard Ware that Linux is disastrous to use on. MZ915 is this one. Has never got the shutdown to work on it. under wubi. 

I deleted linux on it now. I give up on using Linux on this hardware.

---

### Post by ago on 2007-11-12
I somehow doubt that a hard reboot can kill a lan card... If that is the case it is due to the hardware and not the OS...

---

### Post by nooby on 2007-11-12
Ago, 

I Talked to the Computer shop guy and he explained that when Linux shut down uncleanly then most likely this created a conflict when I started Windows so the internal security or protect sensed this and disabled the LAN circuity from overheating due to the short that conflict create. It is not confirmed by the Aopen folks but it sounds likely. 




**Here is how to get LAN going again.**

Hit the Delete button when you see the Aopen logo before windows start loading. Hit it again and again until you see the choices and then go down to Periphericals. 

There you change LAN to disable and do F10 and yes for save and then you let windows load and you go to start and shut the computer down the proper way. That makes the conflict go away and the security protection is lifted and the Windows System will find the LAN Card again

Then you restart your Aopen  with the On button hit Delete again and again and then Enable hit F10 and Yes and then you go to System in the Control panel and go look for the Ethernet LAN card and you enable it and the LAN works again.

Wow I feel so lucky. :)

But Linux seems hard to get working on this Aopen Xc Cube MZ 915 Intel chip set computer. One should not be a newbie like me to get it going. 

Ago it is more likely that it was the non-proper shut down that caused it than a hardware failure. 

But it is the driver for the shutdown process that is not linux friendly. 

Intel obviously has told Windows programmers to do a proper shut down but Linux programmer has either not access to that document or they don't want to allow it. 

Intel should warn all buyers from trying to use Linux on this Aopen machine.

---

### Post by ago on 2007-11-12
> **nooby said:**
> Ago, 

I Talked to the Computer shop guy and he explained that when Linux shut down uncleanly then most likely this created a conflict when I started Windows so the internal security or protect sensed this and disabled the LAN circuity from overheating due to the short that conflict create. It is not confirmed by the Aopen folks but it sounds likely. 

It doesn't sound very plausible to me... There is no way to do a "proper hard reboot", whether in Linux or in Windows... Just look at the web and see how many people ended up with a corrupted windows filesystem because the power went down during I/O operations (that is with only windows, no wubi or linux)...  That said hard reboots should only affect the filesystem, not the hardware... Maybe this "protection" is some TCP "security" which looks at the filesystem to see if everything is ok and possibly requires a "TCP-aware" OS (such as vista)... [http://en.wikipedia.org/wiki/Trusted_Computing_Platform_Alliance](http://en.wikipedia.org/wiki/Trusted_Computing_Platform_Alliance)

...what they call "security", I call "screwing the users"...

---

### Post by StephaneLenclud on 2008-02-05
I've been running Open Suse 10 then Ubuntu 6.10 then 7.04 on a XCcube MZ 915 for over 2 years now and never got any hardware problem. I use it as a server and it runs 24/7; nevertheless I installed and use the Ubuntu GNOME Desktop.

It's true that it won't power off the hardware even though Linux does shut down properly you still have to hold down the power button for 4 seconds to cut the power off. 

Since I hardly ever power off my server it's no problem to me; besides as a desktop user I would not consider this a problem either.

I'm currently in the process of upgrading to Ubuntu 7.10.

Thank you nooby for sharing your problem and the solution with the community.

---

### Post by xcube915 on 2008-02-10
Shut Problems!!

I experienced the same annoying problems on my MZ915, if you can accept shutting down by pressing the button for 4 sec. that works for me as well.
But I did some testing with other distros to see weather it was just my HW which had the problem.

Test results:
Ubuntu :(
Mint :(
Mepis :(
Feora :(
PCLinuxOS :)
Mandriva :)

Since some distros handles the problem I expect that a hardcore Ubuntu hacker can easily solve this problem - Mr. Hacker please help us:)

---

### Post by xcube915 on 2008-02-10
**Shutdown problem has a work around** :)

I googled to find a solution and found this note and now my MZ915 are closing nicely in Ubuntu 7.10, Thanks to the guy named "larryleezard" who ever you are!


[I]The one I suspect that did the trick was suggested by a user called larryleezard:

1. edit /etc/init.d/halt script:

               sudo gedit /etc/init.d/halt

2. add the following to the top of the script:

              rmmod snd-hda-intel

3. save and finally try and shutdown ubuntu..........[/I]

---

### Post by ago on 2008-02-10
> **xcube915 said:**
> Shut Problems!!

I experienced the same annoying problems on my MZ915, if you can accept shutting down by pressing the button for 4 sec. that works for me as well.
But I did some testing with other distros to see weather it was just my HW which had the problem.

Test results:
Ubuntu :(
Mint :(
Mepis :(
Feora :(
PCLinuxOS :)
Mandriva :)

Since some distros handles the problem I expect that a hardcore Ubuntu hacker can easily solve this problem - Mr. Hacker please help us:)

Looks strange to me, hard reboot issues are dependent on the activity status when the shutdown occurred, so you would have to replicate the exact same setup (same disks mounts, same type of I/O activity when shutting down). Do you mean that the system stops while rebooting and does not complete the reboot cycle?

---

