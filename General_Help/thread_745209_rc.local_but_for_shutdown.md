---
title: "rc.local but for shutdown"
date: 2008-04-04
forum: General Help
---

### Post by arizonagroovejet on 2008-04-04
Anyone know what, if anything, the shutdown equivalent of /etc/rc.local is? I want to run a command just before the machine is turned off.

The command incidentally is

```
eject -t /dev/cdrom

```

to make sure I don't end up with a powered off machine with a CD tray sticking out. :)

thanks,

mike

---

### Post by kaivalagi on 2008-04-04
Not sure if there is anything equivalent to rc.local for shutdowns, but a system halt is runlevel 0, which runs certain scripts in the /etc/init.d folder

You could edit the halt script in that folder, in theory it would fire when you shutdown...not sure if that's such a good idea though :)

Edit: if you look at the /etc/rc0.d folder, it holds symbolic links to the files in init.d, it might help you out. /etc/rc0.d/S90halt for example points to /etc/init.d/halt

Edit 2: Take a look at this article, covers runlevels well: [http://www.linux.com/articles/114107]("http://www.linux.com/articles/114107")

---

### Post by arizonagroovejet on 2008-04-04
Adding the eject command as the first line in the do_stop function of /etc/init.d/halt has the desired effect but I prefer not to edit scripts like that as there's the chance that the changes will be wipped out by a package update. /etc/init.d/halt belongs to the initscripts package for example.  By contrast  rc.local is specifically intended for you to make changes to.

---

### Post by kaivalagi on 2008-04-04
It looks like there is no equivalent to rc.local for shutdown. I tracked back rc.local and it is called from /etc/rc5.d/S99rc.local.

To have the same for shutdown you would need to edit the 'halt' script to check for a filename of your choice and run it if found....

But yes you might  loose your script edits with an update, best bet would be to create an rc.shutdown and call it from the halt script, at least if it stopped working you could just re-add the call to the halt script again.

If you do find an equivalent to the rc.local for shutdowns, please post back, I would very much like to know!

Cheers

---

### Post by nick_h on 2008-04-04
> I prefer not to edit scripts like that as there's the chance that the changes will be wipped out by a package update.
You could create a new script in /etc/init.d and then make a symlink to it in the appropriate /etc/rcx.d directories.

Have a look at the *update-rc.d* command, which automates this process.
```
man update-rc.d
```

---

