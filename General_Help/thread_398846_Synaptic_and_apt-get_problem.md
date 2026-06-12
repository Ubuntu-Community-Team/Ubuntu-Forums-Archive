---
title: "Synaptic and apt-get problem"
date: 2007-04-01
forum: General Help
---

### Post by secular on 2007-04-01
I did something stupid, and I hope I can get some help. I'm running Edgy Eft.

When I try to run synaptic, apt-get, and update, I get the following error in each:

```
E: The package envy needs to be reinstalled, but I can't find an archive for it.
```

Now, I can't update, install, or uninstall anything.

I tried sudo apt-get update and sudo apt-get upgrade, but I got the same error.

This came about because I was trying to uninstall my nvidia driver, which I got from the nividia site. I'm trying to do this because of frequent lock-ups, and I've seen that suggestion on several different threads.

I read that Envy could uninstall my old nvidia driver and install an new one, so that's what I tried.

I first downloaded Envy, double-clicked it, and tried to install it with gdebi. It gave me an error (something about another installation program being open, such as Synaptic.)

I then tried to use apt-get to install it this way:

```
sudo apt-get http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb
```

That gave me an error, too, and that's what started my problem with Synaptic, apt-get and update.

I know what I did was really stupid, but at least I know never to try it again.  [-X 

Any suggestions?

---

### Post by acormack on 2007-04-01
in case you have 2 installs running at the same time reboot.

then repeat the envy reinstall

sudo apt-get --reinstall install  [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb)

---

### Post by Nythain on 2007-04-01
have you tried the fantabulous sudo dpkg --configure -a or sudo aptitude clean after making sure that there arent any othe programs running that use aptitude (eg synaptic or adept)

---

### Post by secular on 2007-04-01
Thanks, Nythan. That works!

sudo dpkg --configure -a

---

