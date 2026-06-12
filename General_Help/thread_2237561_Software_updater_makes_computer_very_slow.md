---
title: "Software updater makes computer very slow"
date: 2014-08-02
forum: General Help
---

### Post by Daan_Celie on 2014-08-02
Hi there,

I'm running Ubuntu 14.04 on my HTPC for a while now and it's running okay (not fast but okay). Except every time Ubuntu Software Updater opens itself (which is every day), my computer gets unbearably slow. After the updater has opened, I can barely do anything on my computer anymore. I know I can disable the Software Updater but I'm looking for a solution, not a workaround.

Thanks

---

### Post by philinux on 2014-08-02
Change the settings to update once per week.

---

### Post by startas on 2014-08-02
Well, that thing is a piece of *thing that goes down the toilet*, just disable automatic updates and use terminal "sudo apt-get update" "sudo apt-get upgrade". There is some software in ubuntu, that is very much broken for like 10+ years, so i do not expect it to be fixed in this age - this includes automatic updater gui, synaptics gui, some other programs.

---

### Post by ian-weisser on 2014-08-02
> **Daan_Celie said:**
> Except every time Ubuntu Software Updater opens itself (which is every day), my computer gets unbearably slow.

Since your system seems 'just okay' (slightly sluggish?) under normal operation, you might be running low on RAM or CPU capacity. A normal update/upgrade does require a bit of RAM and CPU, you know. Not a huge amount, but perhaps you have little to spare.

Check 'top' and 'free' after a restart, and before, during (if possible), and after a Software-updater-caused slowdown.
Try to determine of the slowdown is due to cpu or memory.

---

