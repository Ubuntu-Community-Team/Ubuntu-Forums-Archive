---
title: "Why is my console tty2 instead of tty1?"
date: 2022-03-25
forum: General Help
---

### Post by jeff-vancouver on 2022-03-25
I have Ubuntu 20.04.4 LTS, 64-bit, GNOME version 3.36.8
After system startup, if I run ps -a I get this

:~$ ps -a
    PID TTY          TIME CMD
   2122 tty2     00:15:03 Xorg
   2152 tty2     00:00:00 gnome-session-b
  69736 pts/0    00:00:00 ps

Where is tty1?
Is this normal behavior, or do I need to kill a session to get back to tty1?
My system is setup to require a password in order to logon, but I don't think
that is the cause of this behavior.

And why is it gnome-session-b?

---

### Post by DuckHook on 2022-03-26
Welcome to the forums, jeff-vancouver

I don't really have a solid answer to your queries. On my development version running 22.04, it shows TTY2 as well. This is nothing to worry about since a large number of TTYs are created every time you boot the system, so any arbitrary TTY is as good as another. Why the devs chose TTY2 to host your GUI is a mystery, but has no material impact on usage. To see all of the TTYs your system is already running:```
 ls -la /dev | grep -i tty
```

Likewise, gnome-session-b looks like common expected behaviour. It has to be there if you are running a Gnome DE. Why the "b"? Dunno. But again, no impact on usage except if it is absent.

---

### Post by grahammechanical on 2022-03-26
My guess is that Linux is running on tty1 and Ubuntu (x-org, gnome etc.) are running on tty2.

Edit: I have run the above command and myself as a user is running on tty2.  Well, I am logging to Ubuntu.

Regards

---

### Post by deadflowr on 2022-03-27
It's normal.
See: [https://askubuntu.com/questions/910108/why-is-my-gdm-at-a-different-tty-than-my-desktop-environment]("https://askubuntu.com/questions/910108/why-is-my-gdm-at-a-different-tty-than-my-desktop-environment")
and
[https://bugzilla.gnome.org/show_bug.cgi?id=747339]("https://bugzilla.gnome.org/show_bug.cgi?id=747339")
> And why is it gnome-session-b?

gnome-session-bin?
It's part of the gnome-session program used to manage the session.

---

### Post by jeff-vancouver on 2022-03-27
Thank you for your help. I was not sure if I had started a session and was unable to end it. Glad it's just normal.
cheers.

---

