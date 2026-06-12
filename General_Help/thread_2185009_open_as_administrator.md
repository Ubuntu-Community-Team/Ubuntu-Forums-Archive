---
title: "open as administrator"
date: 2013-10-31
forum: General Help
---

### Post by rokikish on 2013-10-31
how do i get "open as administrator" for ubuntu 13.10.

---

### Post by whitesmith on 2013-10-31
One of the reasons Windows is so insecure is that it allows--even courts!--such dangerous behavior. If you want to "open as administrator" you'll have to open a terminal and do something like```
sudo myprog
```If myprog has a pretty GUI, then do this:```
gksudo myprog
```Imagine how hard it would be for a virusmonger to do this without being noticed! What you gain from not having an "open as administrator" option is security. That's how Linux is built.

---

### Post by oldos2er on 2013-10-31
See [http://ubuntuhandbook.org/index.php/2013/10/enable-open-as-administrator-ubuntu-13-10-nautilus/](http://ubuntuhandbook.org/index.php/2013/10/enable-open-as-administrator-ubuntu-13-10-nautilus/)
Warning: I haven't tried this myself so I have no idea whether it works or not. Caveat emptor.

---

### Post by ajgreeny on 2013-10-31
I don't think this is anything new in 13.10, is it?

Prior to 12.04 there was a package called nautilus-gksu or gksu-nautilus, I can't remember, which did this for us but no longer available so since 12.04 a script has been needed which I have added it to my system.  My script is much simpler than the one shown in the link above, but as I am not using 13.10, I don't know if it will work in that version of nautilus.
```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done
``` You could edit the second line of the script to **gksudo "exo-open $uri" &** if not using gnome, but if you have nautilus instaslled I think the gnome-open will work.

---

### Post by Mopar1973Man on 2013-10-31
On Lubuntu or LXDE desktop the pcmanfm (Lubuntu's File manger) has a function for opening folders as root.

---

### Post by ajgreeny on 2013-10-31
> **Mopar1973Man said:**
> On Lubuntu or LXDE desktop the pcmanfm (Lubuntu's File manger) has a function for opening folders as root.

Of course it does !!  I forgot that.

---

### Post by spera on 2014-04-23
> **ajgreeny said:**
> Of course it does !!  I forgot that.

Sorry to inform you, but it doesn't any more... And you can feel my pain...

---

### Post by stalkingwolf on 2014-04-23
so does Mint 13. just right click and select open as admin.  handy for installing fonts.

---

