---
title: "System time changes after booting into Ubuntu (dual boot system with win xp)"
date: 2013-04-07
forum: General Help
---

### Post by sud_pai on 2013-04-07
Hi, I have a strange problem with regards to the system time.

I am situated in Mumbai, India, which is +5.30 hours time zone (no daylight savings).  I have windows xp installed on one hard drive and Ubuntu 12.10 installed on the other hard drive (installed each OS disconnecting the other hard drive; Use the boot menu using F12 to boot into each OS). I use win xp most of the times since my work requires me to be on win xp.

I have a strange problem with regard to the system time.  When I boot into Ubuntu, the system time shows correct, but after booting into Ubuntu, if I restart the machine and boot into win xp, the system time changes to -5.30 hours of my time zone. This happens every time and creates problems with my work software requiring me to correct the time and restart the machine before I can start work.

I would like to know the reason behind this and how to rectify this.

---

### Post by Irihapeti on 2013-04-07
I have a suspicion what's happening, but first I'd like to check.

Open the file /etc/default/rcS, scroll down to the lines where it says:

```
# assume that the BIOS clock is set to UTC time (recommended)
```

and tell us whether the next line is set to 
```
UTC=yes
```
or 
```
UTC=no 
```

---

### Post by Impavidus on 2013-04-08
By default Windows sets the BIOS clock to local time, whilst Linux sets it to UTC. So after shutting down Linux the clock is set to UTC, which is interpreted by Windows as if it were local time, giving the 5.30 hour offset. Reconfiguring Windows to use UTC would be the ideal solution (being more robust in case of time zone changes), but it's easier to reconfigure Linux to use local time. This configuration is in /etc/default/rcS.

---

### Post by ppjdee on 2013-04-08
i have the same issue, though my OS is ubuntu/win7. been wondering whats up with it doing this.

---

### Post by Irihapeti on 2013-04-08
What Impavidus said is correct - Ubuntu usually assumes that the BIOS clock is set to UTC, while Windows doesn't. The easiest way to fix it is to edit /etc/default/rcS so that the line:

```
UTC=yes
```
is changed to 
```
UTC=no
```

You can use sudo nano (or other console editor) or gksu gedit (or other gui editor) to do this.

Then reboot. You might need to change the clock one last time, but afterwards it should be OK.

---

### Post by sud_pai on 2013-04-10
Hi, sorry for the delay,

checked the line in the rcS file, and this is what it says:

# assume that the BIOS clock is set to UTC time (recommended)
UTC=yes

---

### Post by Irihapeti on 2013-04-10
You need to change it to 
```
UTC=no
```

That way, Ubuntu reads the BIOS clock as local time, which is what XP is doing. So no need to reset all the time.

Use either 
```
sudo nano /etc/default/rcS
```
or
```
gksu gedit /etc/default/rcS
```

(Or use other editor of your choice)

Once you've done that, reboot and go into the BIOS and set the time to local time.

---

### Post by sud_pai on 2013-04-10
Hi all,

used gksu gedit and edited UTC=yes to UTC=no

system time now does not change and go back 5:30 hours between the 2 OS.

Thank you all for letting me know the reason for the problem and how to solve it.

:)

---

