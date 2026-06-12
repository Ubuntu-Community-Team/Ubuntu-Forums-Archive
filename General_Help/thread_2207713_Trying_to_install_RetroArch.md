---
title: "Trying to install RetroArch?"
date: 2014-02-24
forum: General Help
---

### Post by ilikecolors on 2014-02-24
I run Ubuntu 13.10 and I am trying to install RetroArch accordingly to this guide: [http://ubuntuhandbook.org/index.php/2013/11/install-retroarch-emulator-ppa-ubuntu/](http://ubuntuhandbook.org/index.php/2013/11/install-retroarch-emulator-ppa-ubuntu/)
However, when I run the first command line to install the PPA needed, I get this error: "Error: Must run as root".
Help?
[COLOR=#333333][FONT=Monaco]


[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-02-24
*Thread moved to **General Help**.*

***Installation & Upgrades*** is 'For questions about upgrading and installation of your new Ubuntu OS'. ;)

---

### Post by sffvba[e0rt on 2014-02-24
Add "sudo" to the start of each of the commands:

```

sudo add-apt-repository ppa:hunter-kaller/ppa

sudo apt-get update

sudo apt-get install retroarch libretro*
```

Some more [information on sudo]("http://en.wikipedia.org/wiki/Sudo").

---

### Post by ilikecolors on 2014-02-25
> **not found said:**
> Add "sudo" to the start of each of the commands:

```

sudo add-apt-repository ppa:hunter-kaller/ppa

sudo apt-get update

sudo apt-get install retroarch libretro*
```

Some more [information on sudo]("http://en.wikipedia.org/wiki/Sudo").
Thank you. That was pretty stupid of me.

---

