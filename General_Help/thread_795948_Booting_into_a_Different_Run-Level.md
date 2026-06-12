---
title: "Booting into a Different Run-Level"
date: 2008-05-16
forum: General Help
---

### Post by flowingfire on 2008-05-16
I have need to boot into the console run-level, but I'm not exactly sure how to do that.  I googled it first, and searched these forums, but I'm just not sure what exactly to look for.

So what do I do to boot into console for a one-time operation? 

I'm running Kubuntu 8.04

---

### Post by sujoy on 2008-05-16
sudo vi /etc/inittab

and change the default runlevel to 2 or 3

---

### Post by flowingfire on 2008-05-16
I typed that (sudo vi /etc/inittab
) into the Konsole, and what came up just confused the heck out of me.  Is there another way to do this?

It just pops up with a bunch of blank lines and a single line on the bottom that doesn't look like anything to do with anything... ?  Also, I couldn't find a file that even remotely resembled /etc/inittab.

---

### Post by fsmithred on 2008-05-16
There is no longer an /etc/inittab file. Changing the default runlevel won't help by itself, and isn't needed. The default runlevel is 2, and runlevels 2,3,4 and 5 all start gdm. Set gdm to start at runlevel 3:

```
sudo update-rc.d -f gdm remove
sudo update-rc.d gdm start 3 4 5 . stop 0 1 2 6 .
```

That will make it so you boot to command line in runlevel 2. If you want to run a graphical environment, you can just type "startx" or you can start gdm with "sudo /etc/init.d/gdm start" or you could switch to a higher runlevel with "sudo init 3".

Also, you might find that nano is easier to use than vi.

---

