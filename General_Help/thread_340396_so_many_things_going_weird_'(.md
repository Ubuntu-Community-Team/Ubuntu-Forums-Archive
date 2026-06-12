---
title: "so many things going weird :'("
date: 2007-01-17
forum: General Help
---

### Post by Choad on 2007-01-17
weirdness #1
suspending: didnt work by default, so u used the suspend2 kernel patch, howto in this forum somewhere, and it seemed to work. except (and this is a problem all over my laptop) its HUGELY unreliable. if i have used beryl, it wont suspend, even if i have then switched back out of beryl to metacity. fair enough, beryl is beta software, but it also randomly decides it wont suspend on other occasions. i can cold boot the laptop, load up maybe firefox and listen, then try and suspend it and it will just go black but never switch to suspend.

weirdness #2
booting: hugely, HUGELY unreliable, and this is what mostly annoys me about the whole operating system at the moment. i have discovered thismorning that whether i have the power in or not will effect the boot reliability. with the power in, it will boot fine 1/3 of the time, other wise you will boot it and it will get stuck about 1/5 of the way through the boot procedure. boot it a second time and it will get stuck about 2/5 of the way through. a third time, and it will work. with the power out however, this morning i booted it 11 times, and it always got stuck. stick the power in, and it boots fine. (but thats not to say it will NEVER boot with the power out, as i booted it last night with the power out)

ordinarily i would suspect dodgey memory to be the cause of such problems, but thats just not the case because it will run perfectly once its loaded up.

weidness #3
after i first installed it, the sound was perfect. now, it only works if i open up the sound manager and tick the "headphones" checkbox. what the hell is that about?!?!


if anyone has any advice regarding any of these issues, please help! PLEASE! it is frustrating like you would not believe, to have something work/not work seemingly so randomly.

thanks,

---

### Post by Choad on 2007-01-17
oh and some more things, when the power is out, i sometimes get a "[BUG] soft lockup on cpu #0" error on boot

also, here is an error log from one time when the suspend failed

```
Jan 17 01:23:37 richard-laptop gnome-power-manager: (richard) Suspending computer because the lid has been closed on ac power
Jan 17 01:23:38 richard-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 19987
Jan 17 01:23:38 richard-laptop dhclient: removed stale PID file
Jan 17 01:23:38 richard-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jan 17 01:23:38 richard-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jan 17 01:23:38 richard-laptop dhclient: All rights reserved.
Jan 17 01:23:38 richard-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 17 01:23:38 richard-laptop dhclient: 
Jan 17 01:23:38 richard-laptop dhclient: Listening on LPF/eth0/00:a0:d1:c1:ab:2c
[B]Jan 17 01:23:38 richard-laptop dhclient: Sending on   LPF/eth0/00:a0:d1:c1:ab:2c
Jan 17 01:23:38 richard-laptop dhclient: Sending on   Socket/fallback
Jan 17 01:32:13 richard-laptop syslogd 1.4.1#18ubuntu6: restart.[/B]

```

you can see that i waited quite a few seconds before i rebooted it with the power button. it seems to get stuck on some network stuff

could this be hardware related? should i send the laptop back to be replaced?

---

### Post by Choad on 2007-01-17
i've been googling my laptop (zepto znote 6214w) and it seems there are similar reports of errors during boot.

if i was to make a claim against my warranty, would i need any proof of hardware error. i have heard alot of bad things about their customer services etc. i also REALLY NEED this laptop for my uni work. gah this sucks.

---

### Post by Choad on 2007-01-17
such overwhelming response! :P

i have "aquired" a copy of xp, so i will soon enough know whether its hardware or software.

i honestly dont know which i would prefer. my laptop needing replacement would suck because i need a computer, but it would also suck if ubuntu was the cause of all this frustration, and doubly suck to have to regress to windows xp.

---

### Post by Choad on 2007-01-17
well, xp didnt exactly install neatly. it made the rookie mistake of thinking it was installed on partition 3, when in fact it was installed on partition 2. fixed it through ubuntu tho by editing the boot.ini

however, it has thus far booted perfectly, suspended perfectly etc. i will let the battery run down a bit then go back to windows and see if it boots (battery was at 40% when i was getting the cpu error)

had to try 3 times to get in to ubuntu this time. its just not right! i wish i could get by without windows but, i need something reliable and if this cant be fixed then i have no choice :(

---

### Post by Choad on 2007-01-17
ok, well as far as i can tell, all the issues are software related. windows works like a charm

im sure you can apprieciate how bitter this tastes, as i *specifically* bought this laptop with **no os** so i could use it with ubuntu. i picked it out as one that should have worked perfectly.

---

### Post by RandomJoe on 2007-01-17
Unfortunately, I've never had issues anything like you describe, so obviously can't give you any advice.  Based on what I've read over the years, though, I would say your problems are probably related to the ACPI/APM implementation on the laptop.  Booting and suspend in particular are more dependent on how the laptop itself sets up or handles things.

Many manufacturers do rather shoddy implementation of the ACPI/APM specs, and naturally just target making things work with Windows whereas the Linux devs have targeted proper adherence to the specs.

Have you checked to see if there are any BIOS updates for your laptop?  Perhaps they've improved the support...

Other than that, it's kind of a crapshoot.  I've had no trouble with booting like that, but I've also never gotten suspend working reliably either.  Not that I've tried that hard - suspend-to-ram eats the battery too fast for my taste, and a cold boot isn't sufficiently slower than HDD suspend for me to put up with the occasional wierdness (even in Windows).

---

### Post by Choad on 2007-01-17
well thanks for the reply. it was beggining to get lonely in here. i suppose theres always fiesty...

and ill check out bios updates.

i dont understand this area too well.... would bios updates effect things beyond the initial pre-grub boot?

---

