---
title: "Halt/shutdown only Reboots"
date: 2007-06-09
forum: General Help
---

### Post by aschueler on 2007-06-09
As the title indicates.  I am running Kubuntu Feisty, and it was pretty much flawless until a few days ago when I noticed my computer was running when I thought I had turned it off.  It turns out whenever I use the KDE console for shutdown, it reboots or if I use the terminal command "halt", it also reboots.

I have had no hardware changes.

I have down a number of the automatic-type upgrades.

I have no idea where to even look for a log of what happens when I halt/reboot.

I searched to forums and couldn't find the same problem, so if this a repost forgive.

Any idears?

Thanks.

---

### Post by cookies on 2007-06-09
What happens if you try 

```

dcop kdesktop default logout

```


In Konsole

And select the Turn Off command?

---

### Post by aschueler on 2007-06-09
Same thing --

System closes down, close screen for Kubuntu appears, then power supply clicks, and grub shows up again.

---

### Post by aschueler on 2007-06-10
I have determined it's a hardware issue.

Last night I loaded Winders so I could play Thief3, and when I shut down it did the same thing.  I do believe it's my ABIT MOBO and some overclocking I sometimes do.

Anyway sorry for blaming Ubuntu!

#-o

---

### Post by drs305 on 2007-06-23
For the past several weeks I've had the same problem in ubuntu feisty. Shutdown via gui reboots to a sign on screen (my normal boot logs me on automatically). Even terminal command 'shutdown' with switches sometimes returns me to the log on screen instead of turning the machine off. The second attempt via gui or command does shut it off. Strange....

---

### Post by spimby on 2007-08-05
> **aschueler said:**
> As the title indicates.  I am running Kubuntu Feisty, and it was pretty much flawless until a few days ago when I noticed my computer was running when I thought I had turned it off.  It turns out whenever I use the KDE console for shutdown, it reboots or if I use the terminal command "halt", it also reboots.

I have had no hardware changes.

I have down a number of the automatic-type upgrades.

I have no idea where to even look for a log of what happens when I halt/reboot.

I searched to forums and couldn't find the same problem, so if this a repost forgive.

Any idears?

Thanks.

I'm having the same issue. I was using 6.06  with no problem, did the update to 7.04 via the update manager. Everything has (amazingly) been fine, with the exception that now when I choose "shutdown" from the gnome menu, it just reboots.  I've tried: sudo shutdown -h now 
with the same result.   My machine is older with an amd athlon XP 2600 processor and a gigabyte MB with dual bios.  But like I said above, this was not an issue with 6.06.  Any help tracking this down would be greatly appreciated.](*,)

---

### Post by spimby on 2007-08-22
> **spimby said:**
> I'm having the same issue. I was using 6.06  with no problem, did the update to 7.04 via the update manager. Everything has (amazingly) been fine, with the exception that now when I choose "shutdown" from the gnome menu, it just reboots.  I've tried: sudo shutdown -h now 
with the same result.   My machine is older with an amd athlon XP 2600 processor and a gigabyte MB with dual bios.  But like I said above, this was not an issue with 6.06.  Any help tracking this down would be greatly appreciated.](*,)

Suddenly it is now working again (shutdown really shuts down) after I applied updates from last night.  I remember one of them was a JPEG update, but I'm not sure what the other one was.  Is there a log or some other way to see what updates have been applied?

---

