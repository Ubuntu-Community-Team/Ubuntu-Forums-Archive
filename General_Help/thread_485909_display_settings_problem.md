---
title: "display settings problem"
date: 2007-06-27
forum: General Help
---

### Post by xyZen on 2007-06-27
Last night i enabled desktop effects on a fresh install of ubuntu 7.04, rebooted, had a muck around with the settings, decided i didnt like them and disabled the driver.

Rebooted again, entered user name and password, and was persented with a plain white screen and cursor which i cant do anything with.

I think i've manage to change the settings to a point where it doesnt work right, so is there a way to amend them via the terminal?

---

### Post by speaker219 on 2007-06-27
You could try reconfiguring your xorg.conf file:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xyZen on 2007-06-27
i've tried doing that, and i get upto a certain point, hit enter and it returns a warning.

i then reboot and nothing has changed.

This happens both in recovery mode and when i boot into a failsafe xterm session...

---

### Post by xyZen on 2007-06-27
just tried again, same thing happened.

after going through what appears to be all the bits in the reconfigure, it tells me it has overwritten the file, but nothing has changed....

---

### Post by xyZen on 2007-06-27
i've also tried remove compiz beryl, with no luck

---

### Post by mig5 on 2007-06-27
> **xyZen said:**
> Last night i enabled desktop effects on a fresh install of ubuntu 7.04
...

Maybe it would be quicker to just reinstall and start over, seeing as you've only just installed it.  That way it will take you less time than fixing it, hopefully ;).

---

### Post by r4ik on 2007-06-27
[http://ubuntuforums.org/showthread.php?p=2351383#post2351383](http://ubuntuforums.org/showthread.php?p=2351383#post2351383)

try Taurus option.

Good luck !

---

### Post by xyZen on 2007-06-27
got round the problem by creating a new admin user in the recovery console, just having to go back and delete the old one, then re-install compiz beryl now.

cheers for the help anyroad :)

---

