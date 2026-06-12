---
title: "New Login in a Nested Window for KDE?"
date: 2006-07-18
forum: General Help
---

### Post by Jucato on 2006-07-18
I was looking for a way to have a new login/session in a nested window. I know that there's the gdmflexiserver --xnest command, but I'm using Kubuntu (I have GNOME installed, but I'm using KDM, not GDM, as default). I was wondering if there's a counterpart of that command/program for KDE.

I have VMWare Server, but making a new installation for Kubuntu and Ubuntu would be time consuming and would eat up a bit of my hard drive space.

Any advice would be greatly appreciated. :D

---

### Post by aysiu on 2006-07-18
[http://wiki.kde.org/tiki-index.php?page=Tips%20and%20Tricks&pagenum=2](http://wiki.kde.org/tiki-index.php?page=Tips%20and%20Tricks&pagenum=2)

---

### Post by Jucato on 2006-07-18
> **aysiu said:**
> [http://wiki.kde.org/tiki-index.php?page=Tips%20and%20Tricks&pagenum=2](http://wiki.kde.org/tiki-index.php?page=Tips%20and%20Tricks&pagenum=2)

That was quick! :D
Thanks! I'll try it out right now.

---

### Post by Jucato on 2006-07-18
Didn't work as expected. But thanks for pointing me in the right direction. 

I was able to run a new user using Xephyr instead of Xnest. I also had to edit /etc/kde3/kdm/Xaccess, together with /etc/kde3/kdm/kdmrc, a bit. 

However, I ran into some problems. For one, I don't seem to know how to start the display from the login screen. Another is that some apps that I've set in KDE to a specific size don't resize when I use a smaller Xephyr resolution and, since there are no scrollbars in the Xephyr window, I can't access those apps without resizing or moving them.

I guess I'd have to settle for either using VMWare or making new users and switching between them (though I'm having a bit of a problem with that right now).

---

### Post by aysiu on 2006-07-18
> **Fenyx said:**
> 
I guess I'd have to settle for either using VMWare or making new users and switching between them (though I'm having a bit of a problem with that right now). Or... use GDM, which is what I do, even when I'm using KDE.

---

### Post by Jucato on 2006-07-18
During the installation of ubuntu-desktop, I chose to use KDM as the default. The login manager window issue is quite easy to solve, via a Live CD on VMWare. 

However, my real problem lies in switching to a new user when I'm in GNOME. Like I said, I use KDM. But right now, I'm using GNOME (to test things). When I'm using KDE+KDM, there's an option in the menu to switch/login to a new user or start a new session. IIRC, when I used GNOME+GDM before, a similar option existed. But when I use GNOME+KDM, that option is no where to be found. If I could only figure out how to login to multiple users when I'm logged into GNOME, I wouldn't have any need for Xephyr/Xnest. The only way I could do that is to logout of GNOME, login to KDE, then use the Start a new session option from there.

---

### Post by aysiu on 2006-07-18
I know KDM is your *default* display manager. Isn't it possible to have KDM and GDM running at the same time, though? And, if so, could you still use *gdmflexiserver --xnest* in Gnome, even if KDM is your default display manager?

---

### Post by Jucato on 2006-07-19
> **aysiu said:**
> I know KDM is your *default* display manager. Isn't it possible to have KDM and GDM running at the same time, though? And, if so, could you still use *gdmflexiserver --xnest* in Gnome, even if KDM is your default display manager?

When I try running
```
sudo /etc/init.d/gdm start
```
in a new virtual terminal (Ctrl+Alt+F2), I get an error message saying that it can't run because GDM is not the default display manager.

When I try running gdmflexiserver, I get these messages:
> 
 Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access configuration key <daemon/PidFile=/var/run/gdm.pid>
Using compiled in value </var/run/gdm.pid> for <daemon/PidFile=/var/run/gdm.pid>


I'm practically clueless... :(

---

### Post by aysiu on 2006-07-19
Hm. Maybe I was wrong. I just seemed to remember at one time having both services checked at once in my bootup manager (*gksudo bum*).

Maybe they can't be both run at the same time.

---

### Post by Jucato on 2006-07-19
Guess that really leaves me no choice but to use VMWare in the meantime.

This if off-topic, but what do you use when you're taking screenshots in your guides? VMWare? Xnest? :D

---

### Post by aysiu on 2006-07-19
I actually use a mix and match.

Sometimes I use Qemu. Sometimes I use VMWare. Sometimes I use Xnest. Sometimes I just use ```
gnome-screenshot --delay 5
```

---

### Post by Jucato on 2006-07-19
I see. I'm actually interested in trying out Qemu. I already have VMWare Server installed, and it's much easier to use compared to my previous experience with Qemu and VMWare Player in Windows. But I have a feeling that it's also a bit slower than Qemu. 

Anyway, I'll probably stick to VMWare Server for a while, since I'm just going to need those other K/X/Ubuntu installs temporarily. I don't plan on taking screenshots the rest of my life. :D

---

### Post by aysiu on 2006-07-19
You'd be surprised, actually--I've found VMWare Player to be *faster* than Qemu.

Qemu, however, is less complicated. No virtual hard drive needs to be created, no configuration file. No breakage on a kernel upgrade. For some simple stuff, Qemu is just a lot easier--all you need is an .ISO and you're in business.

---

### Post by Jucato on 2006-07-19
> **aysiu said:**
> You'd be surprised, actually--I've found VMWare Player to be *faster* than Qemu.

Hmm... it makes me wonder. Will VMWare *Player* be faster than VMWare *Server*??

---

