---
title: "Magic SysRq Key"
date: 2008-04-10
forum: General Help
---

### Post by intense.ego on 2008-04-10
Link: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

I have a few questions:

how can this be used to recover from freezing like the article says at the start?

what's the advantage of a soft reboot, as opposed to me holding down the power key?

---

### Post by Ozor Mox on 2008-04-10
> how can this be used to recover from freezing like the article says at the start?

```
SysRq + Alt + REISUB
```

Hold SysRq and Alt down, and press each letter a few seconds apart. That will reboot a locked up machine after making sure all disks are unmounted and processes are terminated etc.

> what's the advantage of a soft reboot, as opposed to me holding down the power key?

There should be less chance of corruption of data on the hard disk, since the system attempts to shut down as best it can instead of just cutting the power.

---

### Post by klange on 2008-04-10
Here's my mnemonic : (Arr!) Everything Is Shitty! Un-Boot!


[size="1"]Wow, I really can't spell.[/size]

---

### Post by 3rdalbum on 2008-04-10
> **WindowsSucks said:**
> Here's my pneumonic: (Arr!) Everything Is Shitty! Un-Boot!

That's the first magic-key mnemonic that I'll actually remember. I can't stop laughing!

(Actually, I find that the "r" sometimes stops the combinations from working. But sometimes the "r" will cause you to be able to switch to a VT, which is really good.

---

### Post by zmjjmz on 2008-04-10
I have a MacBook keyboard, does anyone know what the SysRq key combo would be?

---

### Post by Polygon on 2008-04-10
On a mac keyboard, they seem to have like f 13 - 16, sysrq MIGHT be f13 since sysrq is right after f12 on my keyboard.

And the advantage to doing this it that it allows programs to possibly do an emergency save of whatever your doing, and gives the hard drives a chance to actually stop and unmount. Just remember to do each letter a few seconds apart.

---

### Post by zmjjmz on 2008-04-10
Macbooks only go up to F12.  Maybe it's the Eject key? I'll try it next time my computer crashes.

---

### Post by aaaantoine on 2008-04-11
When my computer seems to hard lock, I can often hit R, and then Ctrl+Alt+Delete.  And then Ubuntu reboots normally (even showing the splash screen towards the end of the shutdown process).

I suppose if that didn't work, I would go ahead and finish the pattern.  But I haven't had that problem yet.

---

### Post by Mazza558 on 2008-04-11
Be warned that in Hardy, even RSEIUB doesn't work with a particularly nasty crash which makes the screen go blank.

---

### Post by dizee on 2008-04-11
Alt + SysRq + R E I S U B has saved me a few times, extremely useful and much better than a hard reset. I remember it as "busier" backwards.

---

### Post by Penguin Power on 2008-04-11
So, to echo the question of an earlier poster, where is the sysrq key on our nasty, freedom-hating MacBooks? :P

---

### Post by intense.ego on 2008-04-11
What is it for normal laptops? ALT + Fn + PrtSc/SysRq?

---

### Post by Mazza558 on 2008-04-12
> **intense.ego said:**
> What is it for normal laptops? ALT + Fn + PrtSc/SysRq?

It's the same as normal desktops.

---

### Post by K.Mandla on 2008-04-12
Moved to General Help.

By the way, if it hasn't been mentioned already, PmDematagoda put together a [great tutorial]("http://ubuntuforums.org/showthread.php?t=617349") regarding the Magic SysRq keys.

---

### Post by klange on 2008-04-12
> **intense.ego said:**
> What is it for normal laptops? ALT + Fn + PrtSc/SysRq?

Should just be Alt+PrtSc, tried it for myself when I had to restart (for normal reasons) on my laptop and it worked great. Brought up Gnome-Screenshot, though...

---

### Post by intense.ego on 2008-04-12
> **K.Mandla said:**
> Moved to General Help.

By the way, if it hasn't been mentioned already, PmDematagoda put together a [great tutorial]("http://ubuntuforums.org/showthread.php?t=617349") regarding the Magic SysRq keys.

Thank you, that guide was great.

---

### Post by Penguin Power on 2008-04-12
Broken record: MacBook...MacBook...MacBook... 

Hardy keeps crashing on my MacBook and I have to hard reboot :(

---

### Post by flaggh on 2008-05-10
> **Penguin Power said:**
> Broken record: MacBook...MacBook...MacBook... 

Hardy keeps crashing on my MacBook and I have to hard reboot :(

Does anybody know the answer to this?  

Since there is no Print Screen/SysRq key on a MacBook is there an alternate key or a way of manually mapping the key?

---

### Post by nightfrost on 2008-05-19
> **flaggh said:**
> Does anybody know the answer to this?  

Since there is no Print Screen/SysRq key on a MacBook is there an alternate key or a way of manually mapping the key?

I would be very interesting in knowing this as well. My iBook really likes to crash every so often...

---

### Post by Sutur on 2008-07-05
> **nightfrost said:**
> I would be very interesting in knowing this as well. My iBook really likes to crash every so often...

Bumping this issue. I really want to know how to recover a locked up system with a mac keyboard.

---

### Post by pauper on 2008-07-15
For mac users running Ubuntu, is there any Print Screen key? If so, try
"Alt-PrtSc-<command key>"

The following method is more cumbersome and won't work always, as much as a
traditional "ALT-SysRq-<command key>" does fail in some exceptions.

When your system locks up, try to switch to a TTY (Ctrl+Alt+Fn). Login.
Now attempt to kill X session from here before proceeding any further.

If it fails, become ROOT, i.e. "sudo -i", since "sudo" is unable to pipe
the standard output to a file.

Now you can pass SysRq calls via this command:

```
echo ? > /proc/sysrq-trigger
```

where ? stands for a single key, such as r, e, i, s, u, b, etc.
Run it with "h" to view list of all available keys.

When you pass "e" parameter you'll end up logged off, same goes for "i"
(SIGTERM and SIGKILL, respectively). So you'll have to login back again.
Bear in mind that the "Sync" and "Umount" hasn't taken place until you see
the "OK" and "Done" appear on the screen, but again you might not get such
an output if something is messed up really bad. If it happens so then wait
several seconds, as someone already pointed out, and proceed further.


P.S. In case you have "linux-source" installed, look up this file:

```
less `find /usr/src -name sysrq.txt`
``` 

Or check this link:

[http://www.mjmwired.net/kernel/Documentation/sysrq.txt]("http://www.mjmwired.net/kernel/Documentation/sysrq.txt")

---

