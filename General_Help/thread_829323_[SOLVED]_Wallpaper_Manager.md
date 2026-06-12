---
title: "[SOLVED] Wallpaper Manager?"
date: 2008-06-14
forum: General Help
---

### Post by Mako Eyes on 2008-06-14
I was wondering if there's anything I can get for Ubuntu that automatically changes desktop background images at a certain time interval or at every boot?

Even if it can't do this, I was wondering if there is a good alternate wallpaper manager other than Ubuntu's default one because it lags like crazy once there's more than a dozen images in it.

Thanks.

---

### Post by Ub1476 on 2008-06-14
I use Nitrogen, which works fine. Just run with:

```
nitrogen ~/Pictures/Wallpapers
```

And it will display all the pictures in that location.

I know for sure that there are some screenlets which can change the wallpaper, probably some apps to, but I can't come up on any names.. But check out screenlets on gnome-look.org. It should work fine for changing walls.

---

### Post by Mako Eyes on 2008-06-14
> **Ub1476 said:**
> I use Nitrogen, which works fine. Just run with:

```
nitrogen ~/Pictures/Wallpapers
```

And it will display all the pictures in that location.

I know for sure that there are some screenlets which can change the wallpaper, probably some apps to, but I can't come up on any names.. But check out screenlets on gnome-look.org. It should work fine for changing walls.

```
$ nitrogen ~/Pictures/Wallpapers
bash: nitrogen: command not found
```

I found a [place to download the source](http://projects.l3ib.org/nitrogen/) for installation, but I'm afraid I'm still pretty new to using Ubuntu or Linux in general and I don't know where to go with it.

However, I'll check out gnome-look for some screenlets. Thanks.

---

### Post by DaymItzJack on 2008-06-14
> **Mako Eyes said:**
> ```
$ nitrogen ~/Pictures/Wallpapers
bash: nitrogen: command not found
```

I found a [place to download the source](http://projects.l3ib.org/nitrogen/) for installation, but I'm afraid I'm still pretty new to using Ubuntu or Linux in general and I don't know where to go with it.

However, I'll check out gnome-look for some screenlets. Thanks.

If you want to try out nitrogen (I never have) you can download the deb here, which I found on the site you posted:
[http://mogaal.com/paquetes/nitrogen/nitrogen_1.0-1_i386.deb](http://mogaal.com/paquetes/nitrogen/nitrogen_1.0-1_i386.deb)

---

### Post by nkri on 2008-06-14
try Drapes; it's exactly what you described and it's in the repos.

```
sudo apt-get install drapes
```

---

### Post by Mako Eyes on 2008-06-15
> **nkri said:**
> try Drapes; it's exactly what you described and it's in the repos.

```
sudo apt-get install drapes
```

This is *perfect*; exactly what I was looking for and it also organizes them pretty neatly. It doesn't seem to monitor my wallpaper directory though, but I'll work that out.

Thanks nkri!

---

### Post by nkri on 2008-06-16
No problem!

---

### Post by agasamapetilon on 2008-06-16
Heya! This application is just great and exactly what I wanted for my Ubuntu... thanks guys for posting this!

---

