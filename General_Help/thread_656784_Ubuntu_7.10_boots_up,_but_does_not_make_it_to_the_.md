---
title: "Ubuntu 7.10 boots up, but does not make it to the login screen..."
date: 2008-01-02
forum: General Help
---

### Post by Simscape on 2008-01-02
When I boot Ubuntu everything works fine but the login screen never comes up. :confused:
It just now started doing this. I have tried it at least 5 or 6 times.
Can anyone help me to fix this?

***Please do not say I have to reinstall it... Please...*** :(

Thanks in advance!

---

### Post by ~LoKe on 2008-01-02
When you're waiting for the login screen to come up, can you see any messages?  Try hitting ctrl+alt+f1.  It should bring you to a black screen asking you to log in.  Do so, and once you're logged in, type this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If that works...
```
sudo /etc/init.d/gdm restart
```

---

### Post by Simscape on 2008-01-02
> **~LoKe said:**
> When you're waiting for the login screen to come up, can you see any messages?  Try hitting ctrl+alt+f1.  It should bring you to a black screen asking you to log in.  Do so, and once you're logged in, type this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If that works...
```
sudo /etc/init.d/gdm restart
```

Ok, I hit ctrl+alt+f1, and it did some stuff and eventually came up to this message:
/dev/sda1 contains a filesystem with errors, check forced.
/dev/sda1: duplicate or bad block in use!

Also it said that the root filesystem was set to read only.

Then some other messages come up, and now I'm were I can type in commands.
What do I do now? Do I type in those commands above?

---

### Post by GuitarRocker2562 on 2008-01-02
ouch, do nano /etc/fstab    go to your root file system and change the next to last column too 0

but befor you do that do cp /etc/fstab /etc/fstab.bak

---

### Post by Simscape on 2008-01-02
I can't do that.
When I  try to make the .bak file, it can't because the file system is stuck on read-only.

---

### Post by ~LoKe on 2008-01-02
Use sudo if you can.

```
sudo cp /etc/fstab /etc/fstab.bak
sudo nano /etc/fstab
```

---

### Post by GuitarRocker2562 on 2008-01-02
right... i think this may need a reinstall, try using the live CD and changing the partition a little bit. But you should really back up and re-install, this can easily been done witht he CD or by cp / (to external drive, maybe /media/disk)

---

### Post by Simscape on 2008-01-03
When I type that in it says this,
> The command could not be located because '/usr/bin' is not located in the PATH environment variable.
bash: sudo: command not found.
What do I need to do?

---

### Post by Simscape on 2008-01-03
Oh, well so I'll need to reinstall Ubuntu?

---

### Post by TreeFinger on 2008-01-03
I believe I have the same problems as you have after upgrading to 7.10

After selecting which partition I'd like to boot from GRUB the screen never 'kicks-in'. My monitor is turned on but all is black, GUI or Command Line is nowhere to be seen.

The log-in is there though. I am able to log-into my system 'blindly'. I type in my username, hit tab, and then type in my password and then hit enter. Usually, (I say usually because things get funky and sometimes I need to reboot my system and try this process of logging in blindly over again), this will work. My monitor finally 'kicks-in' and I am able to see my Desktop.

Not sure how to fix my problem, was thinking of doing a reinstall but I am not really up for that right now.  I hope my post helped you out a bit.

Does your monitor light continually blink when you are suppose to be seeing the login ?

---

### Post by Simscape on 2008-01-03
Yes, exactly, thats a exactly what my system does, but my monitor's light don't blink, it shows the monitor has kicked on, I also know because it makes a click when it does.
But, I think I'll just reinstall Ubuntu.
Thanks for your help though.

---

