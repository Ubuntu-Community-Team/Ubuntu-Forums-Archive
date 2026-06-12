---
title: "HIBERNATION is no different than Shut down + Restart... why?"
date: 2008-06-07
forum: General Help
---

### Post by the8thstar on 2008-06-07
Whenever I choose Hibernation, the computer does what it's supposed to do and eventually after more than a minute of disk writing and lagging the power goes off.

Then when I turn it back on, the grub menu greets me and launches Ubuntu. There is no difference whatsoever with a normal boot. The applications I had opened have not been saved in the hibernation process and the computer still takes a minute to load the whole shabang.

[COLOR="Blue"]**So what's the point of hibernation? Can it be fixed? Your help will be greatly appreciated.**[/COLOR]

---

### Post by rampageoberon on 2008-06-07
Hibernate saves the contents of your ram to disk and then shuts down. And when you resume it loads that up into the ram and so restores the previous session.

Its possible that the computer doesn't support hibernate. But i'm not too sure about that.

---

### Post by the8thstar on 2008-06-07
> **rampageoberon said:**
> Hibernate saves the contents of your ram to disk and then shuts down. And when you resume it loads that up into the ram and so restores the previous session.

Its possible that the computer doesn't support hibernate. But i'm not too sure about that.

Hmm, I wonder how I could investigate that.

---

### Post by fragos on 2008-06-07
System-> Preferences-> Sessions-> Session Options tab. If you have "Automatically remember running applications when logging out" is checked the system will boot with whatever applications were running when you shut down. Similar but not quite the same as Hibernate.

---

### Post by the8thstar on 2008-06-08
Thanks **fragos**. I knew about the option but didn't put two and two together on that one! If all else fails, I could *at least *use that.

---

### Post by pointone on 2008-06-08
You need to have a swap partition at least as large as the ammount of RAM you have in your system. Post the output of:

```
cat /proc/swaps
```

---

### Post by the8thstar on 2008-06-08
I'm away from my Ubuntu computer at the moment. I'll give you the output in a few hours. Stay tuned...

---

### Post by the8thstar on 2008-06-08
Output:

> Filename				Type		Size	Used	Priority
/dev/sda5                               partition	3903752	0	-1

BTW, I did a reinstall of my system and Hibernation works. It's surprisingly slow though... I'm not sure there is a real advantage to it compared with a regular shutdown in the end.

---

