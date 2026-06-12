---
title: "Temp files that are not so temporary, how do you deal with them."
date: 2014-05-05
forum: General Help
---

### Post by J_Me on 2014-05-05
How do you deal with temporary files that don't get removed after a powerup.
What prompts this question is that I had an issue with a program taking up a large amount of disk space and found by chance that it was storing a temporary file in /var/tmp
Here's the post
[http://ubuntuforums.org/showthread.php?t=2221861](http://ubuntuforums.org/showthread.php?t=2221861)
I came to the conclusion that files stored here can be deleted(but not advisable) and if the program breaks just remove and reinstall, but there has to be a cleaner way to deal with things like this.
Also where are the places other than "/tmp, /var/tmp, trash, .whatEver" temporary files maybe stored.
Thanks

---

### Post by HermanAB on 2014-05-05
Uhmmm, your /tmp should be a RAM disk (tmpfs) and other tmp directories should be soft links to /tmp.

Obviously then when you reboot, it will be empty.

---

### Post by philinux on 2014-05-05
Moved to General Help forum.

---

### Post by ian-weisser on 2014-05-05
You often have temporary files that you _want_ to persist across a restart in /home/$USER/.cache
Your browser cache, for example.

Many applications that have temporary files that reside in /var specifically to persist across restarts, but frequently change or are otherwise not intended to last forever.
Logs, crash reports, game high scores, temporary backup files, system databases (xapian, fonts, manpages, etc.)

Example: I wrote an application that generates customized bus schedule for each day. It uses /var to store each day's (temporary) output.

If some application is generating _huge_ files, or otherwise affects system performance, please file a bug report - it seems unlikely the developers intended that behavior.

---

### Post by J_Me on 2014-05-05
@ian-weisser
Thanks for that explanation, things are much clearer now.

@HermanAB
Yes I understand what you are saying but the /var/tmp file wasn't removed even after a power cycle and I had no obvious way of knowing where that extra disk space went.

Anyway I'll keep an eye on the /var file in future if I suddenly lose disk space. When you use an SSD every Gig makes a difference.

Thanks again

---

### Post by Lars Noodén on 2014-05-05
The directory [/var/tmp/](http://manpages.ubuntu.com/manpages/trusty/en/man7/hier.7.html) hold temporary files, but ones that should persist across reboots, unlike for /tmp/.  Normally applications should remove their own temporary files when exiting, but maybe that does not always happen.

---

