---
title: "Battery Management Icon disappears"
date: 2007-11-26
forum: General Help
---

### Post by FeraTech on 2007-11-26
On my laptop my battery management icon strangely disappears. It won't show up when booting. However, it does occasionally make an appearance only to disappear again.

This started happening when installing Alltray. However, I would prefer not to get rid of Alltray since it's the only way to be able to have Thunderbird running in the background and at startup.

Other alternatives or solutions to my battery problem would be helpful.

Since this is a laptop not having the battery meter is a pretty large problem so any help is greatly appreciated.

---

### Post by aashay on 2007-11-26
Try adding the "Battery Charge Monitor" applet to the panel.

---

### Post by scyhe on 2007-11-28
I have the same problem. The icon dissapeared and i've never seen it again.
Not only that icon but the update icon as well:(

> "Battery Charge Monitor"

That manager doesn't work.It says that there's no battery. What i've seen is that on the /proc/acpi/battery directory when i do "ls", the output is null (the dir is empty:confused:), so i guess the OS just can't detect my battery anymore, but i'm not sure.

Anyway my ubuntu is feisty fawn 7.04 and my laptop is a acer TravelMate 4000.

Any help would be very apreciated
10x

---

### Post by aashay on 2007-11-28
Update and battery icon missing. I'm guessing you could try adding 'notification area' to the panel

---

### Post by scyhe on 2007-11-30
Yeah that fixed the problem of  adding the icon, but the aplication doesn't work. I guess the problem resides on the fact it doesn't detect my battery

---

### Post by toasterboy1 on 2007-12-12
I noticed my battery meter had disappeared as well. I had tried many different things and got klaptop to run. But while searching for solutions to my problem being able to access my other partitions I ran across a post by Frunktz.

> **Frunktz said:**
> I resolved!
Try to change in /etc/init.d/rc the concurrency=none option.
I've set concurrency=shell and HAL has broken down.

So I change to currency=none.  Rebooted and my battery monitor showed up and I can access my partitions. Two for one.

---

### Post by n838901 on 2008-05-18
Open 'Power Management' under 'System/Preferences'. Click the 'General' tab, and select 'Always display an icon'.  That fixed it for me.

---

