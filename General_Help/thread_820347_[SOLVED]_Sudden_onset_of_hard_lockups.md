---
title: "[SOLVED] Sudden onset of hard lockups"
date: 2008-06-06
forum: General Help
---

### Post by Dyqik on 2008-06-06
I'm suddenly suffering hard system lockups that force me to reboot my laptop. 

I'm running Hardy x64 on a new Thinkpad T61 with an nvidia NVS140m Quadra card and 4GB of RAM, and connected to a wireless network.  I'm running compiz with various extra plugins (all from the ubuntu repositories), screenlets and timevault.  I ran the update manager yesterday, and succesfully used the machine all day.  This morning on rebooting I've had two lockups in half an hour.

Everything freezes (with both CPUs maxed out).  No response from any keys, including things like the fn+PgUp key that would usually turn the keyboard illumination led on and off and the caps lock key flashes.  I can't find any relevant log entries for this.

Both have occurred while scrolling around in firefox-2, with evolution running in the background, connected to an exchange server.  This occurred on very different webpages ([www.guardian.co.uk](www.guardian.co.uk) and [www.nukees.com](www.nukees.com)).

Is there any sensible way I can try and diagnose this problem?  I'm unable to try to log in to the laptop remotely due to the network setup at work.

---

### Post by nick_h on 2008-06-06
Have a look in your log files to see if there are any relevant entries.

Try disabling compiz, it can sometimes cause problems.

Instead of a hard boot try using the [Magic SysRq](http://ubuntuforums.org/showthread.php?t=617349) keys.

---

### Post by Dyqik on 2008-06-07
I don't have any log entries from these lock ups.  On the other hand, I applied yesterday's updates and the lock ups have vanished for now.  Just don't ask me why.

---

