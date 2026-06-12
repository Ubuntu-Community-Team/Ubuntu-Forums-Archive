---
title: "restricted driver manager tool"
date: 2007-05-28
forum: General Help
---

### Post by krismatth3 on 2007-05-28
ARGH! Why does this tool transparently overwrite /etc/X11/xorg.conf ?!

Some of us might have to .. customize it a little. For example, advanced configuration of a synaptics touchpad, or multiple monitors.

It's very rare in Unix to see a tool that doesn't a: prompt you before overwriting or b: advertise that it's going to overwrite. Now something like "rm" does not prompt for obvious reasons - removing files is it's JOB. Same with cp, mv, etc - you shoot yourself in the foot, its your own fault.

But a tool to remove/install a package? apt-get itself doesn't (by default) overwrite config files, it prompts you.

</rant>

---

