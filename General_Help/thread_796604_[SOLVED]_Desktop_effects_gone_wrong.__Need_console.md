---
title: "[SOLVED] Desktop effects gone wrong.  Need console help"
date: 2008-05-16
forum: General Help
---

### Post by jwm_TO on 2008-05-16
Hello, I am running Ubunto Feisty 7.04 on a Koolo net appliance and I enabled desktop effects.  The result is a white screen and no control to disable the effects.  

I can reboot and login again but it's still white-screen.  I assume I need to disable desktop effects through logging in to a console session.   Can someone advise me on what file to look for where and then how to disable?

Thanks,

---

### Post by PinkFloyd102489 on 2008-05-16
After you get to the white screen, hit Ctrl+Alt+F1 to get to the console. Then type:

```
killall compiz
sudo /etc/init.d/gdm restart

```

If GDM doesnt restart like it should, replace restart with stop then issue the same command with start.

---

### Post by jwm_TO on 2008-05-16
Well that took me through the console, and then through the login, and then back to the white screen.  Both ways.  It seems to me that GDM implements a setting after I log in and so unless I change the configuration file I'm doomed.  I'm open to other advice and I'm thankful for pink's, but let me know what you've got.

--jwm

---

### Post by jwm_TO on 2008-05-21
I'm revivifying this thread out of hope/desperation.  Any ideas how to turn off desktop effects in my situation?

--jwm

> Hello, I am running Ubunto Feisty 7.04 on a Koolo net appliance and I enabled desktop effects. The result is a white screen and no control to disable the effects.

I can reboot and login again but it's still white-screen. I assume I need to disable desktop effects through logging in to a console session. Can someone advise me on what file to look for where and then how to disable?

---

### Post by Forlong on 2008-05-21
When in GDM, do not log into your regular session but in the Failsafe GNOME session.

There you should be able to use GNOME without Compiz and thus disable it.

---

### Post by jwm_TO on 2008-05-21
I tried that, but I can only log on through a failsafe console session

---

### Post by Forlong on 2008-05-21
You are lucky, I have still a Feisty install on my hard drive.
I'm going to boot into that one later and see what I can find out.


edit: I just did but noticed I do not have the default desktop effects installed. Will do that tomorrow, just bump the thread in case I forget it.

---

### Post by Forlong on 2008-05-22
OK, here's how you do it:

1. Boot into your regular GNOME session.

2. When the white screen comes up, hit [Ctrl]+[Alt]+[F1]

3. Log in

4. Enter the following command: ```
gconftool-2 -s -t string /desktop/gnome/applications/window_manager/default metacity
```

5. Hit [Alt]+[F7] to go back to GNOME

6. Restart your X server by hitting [Ctrl]+[Alt]+[Backspace]

7. Log in


Hope this helps.

---

