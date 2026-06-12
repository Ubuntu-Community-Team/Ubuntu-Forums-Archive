---
title: "[SOLVED] CPU's 100%?!"
date: 2008-05-18
forum: General Help
---

### Post by chris4585 on 2008-05-18
I'm on Openbox, and recently when I run gnome-settings-deamon, my cpu's go up to 100%.  This was happening before with gnome-appearances-properties but only half as bad.  This recently happened when I installed uplashy, and uninstalled it after I tested it during a session, my xserver crashed, I logged back in, and gnome-volume-manager, gnome-settings-deamon, and my xpad were all crazy with my CPU's.  I think it has something to do with gnome-settings-deamon, because when I run gnome-volume-manager, its all fine.

Any ideas?

---

### Post by ibuclaw on 2008-05-18
What is your CPU Clock Speed and RAM size?
Is your swap being used very much?

Try out this little how-to:
[LIST]
[*]Press '**Alt+F2**'
[*]Type in "gconf-editor" into the run app textbox, then hit 'Enter'.
[*]Go into "apps>gnome-power-manager>cpufreq" in the registry.
[*]If **performance_ac** is set above "80", drop it down to around **50** to **70**.
[*]If you run a laptop, set **performance_battery** to around **25**.
[*]Finally, change the value of **policy_ac** and **policy_battery** to **ondemand**.
[/LIST]
If changes aren't immediate, reboot. And see if it's made a better impact on your system power comsumption.

Regards
Iain

---

### Post by chris4585 on 2008-05-18
> **tinivole said:**
> What is your CPU Clock Speed and RAM size?
Is your swap being used very much?

Try out this little how-to:
[LIST]
[*]Press '**Alt+F2**'
[*]Type in "gconf-editor" into the run app textbox, then hit 'Enter'.
[*]Go into "apps>gnome-power-manager>cpufreq" in the registry.
[*]If **performance_ac** is set above "80", drop it down to around **50** to **70**.
[*]If you run a laptop, set **performance_battery** to around **25**.
[*]Finally, change the value of **policy_ac** and **policy_battery** to **ondemand**.
[/LIST]
If changes aren't immediate, reboot. And see if it's made a better impact on your system power comsumption.

Regards
Iain

I have 2GB of ram, 2 dual core athlon 5200+ 

I don't know my clock speed, somehow I fixed the CPU spikes before I read this, but my gtk theme isn't doing as I want, not acting as it did before, I'll try some other things.

Thanks for the help

---

### Post by chris4585 on 2008-05-18
Its not working how I like it, but I'll settle for what I have now, its working for the most part, but not how it was before.

Thanks for the help

---

