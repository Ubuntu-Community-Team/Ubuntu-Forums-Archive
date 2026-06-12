---
title: "beryl messed my system up"
date: 2006-11-28
forum: General Help
---

### Post by el_ricardo on 2006-11-28
ok, here's YET ANOTHER problem with beryl! I installed it using a howto i found [here]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit"). Everything went ok as i followed the step by step guide, but when i came to rebooting, i got the login screen, typed in my login details, and my desktop just failed to load. The first time i tried, i saw the beryl logo flash up for a split second, a load of weird flashy lines, followed by the login screen again. I've tried using failsafe gnome, and that didn't work, i removed the bits i added to "/etc/gdm/gdm.conf-custom" and nothing seems to have fixed it. bottom line - how can i remove beryl and everything that goes with it so i can try this again hopefully with more success?

---

### Post by brottman on 2006-11-28
First of all, that guide is for a really old hacked version of Compiz, before it was even forked as "Beryl". Second, it's designed for Dapper, not Edgy (which are you running?)

```
sudo apt-get remove xserver-xgl compiz-gnome emerald emerald-themes beryl beryl-manager
```

That should get rid of it. Be careful though. If for any reason it wants to remove a TON of packages as a result of removing xserver-xgl, then abort. 

If you tell us if you are running Dapper or Edgy we can point you to some better guides.

---

### Post by Joe_CoT on 2006-11-28
That guide told you to install Xgl, which is 1) A bad move, since Xgl basically requires replacing the default ubuntu xserver, 2) completely unnecessary since a) you could use aiglx, which comes with edgy by default, and b) the beta nvidia driver supports all this stuff **without** xserver addons.

Firstly, you'll need to reverse all those changes to conf files. then remove the repositories from your sources. then remove the packages they had you install:
```
sudo apt-get remove xserver-xgl compiz-gnome emerald emerald-themes beryl
```

then reinstall xserver
```
sudo apt-get --reinstall install xserver-xorg
```

Reinstalling xserver might not be necessary, but i'm not sure what the xserver-gxl package changes.

After that, you *should* be alright. The only good how-tos i've seen have been at beryl-project.org, but their site is apparently down currently. You can wait til they're back up, or find one that's not xgl.

---

### Post by el_ricardo on 2006-11-28
right i'll give those a go then, and i'm running edgy, after i've gotten rid of it, I'll try [this]("http://doc.gwos.org/index.php/BerylOnEdgy") howto i came across in these forums which seems to be a bit more thorough! i really want this to work, its supposed to look SWEET!

---

### Post by reclusivemonkey on 2006-11-29
> **el_ricardo said:**
> right i'll give those a go then, and i'm running edgy, after i've gotten rid of it, I'll try [this]("http://doc.gwos.org/index.php/BerylOnEdgy") howto i came across in these forums which seems to be a bit more thorough! i really want this to work, its supposed to look SWEET!

You might want to update your forum profile to reflect you are an Ubuntu 6.10 user, not Ubuntu 6.06 then people will know you are running Edgy.

Beryl on Edgy works *so* much better than it did on Dapper. If you install it correctly (and have a Nvidia card) you shouldn't have any problems.

---

