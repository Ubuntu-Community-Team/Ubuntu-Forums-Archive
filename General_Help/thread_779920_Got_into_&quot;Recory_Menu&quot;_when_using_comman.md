---
title: "Got into &quot;Recory Menu&quot; when using command &quot;sudo shutdown now&quot;"
date: 2008-05-03
forum: General Help
---

### Post by fird on 2008-05-03
When I used the ```
sudo shutdown now
``` command to shutdown my Ubuntu8.04, I always got into a blue "Recovery Menu" dialog box in text mode asking me to choose: Resume, Root or xfix. And the computer won't shutdown properly.

I got the same problem on my laptop and my friend's. Mine is using an ATI x1300 video card and my friend's is Intel onboard.

---

### Post by spec-chum on 2008-05-03
What happens if you do
```

sudo shutdown -h now

```

The -h flag sends the request that the system should be halted or powered off.

---

### Post by fird on 2008-05-03
Thank you. It does solve my problem.

---

### Post by gotee12 on 2008-05-13
Not to beat a dead horse, but my PC has started to exhibit this same "recovery menu" problem anytime I use...

```
sudo shutdown now
```

This problem didn't pop up until after the SSH critical updates and gnome updates were downloading and installed today ( 3-13-08 ). Before applying today's patches, sudo shutdown worked fine from the CLI.

Any ideas? Thanx in advance...

---

### Post by gotee12 on 2008-05-13
...also....

I am experiencing the same issue on my laptop as well. Both desktop PC and laptop are running 8.04 LTS with all patches applied as of 3-13-08. I'm guessing it's a bug with today's Gnome patches (but what do I know).

I found a (possibly) related [bug on launchpad]("https://bugs.launchpad.net/ubuntu/+bug/216006")...

---

