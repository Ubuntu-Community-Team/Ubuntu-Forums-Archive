---
title: "howto stop nautilus autostart"
date: 2012-12-15
forum: General Help
---

### Post by mbohets on 2012-12-15
Hi,

I installed Ubuntustudio, and add Kubuntu via synaptic.
After using both desktops a number of times, I now have Nautilus sow tarting up each time i log into Kubuntu, it does not start automatically in the other desktops.

How can I get rid of Nautilus autostart in Kubuntu ???

/home/marc/.kde/Autostart    is empty
and when I look in system settings autostart, there is nothing either
and in KDE service manager, Nautilus is not listed as a service
/usr/share/autostart   does not list Nautilus either

So why does Nautilus start after logging into KDE ?

---

### Post by Rexilion on 2012-12-15
Did you check /etc/xdg/autostart and look for references to nautilus. Or maybe you should disable starting *any* Gnome related services in KDE.

---

### Post by mbohets on 2012-12-15
Thx, I just looked, but no reference to Nautilus eiter.

I did not know that there were so many autostart things in linux.

---

### Post by dino99 on 2012-12-15
you might do a choice: either kde or gnome (mostly because they are not expected to be installed side by side, and had never been tested in that way, so you might found alot of unknown issues/conflicts due to the meta-packages and their crossed dependencies)

---

### Post by Rexilion on 2012-12-15
Long shot, but you could try this:

```
sudo mv /usr/bin/nautilus /usr/bin/nautilus.orig
sudo gedit /usr/bin/nautilus
```

Paste the following into this screen, save and close it:

> #/bin/sh
exec 1>> ~/whostartsnautilus
exec 2>> ~/whostartsnautilus
echo $PPID started nautilus
echo ps u -p $PPID

```
sudo chmod 755 /usr/bin/nautilus
```

Now log in and log out to reproduce your issue (nautilus should not pop-up).

And now revert to normal:

```
sudo rm /usr/bin/nautilus
sudo mv -v /usr/bin/nautilus.orig /usr/bin/nautilus
```

In your home directory you should find a file called 'whostartsnautilus'. Post the contents of this file on this forum.

This file will point to the process starting nautilus, and might help us preventing in doing that.

---

### Post by mbohets on 2012-12-15
Because of the reply that kde and gnome don't play well together, I decided to uninstall Nautilus, which in turn automatically uninstalls ubuntu studio.

Ubuntustudio is still there, so I guess it is only a meta package and nothing is removed by removing this.

Anyway Nautilus stopped autostarting now.
Pitty I did not see the next post earlier, because it may have revealed why nautilus autostarted.

---

