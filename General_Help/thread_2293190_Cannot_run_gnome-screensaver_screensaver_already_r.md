---
title: "Cannot run gnome-screensaver: screensaver already running in this session"
date: 2015-09-03
forum: General Help
---

### Post by Daniyal_Javani on 2015-09-03
Hello
I can't run gnome-screensaver, could you please help me to run that
```
$ pgrep gnome-secreensaver
$ pgrep screensaver
$ gnome-screensaver

** (gnome-screensaver:14533): WARNING **: screensaver already running in this session
```

Well, I have no idea what information needed, so if you want more information please tell me.

---

### Post by v3.xx on 2015-09-03
Does gnome-screensaver have a decent selection these days?  I haven't ran it in an age, but use xscreensaver, it has a very large selection of screensavers.

What your getting is just a warning, not an error.  For some reason you have two startups going on.  Did you add one?

Edit

You can use the autostart GUI to check for double entries or go to you hidden files in your home folder.

~/.config/autostart

---

### Post by Daniyal_Javani on 2015-09-03
> **v3.xx said:**
> Does gnome-screensaver have a decent selection these days?  I haven't ran it in an age, but use xscreensaver, it has a very large selection of screensavers.

What your getting is just a warning, not an error.  For some reason you have two startups going on.  Did you add one?

Edit

You can use the autostart GUI to check for double entries or go to you hidden files in your home folder.

~/.config/autostart

Thanks.
Seems there is no two startups:
```
$ ls  ~/.config/autostart 
cuttlefish.desktop            psensor.desktop
indicator-multiload.desktop   redshift-gtk.desktop
indicator-sensors.desktop     remmina-applet.desktop
indicator-sysmonitor.desktop  shutter.desktop
mailnag.desktop               unity-mail-autostart.desktop
```

---

### Post by v3.xx on 2015-09-03
Need to know what your running.

Please post the final output of ..

```
sudo apt-get install -y inxi && inxi -S
```

---

### Post by Dennis N on 2015-09-03
If you are expecting to see screensavers, there no longer are any in gnome-screensaver. It is now basically a screen locker. 

Wikipedia: 
> In GNOME 3, GNOME Screensaver was drastically simplified, supporting only screen blanking and no graphical screen savers.
source: [https://en.wikipedia.org/wiki/GNOME_Screensaver](https://en.wikipedia.org/wiki/GNOME_Screensaver)
If you want real screensavers in Ubuntu, Lubuntu, or Xubuntu you need to use xscreensaver. In Ubuntu MATE, there is MATE Screensaver, which can use the same screensavers as xscreensaver.

---

### Post by Daniyal_Javani on 2015-09-04
> **v3.xx said:**
> Need to know what your running.

Please post the final output of ..

```
sudo apt-get install -y inxi && inxi -S
```

```
$ sudo inxi -S
System:    Host: DEMON Kernel: 4.1.4-040104-generic x86_64 (64 bit) Desktop: N/A Distro: Ubuntu 14.04 trusty
```

```
$ inxi -S
System:    Host: DEMON Kernel: 4.1.4-040104-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
```

> **Dennis N said:**
> If you are expecting to see screensavers, there no longer are any in gnome-screensaver. It is now basically a screen locker. 

Wikipedia: 

source: [https://en.wikipedia.org/wiki/GNOME_Screensaver](https://en.wikipedia.org/wiki/GNOME_Screensaver)
If you want real screensavers in Ubuntu, Lubuntu, or Xubuntu you need to use xscreensaver. In Ubuntu MATE, there is MATE Screensaver, which can use the same screensavers as xscreensaver.

My problem is that "Turn screen of when inactive for" and "Lock screen after" in  Brightness & Lock not working. I think it's related to gnome-screensaver.

---

### Post by v3.xx on 2015-09-04
Your running the gnome desktop.  Something I do not run and beyond the basics, I do not know.  I will not be able to assist you any farther :(

I would suggest that you tag your thread "ubuntu gnome" to help draw in the right people.

Good luck

And thanks for the heads up on that DennisN :)

---

### Post by Daniyal_Javani on 2015-09-04
> **v3.xx said:**
> Your running the gnome desktop.  Something I do not run and beyond the basics, I do not know.  I will not be able to assist you any farther :(

I would suggest that you tag your thread "ubuntu gnome" to help draw in the right people.

Good luck

And thanks for the heads up on that DennisN :)

Thanks, you solve my problem. I'm using unity (The default DE of Ubuntu) but previously I install gnome-shell and remove it. Could you please help me to change desktop completely to unity?

---

### Post by v3.xx on 2015-09-04
I would suggest at this point starting a new thread on how to remove gnome-shell from unity.

---

### Post by Daniyal_Javani on 2015-09-05
Sorry seems my problem wasn't that: [http://ubuntuforums.org/showthread.php?t=2293345&p=13350084#post13350084](http://ubuntuforums.org/showthread.php?t=2293345&p=13350084#post13350084)

Do you have any idea?
How can I check if gnome-screensaver is running or not? And if not, How can I run it?

---

### Post by brian-mccumber on 2015-09-05
Here is a link to gnome-screensaver-command. You could use those commands to get info about and control your gnome sceensaver. When I first installed Ubuntu I found that gnome screensaver just blanks the screen so I uninstalled gnome screensaver and installed xscreensaver so I am also putting a link to the article I used to to do this. I know it says 12.04 but I used it for 14.04 without a problem. If you choose to install xscreensaver make sure to read the whole article, especially the part about adding it to startup which I didn't do the first time because I stopped reading right after I installed it and it did not start working until I added ```
xscreensaver -nosplash
``` to a new start-up program and rebooted my computer.

[http://linux.die.net/man/1/gnome-screensaver-command](http://linux.die.net/man/1/gnome-screensaver-command) 

[http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/](http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/)

---

