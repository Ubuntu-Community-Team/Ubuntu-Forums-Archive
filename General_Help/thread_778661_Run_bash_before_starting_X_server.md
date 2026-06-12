---
title: "Run bash before starting X server?"
date: 2008-05-02
forum: General Help
---

### Post by Forlornity on 2008-05-02
Hey all, I was wondering how to run a bash script **before** X starts.
The reason being that I have an ATI card in my laptop and I frequently connect it to external monitors as well as the notebook's monitor, to facilitate this I wrote a small bash script which queries the connected monitors and changes /etc/X11/xorg.conf accordingly. The only problem with this script is that I must restart the X server every time I change the settings. How does one run such a script before the X server starts?

Thanks, Forlornity

---

### Post by Forlornity on 2008-05-02
Bump?

---

### Post by kpkeerthi on 2008-05-02
Add your script to /etc/rc.local

---

### Post by warp99 on 2008-05-02
> **Forlornity said:**
> Hey all, I was wondering how to run a bash script **before** X starts.
The reason being that I have an ATI card in my laptop and I frequently connect it to external monitors as well as the notebook's monitor, to facilitate this I wrote a small bash script which queries the connected monitors and changes /etc/X11/xorg.conf accordingly. The only problem with this script is that I must restart the X server every time I change the settings. How does one run such a script before the X server starts?

Thanks, Forlornity
Edit your /etc/rc.local file and include the command to issue the script. If rc.local starts the script too late you can set the runlevel and the boot order by placing the script in the /etc/init.d directory and running the command 'update-rc.d'. Type 'man update-rc.d' for more information on how to do this.

---

### Post by ryanhaigh on 2008-05-02
Have you tried putting the script in rc.local. I know this file is executed at boot time but I am unsure as to whether it gets executed before the xserver is started.

I am reasonably sure that gdms startup script (/etc/init.d/gdm) actually starts the xserver so if you put yours at the top of that or at the top of the start section then that should work. It would probably be best to just add the following to the file as it makes it much easier to revert.

```

/bin/bash /path/to/your/script &&

```

Try rc.local first (also make sure it is executable) and then if that doesn't work use gdm.

---

### Post by danwood76 on 2008-05-02
That will run the script after X has loaded.

What you could do is hook into the X server starting script.
/etc/init.d/gdm if your using GNOME.

Rename the gdm script and replace it with your own, but at the end of your script launch old gdm aswell (otherwise X wont load)

-- edit --

beat me to it.
You dont want to do your bash script && as it will run it at the same time as launching X.

So the above example would just be:
```

/bin/bash /path/to/your/script

```

---

### Post by warp99 on 2008-05-02
> **danwood76 said:**
> That will run the script after X has loaded.

What you could do is hook into the X server starting script.
/etc/init.d/gdm if your using GNOME.

Rename the gdm script and replace it with your own, but at the end of your script launch old gdm aswell (otherwise X wont load)

-- edit --

beat me to it.
You dont want to do your bash script && as it will run it at the same time as launching X.

So the above example would just be:
```

/bin/bash /path/to/your/script

```

Changing gdm is a bad idea since the script can be overwritten by an update. Best thing is to add the script to /etc/init.d and set the runlevels like this:
```
sudo update-rc.d foobar multiuser
```
that will run the script 'foobar' at boot order K20/S20, before gdm/xserver loads, and will not attempt to stop the script on shutdown. To remove it do the following:
```
sudo update-rc.d -f foobar remove
```
that will remove all of the runlevel symlinks, but not the script 'foobar' itself.

---

### Post by Forlornity on 2008-05-02
No such luck I'm afraid, I know the script works as I can run it fine then restart the X server and it's fine.
But when I used the update-rc.d method it didn't seem to work, I suspect it's more to do with the runnings of the script than any problem with the instructions, waddya think?

---

### Post by warp99 on 2008-05-05
> **Forlornity said:**
> No such luck I'm afraid, I know the script works as I can run it fine then restart the X server and it's fine.
But when I used the update-rc.d method it didn't seem to work, I suspect it's more to do with the runnings of the script than any problem with the instructions, waddya think?
Post the script and let's take a look.

---

