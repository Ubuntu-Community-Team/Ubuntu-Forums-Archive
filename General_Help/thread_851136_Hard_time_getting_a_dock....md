---
title: "Hard time getting a dock..."
date: 2008-07-06
forum: General Help
---

### Post by Shiv4m on 2008-07-06
Hey guys I'm having a real difficult time getting a dock to work, I keep trying and trying cairo-dock but i end up with the same error:

[IMG]http://img86.imageshack.us/img86/6801/screenshotshivamshivamlxu0.png[/IMG]

Please help thank you...:confused:

---

### Post by tech0007 on 2008-07-06
sudo apt-get install libglitz-glx1

---

### Post by Shiv4m on 2008-07-06
This is what I get:

[IMG]http://img355.imageshack.us/img355/7839/screenshotshivamshivamlsa5.png[/IMG]

When I try to launch Cairo-Dock from Terminal or ALT+F2 thing nothing comes up.

---

### Post by tech0007 on 2008-07-06
make sure that both these files exist:
/usr/lib/libglitz-glx.so.1
/usr/lib/libglitz-glx.so.1.0.0

you may need to remove and reinstall both cairo-dock and libglitz-glx1 using synaptic.

---

### Post by Shiv4m on 2008-07-06
How do I do that for both?

---

### Post by Shiv4m on 2008-07-06
I don't have any of those 2 inside the lib folder, what should I do now?

---

### Post by fabounet on 2008-07-08
try to install the dev packages too with Synaptic

---

### Post by saratchandra on 2008-07-08
The official cairo-dock debs don't work with amd64 systems. Remove cairo-dock completely, download [ubuntu tweak]("http://getdeb.net/release/2890") from here and enable cairo-dock sources from there(its in third party software). Then install cairo-dock from synaptic. Those sources worked perfectly for me.

---

### Post by fabounet on 2008-07-09
there are 64bits packages for CD, and I've heard they work.
There is a thread on this forum about it. Or maybe you can look into the Cairo-Dock wiki.

---

### Post by Shiv4m on 2008-07-10
> **saratchandra said:**
> The official cairo-dock debs don't work with amd64 systems. Remove cairo-dock completely, download [ubuntu tweak]("http://getdeb.net/release/2890") from here and enable cairo-dock sources from there(its in third party software). Then install cairo-dock from synaptic. Those sources worked perfectly for me.
The site doesn't work for me, any of sites?

---

### Post by saratchandra on 2008-07-10
> **Shiv4m said:**
> The site doesn't work for me, any of sites?

Try this

> [http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.3.4-1%7Eppa1_all.deb](http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.3.4-1%7Eppa1_all.deb)

---

