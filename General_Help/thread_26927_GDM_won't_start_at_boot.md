---
title: "GDM won't start at boot"
date: 2005-04-14
forum: General Help
---

### Post by shakin on 2005-04-14
The problem occurred after upgraded to an SMP kernel (2.6.10-5-686 SMP), but switching back to the old kernel didn't solve the problem and since I hadn't rebooted in over a week, the problem could have been another update.

During the boot process I get two errors:

- Not starting Gnome Display Manager (gdm); it is not the default display manager.

- Not starting KDE Display Manager (kdm); it is not the default display manager.

In /etc/X11/default-display-manager I have /usr/bin/gdm. I also ran dpkg-reconfigure gdm to set it as the default, without success.

I can run gdm from the command line without trouble, but for whatever reason it won't load on boot. I also tried dpkg-reconfigure xserver-xorg just in case that was it, but still no luck.

Thanks.

---

### Post by shakin on 2005-04-14
The solution was to remove the commented kdm line from /etc/X11/default-display-manager

My default-display-manager looked like this:
```

/usr/bin/gdm
#/usr/bin/kdm

```

And the problem was fixed after changing it to:
```

/usr/bin/gdm

```

---

### Post by misterlizard on 2005-04-14
Glad you've fixed it. I read somewhere that you have to run

sudo dpkg-reconfigure kdm

To switch between display managers, rather than 'sudo dpkg-reconfigure kdm'. Not sure why this is the case, but it's worked for me.

---

