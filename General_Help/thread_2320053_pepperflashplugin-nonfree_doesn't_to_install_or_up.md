---
title: "pepperflashplugin-nonfree doesn't to install or update"
date: 2016-04-09
forum: General Help
---

### Post by argonvegell on 2016-04-09
This is my attempt to update pepperflashplugin-nonfree, but it bears no fruit, as you can see;

```

sudo update-pepperflashplugin-nonfree
Usage:
  update-pepperflashplugin-nonfree --install
  update-pepperflashplugin-nonfree --uninstall
  update-pepperflashplugin-nonfree --status
Additional options:
  --verbose
  --quiet
sudo update-pepperflashplugin-nonfree --install
sudo update-pepperflashplugin-nonfree --status

```

I've attempted to uninstall, then reinstall using the following code;

```

sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install

```

Still bears no fruits.

---

### Post by deadflowr on 2016-04-10
Remove it.
And then open Software and Updates

(or in a terminal run
```
software-properties-gtk
```
)
then go to Other Software and enable Canonical Partners.
Then close the window and and if given the choice choose reload.
(if no choice to reload appears run an update: *sudo apt-get update*)

Then install the package **adobe-flashplugin**.
This package now contains both old (normal?) flash and the newer pepperflash packages.
So all the pepperflash updates will come automatically with normal updates, like old (normal?) flash does.

Hope it helps.

---

### Post by argonvegell on 2016-04-10
Thanks, it worked!
I'm now running the latest Flash update, '21,0,0,213'

---

