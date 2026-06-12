---
title: "Screen sticks every few minutes"
date: 2013-02-21
forum: General Help
---

### Post by bdecie on 2013-02-21
I am using XUbuntu Precise, a new install.  When running, every few minutes, the screen freezes.  The mouse will still move around the screen, as far as the edges, but will not click or have any effect.  The effect lasts about 5 seconds.  If a job was pending when the screen froze (e.g. one of the slow-responding menus in LibreOffice) it will pop up immediately the screen unlocks, which suggests that the processor is still running threads in the background. This does not seem to be a hardware issue - I have tried with different monitors, and get the same effect.  I have also tried removing as much software as I can from startup, and it makes no difference.  I have checked dmesg and other system logs, and see nothing obviously abnormal, but don't really know where I should be looking.  Any suggestions would be greatly welcomed!!!

---

### Post by Bucky Ball on 2013-02-21
*Thread moved to **General Help**.*

Reason: Nothing to do with desktop environments. ;)

---

### Post by bdecie on 2013-02-21
I am now think this may be to do with lightdm.  Each time the screen sticks, I see the following in the task manager jump to the top of the CPU list using 50% of CPU (1 whole core?). Just after I get control back, it drops to about 10%, and then down to around 5%.

/usr/bin/X -0 -auth /var/run/lightdm/root:0 -nolisten tcp vt7 -novtswitch -background none

Any suggestions?

---

### Post by LewisTM on 2013-02-21
> **/usr/bin/X** -0 -auth /var/run/lightdm/root:0 -nolisten tcp vt7 -novtswitch -background none
That's X11 eating all the CPU. 
Your ~/.xession-errors file might contain a clue. You should definitely investigate your X server configuration, could be a driver issue. You should also disable composition and see if that help: Settings->Window Manager Teaks->Compositor->Disable display compositing.

Good luck!

---

### Post by bdecie on 2013-02-21
Thanks for the suggestions LewisTM.
.xsession-errors shows nothing unexpected (one or two misfires on an smb mounted drive)
disabled composition - no significant effect.
removed cairo-dock - better, but still occasionally sticking. (I've been using cairo on this computer for ages without problems...).  Don't have compiz, conky so not a problem.
Checked davmail - it uses java to get exchange, but activity does not coincide with slowdowns.
drivers - not sure what I should look for. Will investigate, but it's a very ordinary Intel chip, and all my previous versions of XUbuntu never had any problem with it.

---

### Post by bdecie on 2013-02-21
Tried deleting various panel buttons. One had a significant effect - the window selector.  Replaced it with the menu version. Much better.
Gave up searching for other problem threads, checked CPU - running on demand never goes up to full speed, so installed a little script to swith the governor from on demand to full performance. At full performance the screen twitch seems to have disappeared altogether.  This is a kludge, but I will live with it until I have any better ideas, so I'm marking the thread solved.  Thanks to all who helped!:)

---

