---
title: "Install ubuntu-desktop borked KDE"
date: 2007-05-23
forum: General Help
---

### Post by bg1256 on 2007-05-23
I've been running Kubuntu Feisty since it was released, and I've enjoyed it.  But, I wanted to give Gnome another shot, as I've not tried it since Dapper, and I've heard good things about the new updates in Feisty.

So, I ran:

```
sudo apt-get install ubuntu-desktop
```

And it installed fine.

However, when I attempted to log back into KDE, I was greeted with a strange inconvenience.

When I enter K Menu and hit log out, it only gives me the "log out" option.  Only that.  Not shut down, suspend, hibernate, etc.

Also, I ran 

```
sudo apt-get remove ubuntu-desktop
```

it only removed ~41 MB out of the nearly 700 the first command installed.

Is there any way to restore things to the way they were running in KDE before without doing a fresh install?

Thanks for any help!

---

### Post by pbw on 2007-05-24
mv ~/.kde ~/.kde-bak. Then relogin and see if it's back to default kde behavior.

---

### Post by Immolatus on 2007-05-24
removing GDM using synaptic fixed this problem for me.

If you install Kubuntu and then add Gnome it will ask you which (KDM or GDM) to use. 
So, if you have Kubuntu installed use KDM. If you have Ubuntu installed use GDM, and all will remain as it was in the beginning.

---

