---
title: "Linux Program Dependencies"
date: 2007-05-06
forum: General Help
---

### Post by Doughy on 2007-05-06
I am fairly new to Linux, and one thing that has been bothering me about Ubuntu/Linux is all the program dependencies that are necessary to get things working correctly.  Maybe I just don't understand the system well enough, so I have some questions.

- When I install a program that has a lot of dependencies, then remove the program via a package manager, are the dependencies removed as well?

- What if two programs have the same dependencies, then one of them is removed?  How does linux know which programs are using which packages?

- Does installing all of these different dependencies bog down the system (other than hard drive space)?

- Why are there so many different packages that all have very similar names/functionality?  (libxine1, libxine-ffmpeg, libxine-gnome, etc... for example.)

I'm just bothered by the fact that everything is so messy.

---

### Post by K.Mandla on 2007-05-06
It does look messy, doesn't it? :D

1. If you tell the package manager to remove the package, it will probably leave the dependencies in place ... unless you tell it to remove them. The *aptitude* command from the terminal will strip out the dependencies and purge out configuration settings with this command. ...

```
sudo aptitude remove --purge package_name
```

You can achieve a similar effect using *apt-get* and following it with the *autoremove* command.

```
sudo apt-get remove package_name
sudo apt-get autoremove
```

2. Aptitude keeps track of which programs use which dependencies, and won't allow one to be removed if another program needs it. On the other hand, it's possible to remove a program and not remove a dependency, even when it's unneeded. That leftover program is an *orphan*.

3. Not necessarily. You could argue that it might slow some things down by taking up space on the drive, or by getting in the way of programs that are accessed frequently. But the delay is infinitesimal, and modern hardware is so fast you won't even notice it. On really, really old machines, you might find that clearing out unwanted software makes things run a little faster, but it won't be by much.

4. I'm not sure. Probably they provide different functions or are intended for different environments. It depends on the program that needs them, and how that program was built.

If you really want to avoid the "mess," start from a base installation and build up from there. That's what I do. :)

---

### Post by jrseney on 2007-05-07
Thank you for this information, it was very helpful to me after I wanted to remove a lot of kde stuff after trying kompse on gnome :)

Thanks!

---

### Post by dehmmy on 2008-01-18
Doesn't the following command work?

```

aptitude purge package_name


```


dMI

---

