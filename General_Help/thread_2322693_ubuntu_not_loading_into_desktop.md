---
title: "ubuntu not loading into desktop"
date: 2016-04-29
forum: General Help
---

### Post by revolutionkiteman on 2016-04-29
error loading qml file//usr/share/plasma/plasmoids/org.kde.panel/contents/ui/main./qml:25:1:plugincannot be loaded for [email]module@org.kde.kquick[/email]controlsaddons:cannot load library/usr/libx86_64-linux-gnu/
guys, this is the error i get after logging in, the only thing on screen is the folder i can use for general items, desktop/etc, this message is at the bottom of the screen with a no entry icon where the k should be, to my knowledge i have not done anything, all was fine till i started up today?

---

### Post by RobGoss on 2016-04-29
Providing your hardware specs might get you the help you need 

When you ask a question here at the forum it's best to give as much details as you possible can Specs, What kinda machine you have and so on

---

### Post by Geoffrey_Arndt on 2016-04-29
What version of Kubuntu are you running?   And have you recently tried to change or update any "themes"?

---

### Post by revolutionkiteman on 2016-04-30
yea sorry, it was a bit late when i posted this as i was out star watching. its a basic hp, n3450&#8221;2.16, 4gb ram with Ubuntu 15.10....well it was. geoffrey, i did a while ago look through that dept but didn&#8217;t set anything, its been running fine for ages bar never shutting down properly, have to use the power button.
i tried recovery mode and used check files etc and nothing works, its weird as it boots just fine to desktop, just can&#8217;t do anything when there

---

### Post by RobGoss on 2016-04-30
> **revolutionkiteman said:**
> yea sorry, it was a bit late when i posted this as i was out star watching. its a basic hp, n3450”2.16, 4gb ram with Ubuntu 15.10....well it was. geoffrey, i did a while ago look through that dept but didn’t set anything, its been running fine for ages bar never shutting down properly, have to use the power button.
i tried recovery mode and used check files etc and nothing works, its weird as it boots just fine to desktop, just can’t do anything when there

Have you try upgrading to 16.04 or at least take it for a test drive and see how that works

I never encountered any shut down problems with any of the distributions I've tryed

---

### Post by revolutionkiteman on 2016-04-30
funny you say that i was going to upgrade yesterday from the desktop!
it doesnt always do it say 80% of the time, i have seen a few threads on it, it seems mainly on hp laptops.
i suppose i would like to get this sorted then upgrade from the desktop, then i know its all ok again, it would also be easier as i had loads of trouble just trying to get boot and loading before
just to ask, could i upgrade from grub? i can&#8217;t get a terminal on the desktop at the moment

---

### Post by Geoffrey_Arndt on 2016-04-30
Ho_Kay . . . . well, . . . . where to start?

>   If you "can't do anything when you get to the desktop" AND it doesn't shut down properly - well . . . you have a broken system.    Not much worth saving except for any important data . . . especially as 15.10 will not be supported in another 2-3 months anyway.

>  Hard shutdowns can cause all kinds of data/file corruption - - so, that may partially be why you "can't do anything" on the desktop.

>  The only returns on a query for HP n3450 that I got was for printers . . . . am just interested in your PC - especially the following specs:

-   how much ram?
-   what processor?  (I3, AMD Turion X2, etc.)?
-   what gpu chipset (Intel integrated, nvidia xxx, amd/ati xxx)?
-   single OS or multi?
-   how much hdd space allocated for ubuntu?

You can't upgrade from grub - - it's just a bootloader, and don't need terminal to upgrade.   Given the state of your system - - would not be wise to do an upgrade anyway.    A new full-install from a USB Flash-Stick or DVD would be the safest option imho.

Just my 2 cents (or what "pence" in UK?).

---

### Post by revolutionkiteman on 2016-05-01
well, i sorted it, the not always shutting down happens a lot and i have been using for around 3 months, it sort of shutdown all activity stops and is left with just a kubuntu on screen so needs the power off button to turn off completly, 
i managed to get a console up and used devel-release-update to go onto 16.04, 
now i need to post for the constant probs on that lol.

---

