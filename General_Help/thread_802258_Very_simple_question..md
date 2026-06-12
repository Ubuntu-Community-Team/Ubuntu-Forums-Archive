---
title: "Very simple question."
date: 2008-05-21
forum: General Help
---

### Post by Infini on 2008-05-21
I'm not sure if this belongs here and pardon me if I'm wrong in putting here.

I was wondering if uninstalling removes the entirety of the program (all its files and folders) and that nothing is left behind? Y'know, because in Windows when you uninstall a program the folder is still there and has some stuff left behind and you need to go in and manually delete it all.

---

### Post by thisiam on 2008-05-21
i was thinking about this last night and came across [this]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by zvacet on 2008-05-21
> I was wondering if uninstalling removes the entirety of the program (all its files and folders)

Yes but sometimes some of dependencies are still there.You can esay fix that with 

```
sudo apt-get clean
```

---

### Post by Infini on 2008-05-21
Thanks for the quick reply. Thanks guys.

---

### Post by ugm6hr on 2008-05-21
Depends on how you install / uninstall.

*aptitude* removes everything completely, but can only be used from Terminal.

*apt-get* (and therefore Synaptic Package Manager) will remove the package itself, but not all dependencies.

---

### Post by Nameless_one on 2008-05-21
Also, if you just 'sudo aptitude remove' a package, configuration files and such will remain on your hard drive, so if you ever reinstall the program, it will find your old settings. If you want everything to go away, you should 'sudo aptitude *purge*' a program. I don't know the equivalent for apt-get, although I am pretty sure it exists, and usually it is the same as aptitude. Check the man pages.

---

### Post by ibuclaw on 2008-05-21
I personally use the **purge** option when uninstalling. Else residual config files may be left behind.

To find out if you have any residual config files, the following command should show all.
```
dpkg -l | awk '{if ($1=="rc") print $2}'
```
If you get nothing, then you are clean of all residual configs!

Else, using aptitude to purge them should be sufficient.
```
export packages=$(dpkg -l | awk '{if ($1=="rc") print $2}'); aptitude purge $packages -y
```

For cleaning out man pages, I use localepurge
```
sudo apt-get install localepurge
```

And for cleaning out libraries that have no applications using them, I use **deborphan** or **gtkorphan** for that job.
```
sudo apt-get install gtkorphan
```

Although, the old configs are left behind in your home folder!
So it is really up to you to clean out these files yourself. But it's good to know that at least your system is clean!

Two scripts that I find handy are on finding old temp files are:
```

find . -iname "*~"
find . -iname "#*#"

```
Happy Hunting!

Regards
Iain

---

