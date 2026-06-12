---
title: "I need help with custom runlevel trouble"
date: 2008-01-27
forum: General Help
---

### Post by nmz787 on 2008-01-27
So I needed a custom runlevel that would boot into a less than priveleged user and automatically log in to a shell only.

I followed 
[http://www.imbrandon.com/2007.10.19/note-to-self-ubuntu-710-on-a-p200.html](http://www.imbrandon.com/2007.10.19/note-to-self-ubuntu-710-on-a-p200.html) 
and instead of launching it from event/d/tty1 I created a new script in rc2.d at the end of the sequence just before rc.local gets loaded

Now that works pretty well when I boot from grub to runlevel 2, but when I try to boot normally, it gets stuck on runlevel 2.

Is there some way to have the computer skip over runlevel 2 from the normal boot sequence? I know there's no more inittab, but I don't understand quite how to use the upstart program.

---

### Post by kuja on 2008-01-27
I don't know about the runlevel stuffs, but I do know that to be able to sudo you need to add the new user to the "admin" group.

---

### Post by randominternet on 2008-02-01
runlevel are broken in ubuntu now with upstart, see bug 

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014")

but for many problems you can just make your own script that greps /proc/cmdline for whatever trigger you want to stick on the end of the line in grub and you can get the same effect.

---

### Post by bixejo on 2008-04-03
In Ubuntu is indeed rather difficult to customize runlevels, as upstart manages now this stuff. You should do it by hand with a little help from some specialized tools like the ones provided by sysv-rc-conf.

In the following link you may find a comprehensive analysis of these issues and hopefully a good way to fix this:

[http://emmet.caulfield.info/Tech/UbuntuRunlevels/](http://emmet.caulfield.info/Tech/UbuntuRunlevels/)

Hope this helps,

---

