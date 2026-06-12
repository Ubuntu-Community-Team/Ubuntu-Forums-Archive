---
title: "libglew2.1 needed to install game on Jammy"
date: 2022-08-16
forum: General Help
---

### Post by temporos on 2022-08-16
I upgraded yesterday from Focal to Jammy, and I'd like to re-install a game I was playing called *Endless Sky* (fun, top-view space shooter similar to the old *EV Override* series). After adding the game PPA, *apt* refused to install it, because it said *libglew2.1* was a dependency that couldn't be installed.

I did a bit of searching on the Almighty Googlez and found that this library was included in Focal, but not in Jammy. How do I get it, so I can install the game? It's not in the Ubuntu repositories for Jammy—it is in the Ubuntu Universe for Focal.

It should be noted that this game is rather old, and the latest version was released in mid-2020, so there's not likely to be an update to remove old dependencies...

---

### Post by &amp;KyT$0P# on 2022-08-16
> **temporos said:**
> I'd like to re-install a game I was playing called *Endless Sky* 

Would it happen to be [this one]("https://flathub.org/apps/details/io.github.endless_sky.endless_sky")?  If so I would recommend trying installing it through [Flatpak]("https://www.flatpak.org/").
(If this game has save data, the flatpak might use a different location for that, you might need to copy your old save data into the new location.)

If that flatpak is not the game you're looking for, you might try to compile the [focal source package from which libglew2.1 is built]("https://packages.ubuntu.com/source/focal/glew") on jammy and install the generated libglew2.1 deb.

---

