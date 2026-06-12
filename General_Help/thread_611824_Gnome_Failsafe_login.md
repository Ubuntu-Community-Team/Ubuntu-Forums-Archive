---
title: "Gnome Failsafe login?"
date: 2007-11-13
forum: General Help
---

### Post by DrObviousSo on 2007-11-13
I'm having some problems with my current install.  When I log in (as the only account) as normal, the system slows way down.  It's practically unusable.  I tried logging in as a Gnome Failsafe session, and am having no problems.

I've googled around, and haven't been able to find out exactly what the difference is so that I can try to debug my problems.  Does any know know what the differences are, or have a link that explains it?

Much appreciated.

---

### Post by DrObviousSo on 2007-11-15
Bump.  Still haven't been able to find the answer to this.

---

### Post by knutschr on 2007-11-15
As you know, the main difference is that xserver dosn't run in Failsafe mode.
I think there is something wrong with your x.
I know xserver-xgl can terribly slow down everything.

try
```

sudo remove xserver-xgl

```

---

### Post by DrObviousSo on 2007-11-15
Thanks, that solved my problem.  For anyone else, the command is actually ```
sudo apt-get remove xserver-xgl
```.

---

