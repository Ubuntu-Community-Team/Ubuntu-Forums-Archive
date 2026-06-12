---
title: "gdm/grub auto shut down"
date: 2008-03-07
forum: General Help
---

### Post by vexorian on 2008-03-07
First of all, I am using feisty, and I am planning to wait for hardy instead of upgrading to gutsy since it would be a difficult process to me requiring to backup lots of data.

I got a problem, and it is that sometimes, I would click the restart button instead of the turn off one when I am sleepy and not notice I just left the PC turned on all night.

I tried solving this adding an auto shutdown option to grub, I actually found a tutorial on that, but my PC's compatibility with grub seems not to be ok, since instead of shutting down it just closes grub and leaves a blinking terminal cursor.

So, my new option is not make grub launch ubuntu automatically after 10 minutes, and then make gdm shutdown automatically if you do not give it an username in 10 minutes. The problem is that I don't know how to do that, I tried checking out gdm.conf but no comment implied that there is a way to do it.

---

### Post by lha on 2008-03-07
> **vexorian said:**
> So, my new option is not make grub launch ubuntu automatically after 10 minutes, and then make gdm shutdown automatically if you do not give it an username in 10 minutes. The problem is that I don't know how to do that, I tried checking out gdm.conf but no comment implied that there is a way to do it.

If you don't find a better way, try this: Create a dummy user account, and set Gnome to run 'shutdown -h now' when dummy logs in. Gdm can then be set to automatically log in to the dummy account after a given time. In effect, you get a timed shutdown.

---

### Post by vexorian on 2008-03-08
> **lha said:**
> If you don't find a better way, try this: Create a dummy user account, and set Gnome to run 'shutdown -h now' when dummy logs in. Gdm can then be set to automatically log in to the dummy account after a given time. In effect, you get a timed shutdown.

That's feasible, the only problem would be that shutdown requires super user.

---

### Post by lha on 2008-03-09
> **vexorian said:**
> That's feasible, the only problem would be that shutdown requires super user.

I forgot to mention that you need to add
```
dummy ALL = NOPASSWD: /sbin/shutdown -h now
```
to sudoers. (Use visudo to edit /etc/sudoers.) This will allow user 'dummy' to run 'shutdown -h now' as sudo without password.

---

