---
title: "New firefox version - History bug"
date: 2005-07-21
forum: General Help
---

### Post by peter07 on 2005-07-21
I've just upgrade my firefox. I've used standard ubuntu actualization. Now, each time I want to turn on history - firefox crashed. Why?
> 
Firefox version 1.0.2-0ubuntu5.4

---

### Post by lupo on 2005-07-21
Hi,
that's unfortunately not the only bug.
Read:
[http://ubuntuforums.org/showthread.php?t=50686](http://ubuntuforums.org/showthread.php?t=50686)

---

### Post by roman_PL on 2005-07-21
[QUOTE=peter07]I've just upgrade my firefox. I've used standard ubuntu actualization. Now, each time I want to turn on history - firefox crashed. Why?[/QUOTE]
 Had the same problem. So I removed /var/lib/mozilla-firefox directory (whole dir, with all subdirs in it - don't be afraid, these are only program files, your data like config, history, cache, extensions etc. will remain intact in /home) and then reinstalled Firefox.
And now - no problem with Ctrl-H. And no others problem like Ctrl-W problem or extensions (as mentioned in [http://ubuntuforums.org/showthread.php?t=50686)](http://ubuntuforums.org/showthread.php?t=50686)).
HTH

---

### Post by easy_target on 2005-07-21
[QUOTE=roman_PL]Had the same problem. So I removed /var/lib/mozilla-firefox directory (whole dir, with all subdirs in it - don't be afraid, these are only program files, your data like config, history, cache, extensions etc. will remain intact in /home) and then reinstalled Firefox.
And now - no problem with Ctrl-H. And no others problem like Ctrl-W problem or extensions (as mentioned in [http://ubuntuforums.org/showthread.php?t=50686)](http://ubuntuforums.org/showthread.php?t=50686)).
HTH[/QUOTE]
 I tried it and it didn't work. Firefox still crashes when I click the history.
Any solutions?

---

### Post by bpilgrim1979 on 2005-07-22
Hey people, I don't know what's going on with the recent firefox update.

But another approach is start firefox with firefox -profilemanager and then delete your existing default profile (the one with all the extensions).  Then create a new profile.  For me, that new profile started firefox without problems (until I tried to install extensions again).

---

### Post by manicka on 2005-07-22
I'm using 1.0.6 from backports and these issues don't exist. It might be worth giving it a go

---

