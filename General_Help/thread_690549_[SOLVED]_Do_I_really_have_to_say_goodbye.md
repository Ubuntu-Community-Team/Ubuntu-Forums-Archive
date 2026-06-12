---
title: "[SOLVED] Do I really have to say goodbye"
date: 2008-02-07
forum: General Help
---

### Post by Thingymebob on 2008-02-07
Aaaargh!!

I love Ubuntu, I've been using it for at least 2 years now with no real problems. However At the beginning of the week I powered up my laptop and it immediately shutdown again before getting to a login.

So I boot in single user mode so I can see whats going on 
```
ACPI Critical point reached (95 C)
SYSTEM WILL NOW HALT
TERMINATING PROCESS....ETC/ETC/ETC
``` or something like. I can't remember exactly.
Now I know the machine is nowhere near that hot (Its been off all night) so  I boot with acpi=off, and get a login but now the login gong repeatedly plays and gnome won't start just sits with a black screen & cursor (which does move) the only session that will start is failsafe with terminal.

So I dig out my install disk and attempt a re-install, again acpi issue so do the acpi=off thing which causes the installer to fail at random points while booting.

Now my hardware appears fine as both Gentoo and Slackware are starting without pain. I am infact typing this from gentoo right now. The logs aren't telling me a lot but maybe some Guru can help.

in the attached are dmesg, syslog, Xorg.log and syslog from Feb 3, (about 15:44 on Feb 3 was the last successfull start).

I really don't want to switch from Ubuntu. I've got it just the way I like it and the whole family switched from MS with no effort. Don't really want to make them switch again

---

### Post by cmnorton on 2008-02-07
Is this an Acer laptop? I cannot tell from the model number. I have an older Acer Travelmate 630, and have had lots of boot/shutdown problems.

Although my problems were not like yours at all, I wound up adjusting a BIOS setting that had something to do with power stepping. I used recommended mode. Shutting it off caused boot problems, and setting it to recommended stopped the boot problems.

Don't give up on Ubuntu; it's got to be something wierd like that.

---

### Post by Thingymebob on 2008-02-07
You guessed it, its an aspire 5103. Although this is the first issue I've had with boot/shutdown did have issues with hibernate/sleep though. BIOS looks really basic and can't see anything in there that would help here but will have another look (about the only things I remember that can be changed are boot sequence and passwords.)

Just another note here, the system has now been up with gentoo for a while and the fans are all cycling normally so I am now 100% confident the acpi message is inaccurate.

Been and checked, absolutely nothing changeable in the BIOS except for what I've already mentioned and turning on/off boot menus/displays

I'm not giving up, thats why I'm here. I love Ubuntu and will stick with it. Laptop will be in pieces this weekend just to make sure the nipper hasn't shoved something in the grills making it cook.

---

### Post by Thingymebob on 2008-02-13
Sorted,

Stripped the laptop at the weekend internal really dusty and a nice thick matt covering the cooling grills although they looked clean from outside and could feel good airflow. cleaned off and all is back to normal.

---

### Post by apetresc on 2008-02-13
Wow, nice :)

So Ubuntu averted what could have turned into a hardware disaster?

---

### Post by Thingymebob on 2008-02-13
It did indeed. Ubuntu succeeded where both Slackware & Gentoo failed

Three Cheers for Ubuntu!=D>

---

