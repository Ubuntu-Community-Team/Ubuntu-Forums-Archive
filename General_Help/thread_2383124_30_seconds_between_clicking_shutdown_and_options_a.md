---
title: "30 seconds between clicking shutdown and options appearing"
date: 2018-01-21
forum: General Help
---

### Post by jayram on 2018-01-21
Hi there,  I managed to get 17.10.1 installed (dual boot with windows) and have it set up pretty well I think.  My install is on an M.2 SSD and is quick except when it comes to shutting down.
When I click the shutdown button, the computer hangs for about 30 seconds before giving me the Cancel/Restart/Shut Down options.  If I click cancel and click the shutdown button again the options are displayed instantly.
I tried turning off wifi to see if that as the problem, which I had seen online might be the cause, but with no effect.  After the first boot, the shutdown is always slow.
I am using kernel v4.13.0-25.29.  I did test out some newer kernels, but the same issue remains as well as some bootup problems so stuck with the current kernel.

Is there a log file to check in order to see what is causing the shutdown delay?

---

### Post by lionel4anlominus on 2018-01-21
What SHELL are you using?

---

### Post by jayram on 2018-01-21
echo $0 gives me : bash
$SHELL --version gives me : GNU bash, version 4.4.12(1)-release (x86_64-pc-linux-gnu)

---

### Post by jayram on 2018-01-21
> **lionel4anlominus said:**
> What SHELL are you using?

My desktop shell (if that is what you mean) is Gnome 3 using Arc-darker theme...

---

