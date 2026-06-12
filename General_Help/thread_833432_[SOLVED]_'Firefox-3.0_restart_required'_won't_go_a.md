---
title: "[SOLVED] 'Firefox-3.0 restart required' won't go away"
date: 2008-06-18
forum: General Help
---

### Post by Thorndeux on 2008-06-18
After the last firefox update I got the little light bulb info sign in the upper panel telling me I had to restart:

> Firefox-3.0 has been upgraded (or reinstalled) and must be restarted. Please quit and restart your web browser now.

I did that, but the message keeps popping up regardless, even after two reboots. Any ideas why it's there and how I can get rid of it?

Thanks,
Thorn

---

### Post by Thorndeux on 2008-06-18
Bump :(

---

### Post by yorkie on 2008-06-18
Hi
 shut down your computer completely then restart.

---

### Post by Sef on 2008-06-18
Don't bump your thread unless 24 hours has gone by since the last post in it.  Othewise you could get an infraction.

---

### Post by Thorndeux on 2008-06-27
> **yorkie said:**
> Hi
 shut down your computer completely then restart.
Thanks, but I've done that many times (and would it be different from a reboot?) - without success.

> **Sef said:**
> Don't bump your thread unless 24 hours has gone by since the last post in it.  Othewise you could get an infraction.
Ok, thanks for the info. As the forum is so active I just saw my thread vanish on page three in no time - I guess I was just impatient :).

The problem still persists. In 'Help>About Mozilla Firefox' I find that the version I'm running is: > Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0
 That should be the latest version, no? So why does Ubuntu think I'm still running the Beta?

---

### Post by cpetercarter on 2008-06-27
Have you tried using Synaptic Package Manager to re-install Firefox?

---

### Post by Thorndeux on 2008-06-27
> **cpetercarter said:**
> Have you tried using Synaptic Package Manager to re-install Firefox? Thanks, that did it, I believe! Sometimes the simple solutions are the best :)

---

### Post by halfB on 2008-08-15
Worked for me too!!
Thanks

---

### Post by rmbzz on 2009-03-08
> **Thorndeux said:**
> After the last firefox update I got the little light bulb info sign in the upper panel telling me I had to restart:



I did that, but the message keeps popping up regardless, even after two reboots. Any ideas why it's there and how I can get rid of it?

Thanks,
Thorn

When you quit firefox are you saving the session?

It appears that if you save the session, firefox does not realize it has been upgraded, but if on exiting you choose quit,
rather than save and quit, the restart message goes away.

---

### Post by 42Sec on 2012-09-12
The real root of this problem is usually a corrupt timestamp of the file at /var/run/firefox-restart-required - just delete it to get rid of the message.

---

