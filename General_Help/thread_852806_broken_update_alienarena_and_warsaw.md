---
title: "broken update alienarena and warsaw"
date: 2008-07-07
forum: General Help
---

### Post by bogdanbiv on 2008-07-07
The following packages keep showing up on my update packages list (in Adept). Installing updates seems to work just fine but then again I see these packages up for update tomorrow. So I decided to investigate.

I fired up Synaptic, I chose 'Custom filters' and then upgradable. Only three packages to upgrade:
alien-arena, alien-arena-browser and warsaw
I marked them for update and applied changes.
After downloading (at install phase) I got these errors in a popup:

-------------------
alien-arena:
  Depends: alien-arena-data (>=7.0) but 6.10-1 is to be installed

alien-arena-browser:
  Depends: alien-arena (>=7.0-1~hardy1) but 6.10-2 is to be installed

warsow:
  Depends: warsow-data (>=0.42) but 0.32-1 is to be installed
-----------------

It's not a major issue for me (it's just annoying) as I don't play much alien-arena, but someone may have real trouble with it.

Medium:
Kubuntu 8.04, KDE 3.5.9

$ uname -a
Linux bog-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

I try to keep up with the updates for Ubuntu, so I otherwise the update list is (almost) empty.

---

