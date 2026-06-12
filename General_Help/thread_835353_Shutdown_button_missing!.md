---
title: "Shutdown button missing!"
date: 2008-06-20
forum: General Help
---

### Post by chrisruls00 on 2008-06-20
I recently used adept updater to update the Linux kernels in kubuntu. However after that something broke. When I click shutdown from the K-menu and the box that usually has around 5 options show up none of them but log-off are there! Shutdown, hibernate, and standby are missing! This means I must shut down my computer by logging off and then choosing shutdown from the log-in screen. Does anyone know what could be wrong?

---

### Post by natirips on 2008-06-20
I don't know what could be wrong but you can also "sudo shutdown 0" from the console. Type "shutdown --help" for usage. You can also mybe create a custom menu entry with such command, although it's not as practical since you'll have to type your password to shut down this way...

I'm not 101% sure the command is called "shutdown" as I'm using Ubuntu (with Gnome), but I don't think it should be any different on KDE.

Edit: if you'll be making a custom menu entry, make sure to use "gksudo" instead of "sudo".

---

### Post by dracayr on 2008-06-20
It's ```
sudo shutdown now
```or ```
sudo init 0
```

dracayr

---

### Post by Zorael on 2008-06-20
There are two things to make sure of.
[list=1][*]Go into System Settings -> Advanced -> Session Manager. See to it that *Offer shutdown options* is checked.
[*]Make sure that you don't have the **xserver-xgl** package installed, unless you really need it for your videocard to get decent Compiz performance. (Few cards want it.) Pop up Adept Manager, find it, tag it for removal, apply. Or do it through a terminal.
```
$ sudo aptitude purge xserver-xgl
```[/list]

---

### Post by chrisruls00 on 2008-06-20
Thanks Zorael! It was the xserver-xgl package. Around the time of the update I also had some compiz problems and installed it because someone said it helps. I guess I should look into those things more next time.

---

