---
title: "Eliminate a 12.04 Setup Splashscreen"
date: 2014-05-15
forum: General Help
---

### Post by BuntuSeriously on 2014-05-15
Greetings.

Wanted to know if it's possible to entirely eliminate the 12.04 splashscreen and background image during setup ops from one end to the other.

In short, I don't need a splashscreen or background image during setup at all (nasty repaint issues), and would like to see what's going on during initial setup boot.  As an aside, having an actual status pane of some reasonable size during setup procedures would be a definite plus as well; but I don't know how feasible that might be...

FWIW, I've tried to resolve the basic matter by pulling "quiet splash" from the setup codeblock in loopback.cfg with no effect.

Thoughts?  Ideas???


Thanks a mugful ;)

---

### Post by plucky on 2014-05-16
> FWIW, I've tried to resolve the basic matter by pulling "quiet splash" from the setup codeblock in loopback.cfg with no effect.

I don't know what "setup codeblock in loopback.cfg" means, but have you tried running ```
sudo update-grub
``` after you removed "quiet splash" from **/etc/default/grub** config file?

Good Luck

---

### Post by BuntuSeriously on 2014-05-16
Thanks, plucky, for dropping by. Here's a [link]("http://www.supergrubdisk.org/wiki/Loopback.cfg") to a good discussion of loopback.cfg

Looks like this might be a broader plymouth issue after all. I'll be digging around in there next...

Have a great day.

---

