---
title: "Switch between users fast"
date: 2024-02-18
forum: General Help
---

### Post by ValentynPrumers on 2024-02-18
Hi!

My gf and me are sharing a laptop. We are not afraid of seeing each other data (lol). But i dont want her missing up with all my tabs. So i created a separate
user for her. Now we want to be able to switch fast between users. System is: Kubuntu 23.10 (plasma). Now if i click on the application launcher->leave->switch user...it does
take me to the login screen. But that takes a pretty long time (a few seconds at least). Then she has type in her password and again it takes time to load her desktop. 

I found another way.

Ctrl-Alt-F3; login me, startx ; Ctrl-Alt-F4: login her, startx.

Now we can switch between each others desktop environments with great speed (ctrl-alt-F3/4). Just wondering if this approach is ok?

Are there better solutions?

Lastly i have encountered one downside. The application plank doesn't want to run anymore. I get:

Abst[FONT=monospace][COLOR=#000000]ractMain:255 Only X11 environments are supported.[/COLOR][COLOR=#000000]

Any idea why?[/COLOR]

[/FONT]

---

### Post by #&amp;thj^% on 2024-02-18
Well Dolphin can use [s]{Ctrl+Alt+F4}[/s] correction (Shift+F4) to open konsole inside the current directory. So there's that. Just so you know is all.

Have you tried to add this to your ".profile"
```
XDG_SESSION_TYPE=x11 plank
```

I'm smiling with your use of plank on Plasma..:)

---

### Post by ValentynPrumers on 2024-02-18
I dont really understand what you mean. If I press Ctrl+Alt+F4 in Dolphin I get thrown to tty4 text mode. 

Another question. My machine boots to a login window (sddm). Now i have the option to just login here (for me). And then press Ctrl+Alt+F3 and login my gf and execute startx.  Or i
dont use the login window at all. And after boot I press Ctrl+ALt+F3 ; login;startx for me. And the same on tty4 for my gf. Is there a preference between the two, or doesnt it really matter?

The downside of the latter is that when someone  (gf looking at you :D)  presses Ctrl+Alt+F2  (instead of F4) by accident, she gets the graphic login and might log herself in twice. I tried it, and  the system hangs when you do that.

Last question. Is it possible to simply not boot into a GUI login mode? So just in text mode? I know thats possible from a previous SUSE installation. But that was
years ago. It got something to do with the init levels and the /etc/fstab file perhaps? Cant recall exactly how to do it.

---

### Post by dragonfly41 on 2024-02-18
> [COLOR=#000000]But i dont want her missing up with all my tabs. 

If your "tabs" are only in browser then there is the option of switching firefox profiles by command line.

Likewise profiles in other apps.[/COLOR]

---

### Post by #&amp;thj^% on 2024-02-18
> **ValentynPrumers said:**
> I dont really understand what you mean. If I press Ctrl+Alt+F4 in Dolphin I get thrown to tty4 text mode. 
I had a senior moment, just disregard it is (Shift+F4) in Dolphin
> **ValentynPrumers said:**
> 
Last question. Is it possible to simply not boot into a GUI login mode? So just in text mode? I know thats possible from a previous SUSE installation. But that was
years ago. It got something to do with the init levels and the /etc/fstab file perhaps? Cant recall exactly how to do it.
That is not a choice I can make for you.
Now I'll add I have not used this method for well over 5 Years now but it went like:
```
systemctl set-default multi-user.target && sed -i "s/GRUB_CMDLINE_LINUX_DEFAULT=\"quiet\ splash\"/GRUB_CMDLINE_LINUX_DEFAULT=\"\"/g" /etc/default/grub && update-grub
```

***BUT USE AT YOUR OWN RISK*** :)

---

### Post by ValentynPrumers on 2024-02-19
Thanks! I didnt have the guts to try it. But i did follow this:

[https://askubuntu.com/questions/378046/how-to-run-ubuntu-xubuntu-in-a-complete-non-gui-mode](https://askubuntu.com/questions/378046/how-to-run-ubuntu-xubuntu-in-a-complete-non-gui-mode)

1. uncomment grub_terminal=console in /etc/default/grub
2. sudo update-grub
3. sudo systemctl enable multi-user.target --force
4. sudo systemctl set-default multi-user.target

That worked perfectly.

After this i get a terminal after boot. And i can login and startx manually for each user and next switch between session with Ctrl+Alt+FX

---

### Post by #&amp;thj^% on 2024-02-20
Yep same thing I suggested, just different wording...

All's Good that ends Good.

BTW, i just used the same suggestion I offered in post #5 and it still works. (I need to use what I suggest to be sure it is safe)

---

