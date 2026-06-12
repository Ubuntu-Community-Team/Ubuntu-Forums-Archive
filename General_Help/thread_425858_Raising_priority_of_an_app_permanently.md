---
title: "Raising priority of an app permanently"
date: 2007-04-28
forum: General Help
---

### Post by Patrick K on 2007-04-28
I've been having playback problems in Audacity (breaking up sound). I tried raising the priority to -10 and this corrected the problem. 

I tried editing the launcher with "nice -10 audacity", "sudo nice -10 audacity", and "gksu nice -10 audacity". Nice -10 set the priority at 10. The others wouldn't launch. I found several post on how to lower the priority but none on raising it. 

How can I permanently set the priority of Audacity to "nice -10"?

---

### Post by Jussi Kukkonen on 2007-04-28
First, running something as root is usually not the right answer. This is a bit tricky however.
> 
I tried raising the priority to -10 and this corrected the problem. ... I tried editing the launcher with "nice -10 audacity"
*nice -n-10 audacity* is the command, but you'll need to be root to start processes with a higher priority...   The nicest solution is probably adding 
```
yourusername ALL = NOPASSWD:/bin/nice -n-10 audacity
``` to the end of /etc/sudoers (I didn't test, but that should give your user passwordless access to that exact command)

---

### Post by Patrick K on 2007-04-28
I don't like running as root but I have to run Jackd as root to get realtime access (I started a thread about this but haven't received any answers).

Anyway, I'm having a problem writing to the sudoers file. I used "sudo visudo" and the file opened in the terminal (maybe with the nano editor). I did a "ctrl b" to make a backup then added the line (with a #note) then "ctrl o" and OKed overwriting the existing file. It seemed to write the file but didn't. When I look at the file in the editor the lines I put in are gone, as is the backup file. What am I doing wrong?

---

### Post by Patrick K on 2007-04-28
I found another way that might allow higher priority. "/etc/security/limits.conf" sets limits on groups. I can set my main group or the audio group at priority -10, however most all processes are set to this. Audacity doesn't breakup but the mouse is very jumpy. I don't know if there is another way to use this file to get just the audio processes to run at a higher priority without raising the priority of all processes.  Thoughts?

---

### Post by Patrick K on 2007-04-29
bump

---

### Post by Patrick K on 2007-05-02
bump

---

