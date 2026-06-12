---
title: "gnome-games Missing packages"
date: 2022-02-22
forum: General Help
---

### Post by dorpapst on 2022-02-22
Hello people,
I am using Ubuntu 20.04 together with GNOME and I have just installed gnome-games via
```
sudo apt install gnome-games
```

Unfortunately, none of the games is running because it looks like some gnome themes are missing.
They just do not open. If I open them via terminal, for example running 
```
 gnome-klotski 
```
I get the following message:
```

Gtk-Message: 18:38:47.719: Failed to load module "appmenu-gtk-module"

(gnome-klotski:14159): GLib-GIO-ERROR **: 18:38:47.788: Settings schema 'org.gnome.Klotski' is not installed
[1]    14159 trace trap (core dumped)  gnome-klotski

```

I googled a bit but I have absolutely no idea what is going on here.

Can anybody tell me how to fix that?

Many greetings and thank you :)

---

### Post by Xian on 2022-02-22
If you were to install/use apt-file such as:
```
sudo apt-file search appmenu-gtk-module
```

You would probably find that you need to:
```
sudo apt install appmenu-gtk2-module appmenu-gtk3-module
```

---

### Post by dorpapst on 2022-02-23
Hello,
Thank you for your answer. 
I was running sudo apt-file search appmenu-gtk-module which gave me that output here:
```
appmenu-gtk-module-common: /usr/lib/systemd/user/appmenu-gtk-module.service
appmenu-gtk-module-common: /usr/share/doc/appmenu-gtk-module-common/changelog.Debian.gz
appmenu-gtk-module-common: /usr/share/doc/appmenu-gtk-module-common/copyright
appmenu-gtk2-module: /usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libappmenu-gtk-module.so
appmenu-gtk3-module: /usr/lib/x86_64-linux-gnu/gtk-3.0/modules/libappmenu-gtk-module.so
```

I installed all of them, first those you mentioned but after it did not work also the other ones.

I now get a different error message which looks very much like the package(s) I actually installed:
```
(gnome-klotski:47223): GLib-GIO-ERROR **: 12:14:30.066: Settings schema 'org.appmenu.gtk-module' is not installed
[1]    47223 trace trap (core dumped)  gnome-klotski
```

Something is weird here

```
sudo apt-file search org.appmenu.gtk-module                  
```
gives me
```
appmenu-gtk-module-common: /usr/share/glib-2.0/schemas/org.appmenu.gtk-module.gschema.xml
```
which is already installed :(

---

### Post by Dennis N on 2022-02-23
Rather than struggle with this problem, I might suggest an alternate package for Klotski (and other gnome games), either a Snap package or a Flatpak package. I know that at least the Flatpak works fine - I have it installed. I don't use the gnome-games launcher. The games show up in my Application Menu or Activities search.

The Snap is installable from the Software app.

The Flatpak support on 20.04 requires a bit more setup to get started. Follow the steps here:
[https://flatpak.org/setup/Ubuntu](https://flatpak.org/setup/Ubuntu)

At the end of the instructions is a link to the Flatpak store (called Flathub) where you can search for and install the game.

---

