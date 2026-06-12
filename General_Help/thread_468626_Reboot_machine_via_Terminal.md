---
title: "Reboot machine via Terminal?"
date: 2007-06-09
forum: General Help
---

### Post by _simon_ on 2007-06-09
First some background, I have a Razor Copperhead mouse and you may or may not know that there is currently a problem with it being detected on boot in that you have to unplug and plug it back in fo it to work.

I have found that if I shutdown via terminal with ```
sudo shutdown -h now
``` that the mouse DOES get detected on boot, however I need to know a command that will work for restarting the machine as well.

I know that Alt + SysRq +b will do a reboot but that skips the whole shutdown process, so I guess it won't do my install much good?

---

### Post by thelinuxguy on 2007-06-09
Doesn't the -r switch do a reboot? Or did I miss anything in your question?

Regards.

---

### Post by PointSource on 2007-06-09
Or just simply:
```
sudo reboot
```

---

### Post by Dekunuts on 2007-06-09
yes 'sudo reboot now' will do

---

### Post by _simon_ on 2007-06-09
> **thelinuxguy said:**
> Doesn't the -r switch do a reboot? Or did I miss anything in your question?

Regards.

Now I feel very stupid!

Thanks guys, I'll use the -r switch as I've just tested it and the mouse still works on boot :)

---

### Post by _simon_ on 2007-06-09
Is there anyway to do this without being prompted for my password?

---

### Post by thelinuxguy on 2007-06-09
> **_simon_ said:**
> Is there anyway to do this without being prompted for my password?

Take a look at this (for Gentoo): [http://forums.gentoo.org/viewtopic-t-561399-highlight-granting+permission+hibernate.html](http://forums.gentoo.org/viewtopic-t-561399-highlight-granting+permission+hibernate.html)

---

### Post by _simon_ on 2007-06-09
Well I worked out how to add it to sudoers but if I do that, then the mouse doesn't work on boot :?:

---

### Post by thelinuxguy on 2007-06-10
> **_simon_ said:**
> Well I worked out how to add it to sudoers but if I do that, then the mouse doesn't work on boot :?:

Does it happen on EVERY reboot? Consistently? I doubt if they are related. 
Even if they are, I cant think of any specific reason. Lets see if someone else has the same problem or knows the solution.

---

### Post by _simon_ on 2007-06-10
Yep.

If I shutdown or reboot normally (System -> Quit)  then the mouse does NOT work, without fail.
If I shurdown or reboot via terminal with entering my password then on boot the mouse DOES work, every time without fail.
If I add myself to suoders so that I don't have to enter the password for shutdown or reboot then it does NOT work on boot.

I only worked it out because I had 3 power cuts recently so my machine did not shutdown properly, and low and behold on each boot the mouse worked.

---

### Post by nqsonk9 on 2007-06-10
Hi, I'm looking for the command to open the LOGOUT box of Gnome? Anybody any suggestion ?
Thnks

---

