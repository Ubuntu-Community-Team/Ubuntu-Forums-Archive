---
title: "virtual box install error message"
date: 2008-04-24
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-04-24
Hi all,
I just installed virtual box and got the followning message in the terminal:

```
Get:1 http://au.archive.ubuntu.com gutsy/universe libxerces27 2.7.0-3 [1321kB]
Get:2 http://au.archive.ubuntu.com gutsy/universe libxalan110 1.10-3.1 [1241kB]
Get:3 http://au.archive.ubuntu.com gutsy/universe virtualbox-ose-modules-2.6.22-14-generic 6 [317kB]
Get:4 http://au.archive.ubuntu.com gutsy/universe virtualbox-ose 1.5.0-dfsg2-1ubuntu3 [5695kB]
Fetched 8574kB in 5m16s (27.1kB/s)


*Unpacking, Selecting, Setting Up, bla bla bla*


Setting up virtualbox-ose-modules-2.6.22-14-generic (6) ...
 * Starting VirtualBox kernel module vboxdrv                                                                                                                             chown: `:vboxusers': invalid group

 * Cannot change owner vboxusers for device /dev/vboxdrv.

Setting up virtualbox-ose (1.5.0-dfsg2-1ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

Is that something to worry about? Do I need to do something about that? And if so, what?

Thanks,
Steve

---

### Post by ibuclaw on 2008-04-24
Type in this:
```
gksu gedit /etc/group
```
Find the word "**vboxusers**
And add your name to the end of the line.
ie:
My login name is "iain"
> vboxusers: x:123:iain 
Save the file.
Log out, and log back in again.

If you got the OSE version, you may have to run a script which compiles the virtual headers to be compatible with your kernel.

If this is the case, VB will display an error message when you first try to run a virtual environment.
It should tell you what to do though.

Regards
Iain

---

### Post by Linux&amp;Gsus on 2008-04-24
That did the trick.
Thank you very much.

Cheers,
Steve

---

