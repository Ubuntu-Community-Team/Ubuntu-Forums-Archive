---
title: "strange behavior - attack?"
date: 2007-05-24
forum: General Help
---

### Post by googlebytes on 2007-05-24
I guess I got overly confident in Ubuntu, and I left my internet plugged in.  Came back later, and the processor was working away so much, that the screen wouldn't come up. It is connected through my router/modem/firewall. Plus, I installed the Firestarter firewall. 
So what's the deal? I know it's not a whole lot of info to go on, but it seems my computer was under attack?
How can I find out? How can I tell what program is trying to run on Ubuntu? In Windows the magic keys are <Ctrl> <Alt> <delete>

---

### Post by ruy_lopez on 2007-05-24
You should check your system logs, for the time period when it happened, it might just have been a hardware flakeout, and not an attack after all. 

If you don't have any open ports, and you have the firewall setup correctly, it is hard to attack a system like that.  And if it hasn't happened since then its unlikely it was an attack, because the only other way through those defenses would have been to download something yourself. 

When your system freezes like that, the only the you can do is press and hold the power button for five seconds, until you hear it switch off. Definitely check your logs, though.

---

### Post by googlebytes on 2007-05-24
Thank you for your reply - Scotland that is cool - it's our family homeland.
I am a NooB, and I can't get System Log to show anything but the logs for the current date. If I click on a date on the calendar, nothing happens. If I go to Open Log, just about all the files for prior dates are in .gz format, and won't open. Plus, they are scrambled in with all the other dates.

System Monitor seems to just deal with the current programs running.

All suggestions please...

---

### Post by onbongos on 2007-05-24
i would suspect either the software firewall or a screensaver was having some difficulty

---

### Post by fanatik on 2007-05-24
if you can get a terminal open, type **top **to show whats using the most CPU/memory etc.

---

### Post by aktiwers on 2007-05-24
Or you can install the CRTL+ALT+DELETE thing with automatix. It makes your system monitor show up like in windows, when you hit control alt delete.  The only other way to show it, I know, is to add the CPU applet in gnome panels and then click on it.

Oh wait..
System => Administration=>System Monitore
Shows it too. :)

---

