---
title: "Alarming Hardy Heron crash after update"
date: 2008-05-20
forum: General Help
---

### Post by dayanandasaraswati on 2008-05-20
Hello friends,
       Yesterday morning i updated my hardy heron and after reboot system did not work. I found a bunch of problems arising.
1. During login screen it says one of the svg images from usr/share/.... direcctory is corrupted and loads another login screen instead of the default login screen.
2. after i key in my user id and password, I get a screen which has a pop up saying "hal failed to initialize". After that nothing loads in the screen.

I went into the failsafe terminal mode and type nautilus. This is wat it had to say> nautilus: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: glib_gettext

I reinstalled nautilus, gdm, ubuntu-desktop using apt-get. Stil problem persists. Problem with the login screen is also tolerable, but find me a solution to the second problem.

NOTE: Two days before I updated my system I installed gtk. I used my system a couple of times before the crash without any problem. This crash happened only after update

---

