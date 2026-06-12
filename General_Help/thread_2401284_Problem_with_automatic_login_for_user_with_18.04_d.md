---
title: "Problem with automatic login for user with 18.04 desktop"
date: 2018-09-16
forum: General Help
---

### Post by paligap on 2018-09-16
My machine has just one user - me!

I don't want to have to login  each time after my machine goes into automatic suspend. However I can't  figure out how to stop this.


[LIST]
[*]Settings >> privacy >> automatic screen lock is off. 
[*]Settings >> details >> users >> automatic login is on. 
[/LIST]

I  saw somewhere there is an issue with /etc/gdm3/custom.conf where  "AutomaticLoginEnable" gets set as "True" whereas it's case-sensitive  and should be "true". I've fixed that, but it's not better.

Where am I going wrong?

---

### Post by paligap on 2018-09-22
I have now found the solution:

Installed dconf editor and set org >> gnome >> desktop >> lockdown >> disable-lock-screen = ON

Seems to me Ubuntu 18.04 ain't 100% playing nice with Gnome...

---

