---
title: "Installing GIMP using Flatpak on Ubuntu 18.04 failed"
date: 2022-06-03
forum: General Help
---

### Post by John_Patrick_Mason on 2022-06-03
According to [this]("https://linoxide.com/install-gimp-on-ubuntu/") guide, although I was initially hesitant installing GIMP using Flatpak, the guide states that installing GIMP using Flatpak is the official way of installing GIMP on Ubuntu 18.04, so I decided to take a chance and install GIMP using Flatpak. Unfortunately, even though I copied and pasted the same commands into my terminal, I am unable to find GIMP in my list of available applications.

Could somebody have a look at the Flatpak installation process in the guide and tell me if the person who wrote the guide made any mistakes, and if so, how to remedy them? If it's not possible, how do I undo the changes that were made?

---

### Post by #&amp;thj^% on 2022-06-03
try this
```
flatpak run org.gimp.GIMP
```

---

### Post by John_Patrick_Mason on 2022-06-03
> **1fallen said:**
> try this
```
flatpak run org.gimp.GIMP
```

Thanks. That worked. Am I going to have to run the same command every time I need to access GIMP or is this a permanent solution? Sorry, but I'm more used to dealing with simple .deb packages.

---

### Post by #&amp;thj^% on 2022-06-03
if it dose not show up under [Graphics] you could just create a shortcut with that command used.
if you can edit your menu you can add it there as well using:
```
/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @@u %U @@
```
Named Gimp.
Just a nice page for reference:[https://docs.flatpak.org/en/latest/index.html](https://docs.flatpak.org/en/latest/index.html)

---

### Post by John_Patrick_Mason on 2022-06-03
> **1fallen said:**
> if it dose not show up under [Graphics] you could just create a shortcut with that command used.
if you can edit your menu you can add it there as well using:
```
/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @@u %U @@
```
Named Gimp.
Just a nice page for reference:[https://docs.flatpak.org/en/latest/index.html](https://docs.flatpak.org/en/latest/index.html)

Thanks. I think I'll just do an:

```
alias gimp='flatpak run org.gimp.GIMP > /dev/null 2>&1 &'
```

to allow me to access GIMP from the command line from now on. Since I'm more familiar with .deb packages, at first, I wasn't sure whether running the:

```
flatpak run org.gimp.GIMP
```

command was just another part of the installation process or whether I could just run the command in order to run GIMP. If I knew, beforehand, that I could open GIMP by typing:

```
flatpak run org.gimp.GIMP
```

I would have created an alias for that command. However, I'm not sure if I understand the:

```
/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @@u %U @@
```

command. When you say adding a shortcut to the 'menu,' you mean adding a shortcut to the Dock? Because I tried inputting the above command into the terminal and it failed to create a shortcut on the Dock.

---

### Post by Dennis N on 2022-06-03
The name it uses in the Application Menu is not Gimp. It's "GNU Image Manipulation Program". So you may not recognize it. But if you do search for "Gimp" in the Overview Screen search, you should find it. Does that work? See screenshot (from Ubuntu 18.04, where I also have the Flatpak installed.).

---

### Post by John_Patrick_Mason on 2022-06-03
> **Dennis N said:**
> The name it uses in the Application Menu is not Gimp. It's "GNU Image Manipulation Program". So you may not recognize it. But if you do search for "Gimp" in the Overview Screen search, you should find it. Does that work? See screenshot (from Ubuntu 18.04, where I also have the Flatpak installed.).

Oh, it works. I just couldn't find GIMP when I would search for "GIMP" in the Overview Screen search until after I ran the following command:

```
flatpak run org.gimp.GIMP 
```

I just wasn't sure what 1fallen's second command was supposed to do given that nothing happened after I inputted it into a terminal. I should note that I'm under Ubuntu 18.04, which uses Gnome as its desktop environment, so I don't really have an application *menu*, per say, so I'm not sure if his post was meant for people who use Kubuntu or Xubuntu, which do have proper application menus.

---

### Post by Dennis N on 2022-06-04
>  I don't really have an application menu...
Correct, there is not one in the default install. But you could have one - all the application menus (there are several to choose from) are gnome shell extensions. Attached is a screeenshot of probably the most basic one. I have one so that I can view applications by category when I want to.

---

### Post by #&amp;thj^% on 2022-06-04
> **John_Patrick_Mason said:**
> 

I just wasn't sure what 1fallen's second command was supposed to do given that nothing happened after I inputted it into a terminal. 
That was referring to adding to your menu, and yes I was well aware you was using 18.04
```
/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @@u %U @@

Note that the directories 

'/var/lib/flatpak/exports/share'
'/home/me/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

Gtk-Message: 14:08:23.992: Failed to load module "atk-bridge"
Gtk-Message: 14:08:23.997: Failed to load module "canberra-gtk-module"


```
A menu editor is always nice to have, I use "menulibre" works well for me.
Thanks to Dennis N for picking up my hurried reply's and help making it a bit more clear.
```
 sudo apt install menulibre
```
to use it just run
```
menulibre
```
for a nice GUI.

---

### Post by John_Patrick_Mason on 2022-06-04
> Note that the directories 

'/var/lib/flatpak/exports/share'
'/home/me/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

I see. I'm just more used to .deb packages, where you can use the application immediately without having to restart.

I just did a:

```
printenv
```

to see what the XDG_DATA_DIRS variable is set for, and noticed /var/lib/flatpak/exports/share and /home/$USERNAME/.local/share/flatpak/exports/share were there. Were these added automatically to $XDG_DATA_DIRS after I rebooted?

I also tried to run the command:

```
 /usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @@u %U @@
```

but I keep getting an error in GIMP:

```
Opening '/home/$USERNAME/%U' failed: Error opening file /home/$USERNAME/%U: No such file or directory
```

Do I need to install the menulibre package first?

---

### Post by #&amp;thj^% on 2022-06-04
> **John_Patrick_Mason said:**
> Were these added automatically to $XDG_DATA_DIRS after I rebooted?

Yes Sir. and sorry I really was rushed yesterday, too many irons in the fire ATM.
:)

---

### Post by John_Patrick_Mason on 2022-06-04
[QUOTE=1fallen]Yes Sir. and sorry I really was rushed yesterday, too many irons in the fire ATM.[/QUOTE]

That's okay. I really appreciate you taking time out of your busy schedule to answer some of my questions.

---

