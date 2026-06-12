---
title: "OpenOffice.org2 Base?"
date: 2005-04-13
forum: General Help
---

### Post by destroyingworld on 2005-04-13
Does anyone know what happened to the openoffice.org2 Base (database) packages?  They don't seem to be in the repositories anymore...

---

### Post by ubuntu_demon on 2005-04-15
[QUOTE=destroyingworld]Does anyone know what happened to the openoffice.org2 Base (database) packages?  They don't seem to be in the repositories anymore...[/QUOTE]
 openoffice2 is in universe

---

### Post by Grey on 2005-04-15
That's the whole problem.  This is what happens when you try to install it.

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-common_1.9.79.2-0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-common_1.9.79.2-0ubuntu2_all.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-l10n-en-us_1.9.79.2-0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-l10n-en-us_1.9.79.2-0ubuntu2_all.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-core_1.9.79.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-core_1.9.79.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-writer_1.9.79.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-writer_1.9.79.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-calc_1.9.79.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-calc_1.9.79.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-impress_1.9.79.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-impress_1.9.79.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-draw_1.9.79.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-draw_1.9.79.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-math_1.9.79.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-math_1.9.79.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2_1.9.79.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2_1.9.79.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-gnome_1.9.79.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-gnome_1.9.79.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 82.211.81.138 80]

---

### Post by ubuntu_demon on 2005-04-15
edit your /etc/apt/sources.list and make sure universe isn't commented
after this do a 
$sudo apt-get update

Now try installing oo2 again

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=demon666_nl]edit your /etc/apt/sources.list and make sure universe isn't commented
after this do a 
$sudo apt-get update

Now try installing oo2 again[/QUOTE]

I had to add the breezy repositories to get OpenOffice.org2.

---

### Post by ubuntu_demon on 2005-04-15
[QUOTE=Stormy Eyes]I had to add the breezy repositories to get OpenOffice.org2.[/QUOTE]
 I wouldn't advise to run breezy already on your main desktop!

When I apt-cache search for openoffice it's still there

---

### Post by Stormy Eyes on 2005-04-15
> **demon666_nl]I wouldn't advise to run breezy already on your main desktop![/quote]

It can't be worse than running Gentoo with ACCEPT_KEYWORDS="~x86" in /etc/make.conf, can it? Don't worry, I won't whinge if something breaks said:**
> When I apt-get search for openoffice it's still there

So did I, but when I tried to actually install it with just hoary on 13 April, I got 404 errors when apt tried to fetch the packages.

---

### Post by ubuntu_demon on 2005-04-15
[QUOTE=Stormy Eyes]It can't be worse than running Gentoo with ACCEPT_KEYWORDS="~x86" in /etc/make.conf, can it? Don't worry, I won't whinge if something breaks; I promise.



So did I, but when I tried to actually install it with just hoary on 13 April, I got 404 errors when apt tried to fetch the packages.[/QUOTE]
 good luck then :)

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=demon666_nl]good luck then :)[/QUOTE]

Thanks. I did a dist-upgrade last night at about 8:00PM EST and rebooted; everything's working fine so far. I'll report bugs if I find any (and be polite about it), and upgrade every couple of weeks.

---

### Post by destroyingworld on 2005-04-15
Hmm... I know that openoffice.org2 is in universe... The problem is that the database portion of it (base) is not... does anyone know why?

---

