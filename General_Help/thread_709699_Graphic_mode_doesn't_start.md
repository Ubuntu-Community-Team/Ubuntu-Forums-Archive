---
title: "Graphic mode doesn't start"
date: 2008-02-27
forum: General Help
---

### Post by ronniegaucho on 2008-02-27
Hello,

First, please, excuse my bad English level

I've just installed Ubuntu (7.10) on my laptop computer (HP Pavillon dv4000). When I start the computer, it appears the boot screen (HP), then Grub (Please wait..., Starting up...), but after this, there is this error:

[[IMG]http://img254.imageshack.us/img254/7158/27022008356fi4.th.jpg[/IMG]](http://img254.imageshack.us/my.php?image=27022008356fi4.jpg)

Then, there is a neverending blank black screen:

[[IMG]http://img522.imageshack.us/img522/3493/27022008357ta3.th.jpg[/IMG]](http://img522.imageshack.us/my.php?image=27022008357ta3.jpg)

And I have to do CTRL+ALT+F1, to remove this screen, so I have:

[[IMG]http://img442.imageshack.us/img442/7323/27022008358op9.th.jpg[/IMG]](http://img442.imageshack.us/my.php?image=27022008358op9.jpg)

Then, and just then, it starts:

[[IMG]http://img238.imageshack.us/img238/6054/27022008359ka7.th.jpg[/IMG]](http://img238.imageshack.us/my.php?image=27022008359ka7.jpg)

[[IMG]http://img337.imageshack.us/img337/1007/27022008360nc1.th.jpg[/IMG]](http://img337.imageshack.us/my.php?image=27022008360nc1.jpg)

Now, the graphic mode starts:

[[IMG]http://img337.imageshack.us/img337/3007/27022008361qf6.th.jpg[/IMG]](http://img337.imageshack.us/my.php?image=27022008361qf6.jpg)

When I do lspci, 00:1c.0 matches with PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)

What is the problem? Why the graphic mode didn't start automatically?

Thanks ;)

---

### Post by Rocket2DMn on 2008-02-27
Not sure exactly about the allocation of resources problem (bad BIOS config?), but you can try reconfiguring X, try following this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If everything seems to work afterward, then just let it be I suppose.  It's possible you have some incompatible hardware, but we'll just have to see about that later.

---

