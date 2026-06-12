---
title: "What is the easiest and safest way to logout through tty1?"
date: 2016-08-04
forum: General Help
---

### Post by hey2 on 2016-08-04
Hi.

Every once in a while, after the login, i get nothing but a wallpaper and the mouse cursor. 

Usually i use a live usb to fix my accoumt, but i want a faster way.

I already tried to use the " DISPLAY=:0 gnome-session-quit", but i get this error:

   Failed to call logout: The name org.gnome.SessionManager was not provided by any .service files

Am i doing something wrong?

What is the easiest and safest way to log out using the tty?

I'm using 14.04.

Thanks and sorry for my English

---

### Post by CantankRus on 2016-08-04
You could run...
```
kill -9 -1
```
which will kill all the users running processes and leave you at the login screen.

---

### Post by Bucky Ball on 2016-08-05
Reboot or shutdown from a terminal/CLI, in that order and you only need one or the other:

```
sudo reboot -h now
sudo shutdown -h now
```

Probably a good idea to start a thread and see if we can help you solve what is happening with your dodgy install.

---

### Post by hey2 on 2016-08-05
> **CantankRus said:**
> You could run...
```
kill -9 -1
```
which will kill all the users running processes and leave you at the login screen.

Hi.

Thank for your reply. 

when i was searching for a solution i read about that command, but there was people saying that is kind of aggressive.

Do you know a command just to logout?

---

### Post by Bucky Ball on 2016-08-05
I gave a couple of commands to restart and shutdown the machine in post #3. Are you talking about logging out to the login screen, not a restart or reboot? Sorry for the confusion ...

---

### Post by hey2 on 2016-08-05
> **Bucky Ball said:**
> Reboot or shutdown from a terminal/CLI, in that order and you only need one or the other:

```
sudo reboot -h now
sudo shutdown -h now
```

Probably a good idea to start a thread and see if we can help you solve what is happening with your dodgy install.

Hi.

Thanks for your replay.

My first thought was to do a simple "sudo reboot", but i wanted to find faster way.

 What is the advantage of the halt option? What is the command that ubuntu uses when i go to the shut down menu and i press shut down?

Thank for the suggestion of opening a new thread, but i think that the issue is caused by me.

The last time was because i messed with the compizconfig.

When this happens i just delete the .config folder and everything is back to normal.

---

### Post by hey2 on 2016-08-05
> **Bucky Ball said:**
> I gave a couple of commands to restart and shutdown the machine in post #3. Are you talking about logging out to the login screen, not a restart or reboot? Sorry for the confusion ...

Hi.

I haven't seen your reply.

After the login i only have the wallpaper and the mouse cursor. I want to use tty1 to logout that session so that when i press ctrl+alt+f7 I'm back at the login screen.

Then i use the tty1 to fix my account, exit the tty1, login as normal and hopefully i see an orange wallpaper, a menu bar and a launcher ( .config deleted ).

Thanks.

---

### Post by CatKiller on 2016-08-05
```
 sudo service lightdm restart 
``` might be what you're after. You could also consider re-enabling the Ctrl-Alt-Backspace shortcut for killing the X server.

Edit: if you want to fiddle with stuff in-between, you can split the **restart** into separate **stop** and **start** commands.

---

### Post by hey2 on 2016-08-05
> **CatKiller said:**
> ```
 sudo service lightdm restart 
``` might be what you're after. You could also consider re-enabling the Ctrl-Alt-Backspace shortcut for killing the X server.

Edit: if you want to fiddle with stuff in-between, you can split the **restart** into separate **stop** and **start** commands.

Hi.

Thanks for your reply.

I will try it.

The last time i couldn't use the terminal shortcut so i don't know if shortcuts are an option.

---

