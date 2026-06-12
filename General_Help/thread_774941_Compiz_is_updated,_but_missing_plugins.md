---
title: "Compiz is updated, but missing plugins?"
date: 2008-04-29
forum: General Help
---

### Post by EpicDem on 2008-04-29
ok, so i am an Ubuntu n00b, but i also have some friends who use it regularly and they are stumped, so i turn to you.
I have compiz fusion and love it.  as to how i installed it i have no idea, just looked around the internet and ended up with:

```
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig0
```

Well, looking on the compiz site, I realized that I'm missing some plugins (mainly Atlantis).  I figured it wasn't a problem, i would just update compiz.  well, whenever i try:

```
sudo apt-get install compiz
```

it claims that i already have the latest version and does nada.  am i even doing it right?  any help?

---

### Post by EpicDem on 2008-04-29
Ok, i think i made things worse...  i did a complete uninstall (using sudo apt-get remove), then reinstall with the origional code and with compiz-fusion-plugins-unsupported.  for some reason i had to alter more of the code, ending up with 
```
sudo apt-get install compizconfig-settings-man compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-fusion-plugins-unsupported compizconfig-backend-gconf compiz-gnome compiz-plugins libcompizconfig0
```
i ran this, and it gave me the following:

dpkg: error processing /var/cache/apt/archives/compiz-fusion-plugins-extra_0.7.4-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/compiz/3d.xml', which is also in package compiz-fusion-plugins-unsupported
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-fusion-plugins-extra_0.7.4-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

then it gave me a crash message at the top of the screen, and now the advanced desktop settings options is under system->preferences, and it opens compiz and has all the plugins, but none of them are having any effect on the computer...  halp please?

---

### Post by Zorael on 2008-04-29
I don't think Atlantis is included in the build available from the repositories. Try the git install script, it'll get you the latest (unstable) build.

[http://ubuntuforums.org/showthread.php?t=763829](http://ubuntuforums.org/showthread.php?t=763829)

---

