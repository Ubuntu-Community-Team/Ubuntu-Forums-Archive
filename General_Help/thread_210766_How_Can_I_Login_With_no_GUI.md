---
title: "How Can I Login With no GUI?"
date: 2006-07-07
forum: General Help
---

### Post by yosef on 2006-07-07
I have installed edubuntu on an ancient machine and itn goes so slowly that I can't do anything!  I actually typed server at boot: when I installed it but the desktop was installed anyway.  I want to get rid of the gnome and put on fluxbox, but I am not sure how to do it... I  know the first thing is to login with text only, but even that I can't figure out how to do!  The computer is a toshiba tecra 550cdt wih 64mb ram and 4gb hard drive.

---

### Post by mgor on 2006-07-07
you have 6 tty's and X is running on the 7th. you can switch to a tty by pressing ctrl+alt+F#, where # can be 1 through 7.

ctrl+alt+F1 will switch to tty1.

found a thread[0] about removing gnome.

[0] [http://www.ubuntuforums.org/showthread.php?t=210496](http://www.ubuntuforums.org/showthread.php?t=210496)

---

### Post by ajgreeny on 2006-07-07
You could use aptitude to reinstall ubuntu-desktop, then use it again to remove ubuntu-desktop.  Use aptitude, not apt-get or synaptic, as they will not remember all the packages reinstalled as aptitude will.  Beware of any dependencies it takes away, though as I understand it aptitude should deal with that automatically.

---

### Post by echo $USER on 2006-07-07
Also you can run > sudo /etc/init.d/gdm stop to completely shut donw the GUI.  Run > sudo /etc/init.d/gdm start to restart it.

---

### Post by yosef on 2006-07-07
Thank you guys, I will try this stuff out!

---

### Post by mannheim on 2006-07-07
If you really don't want to even see the login screen (which is the "gdm" screen if you are using ubuntu), then you can disable gdm in the startup scripts. That way, you will boot to a text-mode login prompt every time. To disable gdm forever in the startup scripts do:

```

sudo update-rc.d -f gdm remove
sudo update-rc.d stop 01 0 1 2 3 4 5 6 .

```


I **think** you will be able to undo this by:

```

sudo update-rc.d -f gdm remove
sudo dpkg-reconfigure gdm

```

In the meantime, you will still be able to start gdm from the text-mode console as "echo $USER" said, with "/etc/init.d/gdm start"

---

