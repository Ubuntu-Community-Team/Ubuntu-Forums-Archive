---
title: "Some snap packages installed by default ?"
date: 2018-05-25
forum: General Help
---

### Post by linuxyogi on 2018-05-25
Hi,

I am using 18.04

```
$ snap list
Name                  Version    Rev   Tracking  Developer  Notes
core                  16-2.32.8  4650  stable    canonical  core
gnome-3-26-1604       3.26.0     64    stable/…  canonical  -
gnome-calculator      3.28.1     167   stable/…  canonical  -
gnome-characters      3.28.0     86    stable/…  canonical  -
gnome-logs            3.28.0     31    stable/…  canonical  -
gnome-system-monitor  3.26.0     39    stable/…  canonical  -

```

I haven't installed any snap packages.

Some snap packages installed by default ?

---

### Post by monkeybrain20122 on 2018-05-25
> **linuxyogi said:**
> 

Some snap packages installed by default ?

Yes.

I uninstalled them and installed the .debs from apt instead, cut down my boot time by 1/2.

---

### Post by linuxyogi on 2018-05-25
> **monkeybrain20122 said:**
> Yes.

I uninstalled them and installed the .debs from apt instead, cut down my boot time by 1/2.

The list has

```
 gnome-3-26-1604 
``` 

The entire gnome. I dont feel confident to uninstall it. It may break the whole installation.

If this is not a problem security wise I am going to leave it alone.

---

### Post by monkeybrain20122 on 2018-05-25
> **linuxyogi said:**
> The list has

```
 gnome-3-26-1604 
``` 

The entire gnome. I dont feel confident to uninstall it. It may break the whole installation.

If this is not a problem security wise I am going to leave it alone.

You can safely remove it if you are not using other gnome snaps, that is for installing gnome snap applications such as (gasp!) gnome recipe since "gnome likes to cook" :p(quoted from a blog post advertising it) There is of course no .deb replacement for this one. I have removed it and snapd, there is no problem.

---

### Post by sgage on 2018-05-28
That 'gnome-3-26-1604' snap contains the necessary Gnome 26 libraries and supporting files backported from 16.04. It seems that most of the snaps that are available were built against Gnome 26, and so you need this ball o' stuff for those snaps. The pre-loaded snaps that come with 18.04 all depend on it, but if you're going to remove those, you won't break anything by removing it - 18.04 itself runs on the Gnome/Gnome Shell 28 stack.

---

### Post by linuxyogi on 2018-09-17
> **monkeybrain20122 said:**
> Yes.

I uninstalled them and installed the .debs from apt instead, cut down my boot time by 1/2.

Following  your advice I just did 

```
sudo apt autoremove --purge snapd 
```

but boot time is the same.

```
$ systemd-analyze 
Startup finished in 10.600s (firmware) + 11.559s (loader) + 2.248s (kernel) + 22.823s (userspace) = 47.231s
graphical.target reached after 22.800s in userspace


```

---

### Post by linuxyogi on 2018-09-20
Bump

---

