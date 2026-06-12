---
title: "Beryl+KDE... 30+ workspaces!"
date: 2007-04-30
forum: General Help
---

### Post by GSF1200S on 2007-04-30
Should be an easy fix.. I have KDE configured to have 4 workspaces. When KDE uses Kwin, I have 4 workspaces as im supposed to. I have Beryl setup for 4 number of desktops and 4 horizontal virtual size.

But for some reason, the workspace switcher has 30+ workspace slots on it whenever Beryl is running. It actually pushes the system tray off the screen, forcing me to remove the workspace switcher from the taskbar. It might also help to note that only four of the workspaces (the first 4) will actually work. The other 20 some workspaces wont do anything.

---

### Post by Nythain on 2007-04-30
odd... though i would like to point out that the ones in beryl arent different desktops per say, they are viewports or some jazz like that... have you tried installing the compiz kicker and using it instead of the regular one

---

### Post by GSF1200S on 2007-04-30
> **Nythain said:**
> odd... though i would like to point out that the ones in beryl arent different desktops per say, they are viewports or some jazz like that... have you tried installing the compiz kicker and using it instead of the regular one

No... isnt that going to be an issue with Beryl.. Im venturing to guess Adept has it?

I know about virtual vs. real workspaces. Its weird, because this isnt an issue on GNOME. Right now, according to Beryl and KDE I have one workspace, but the workspace switcher has 8 tiles... If I mouse down to them, every tile thumbnail says "desktop 1."

Weird huh?

---

### Post by GSF1200S on 2007-04-30
Did the compiz package anyway via a deb package, and now I understand.

The biggest thing screwing me up was how GNOME works. In GNOME, the workspace switcher stays the same whether beryl is on or not. In KDE, the workspace switcher not only lists by workspace, but also by how many cube sides you have. So, in Gnome w/ Beryl (4 sided cube) with 4 workspaces, I still would only have 4 tiles on the switcher. In KDE, I would have 16, as its listing all 4 sides of all 4 workspaces. Kind of confusing... thanks for the compiz kicker idea...

---

### Post by hyperair on 2007-04-30
Beryl's "desktops" aren't really desktops. They're just one massive desktop that is stretched 4x to form a cube. First of all, in Gnome (I'm not so sure about KDE) go to Beryl Settings Manager, and under General Options->Main, look for Number of Desktops and reduce it to 1. This is essential if you plan to use the workspace switcher in Gnome. Next, look for Horizontal Virtual Size and set that to how many desktops you want. The number will determine how many faces of the "cube" there are. If you want 30 desktops, then have the horizontal virtual size set to 30.

For Compiz, it's pretty much the same but it's in gconf-editor instead.

---

### Post by GSF1200S on 2007-04-30
> **hyperair said:**
> Beryl's "desktops" aren't really desktops. They're just one massive desktop that is stretched 4x to form a cube. First of all, in Gnome (I'm not so sure about KDE) go to Beryl Settings Manager, and under General Options->Main, look for Number of Desktops and reduce it to 1. This is essential if you plan to use the workspace switcher in Gnome. Next, look for Horizontal Virtual Size and set that to how many desktops you want. The number will determine how many faces of the "cube" there are. If you want 30 desktops, then have the horizontal virtual size set to 30.

For Compiz, it's pretty much the same but it's in gconf-editor instead.

Right.. basically beryl desktops are "imaginary."

As far as GNOME goes, I have 4 seperate workspaces, as well as Beryl having 4 cube faces and it works fine. Basically, if im on desktop 1, rotating the cube will explore all applications open on desktop 1, etc. It hasnt caused me any problems.

Imagine my confusion when I log onto KDE and I have over 30 tiles on the workspace switcher! haha... funny stuff

---

### Post by hyperair on 2007-04-30
That is one of the factors i just hate KDE and stick to Gnome. There are other factors as well, but I don't think this is the place to discuss such things.

---

### Post by russianbandit on 2007-05-01
I had similar problems as the OP.
Thanks for explaining all of this. It seems there's really no work around in KDE + Beryl for this.
You either have 1 KDE desktop and 4 Beryl desktops, which cause the Taskbar to display windows from all of the beryl desktops.
Or you have 4 KDE desktops and 1 Beryl desktop and then you don't get the benefits of the Cube.

What is this Compiz kicker? What does it do?

---

### Post by GSF1200S on 2007-05-01
> **russianbandit said:**
> I had similar problems as the OP.
Thanks for explaining all of this. It seems there's really no work around in KDE + Beryl for this.
You either have 1 KDE desktop and 4 Beryl desktops, which cause the Taskbar to display windows from all of the beryl desktops.
Or you have 4 KDE desktops and 1 Beryl desktop and then you don't get the benefits of the Cube.

What is this Compiz kicker? What does it do?
Install the compiz kicker. Right click on panel of choice and go to add aplet. Add Compiz Desktop Preview and Pager, and restart X... For some reason when I did this, it now acts the same way as GNOME with 4 tiles for 4 desktops. You still get the cube, and each workspace essentially has its own cube.

Good Luck!

Thanks to the poster with info on the compiz kicker...

---

### Post by hyperair on 2007-05-01
Hey if that works maybe, just maybe I'll try out kubuntu-desktop again!

---

