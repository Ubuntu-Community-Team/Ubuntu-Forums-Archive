---
title: "Brightness reset on log out"
date: 2015-03-26
forum: General Help
---

### Post by Issam2204 on 2015-03-26
Hello everyone!

I'm having an issue with Ubuntu 14.10 64bit on my HP 250 G3. Basically, every time I log-out, the brightness level gets reset and pushed to its maximum value.

I've already searched online for a solution and indeed now when I reboot the machine, the brightness level gets saved but not when I log out.

The solution I used is to add 
```
exec echo X > /sys/class/backlight/intel_backlight/brightness
```

in /etc/rc.local, just before the last line.

Again, this works for the reboot but not for the log-out.

Any suggestions?

Thank you for your attention :-)

---

### Post by robsoles on 2015-03-26
Assuming perhaps you do that because the 'regular' controls on the laptop are not functioning maybe it has similar issues to this;

[http://askubuntu.com/questions/553713/screen-brightness-cannot-be-changed-after-upgrade-to-14-10](http://askubuntu.com/questions/553713/screen-brightness-cannot-be-changed-after-upgrade-to-14-10)

---

### Post by Issam2204 on 2015-03-26
Thank you for your answer and help!

The keys are already working. Would it be so bad if I was simply annoyed by the fact that the system doesn't save my settings? ;)

---

### Post by robsoles on 2015-03-26
not at all, I recently made a post in another forum regarding some software not honoring my choices so I can hardly say anything against you wanting the same :)

Does it remember the setting you last set with the control keys if your command does not get executed at boot time?

You say that when you log out the brightness snaps to brightest so I assume that if you set it at a reasonable level using the control keys in a session in which your line hasn't been in rc.local and then you add the line and reboot and then when log out it snaps to max brightness rather than what you set with keys in previous session - this being the case I think it is worth reporting as a bug, odd bug too.

If ending the user's session need alter the brightness then it should go to a reasonable default which is unlikely to be full brightness.

---

### Post by Issam2204 on 2015-04-08
It looks like now it's working. I really don't know how or why but it is working :)

Thank you again!

---

### Post by robsoles on 2015-04-08
I love hate that sort of thing - love that it is working, hate that we are not sure why; hopefully it will last :)

---

