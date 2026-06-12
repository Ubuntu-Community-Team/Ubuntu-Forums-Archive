---
title: "4gb dmg expands to 30gb???"
date: 2013-10-11
forum: General Help
---

### Post by bewareofthephog on 2013-10-11
I have a 4gb DMG that I want to burn to a blu-ray disc.  When I convert it to img it expands to 30gb which is 5gb over the blu-ray capacity.  There's no way this actually holds 30gb of data, is there???  How do I get around this?

---

### Post by varunendra on 2013-10-12
If you open or mount the dmg image on MAC or with archive manager (with "p7zip-full" installed) on Ubuntu, then copy-paste the contents, does the size remain the same?

Note that DMG is a 'compressed archive' format, means its contents can be larger than its own size. Besides, there are some special cd/dvd images that contain some sort of multiple hardlinks to some common contents on them. While this physically occupies the space just once on the disc, it makes that content appear at multiple places, thus occupying the same space multiple times when copy-pasting.

You may also try installing CDemu on Ubuntu to try mounting it (not guaranteed if it is a non-standard DMG) and check the properties of the contents to see how much space they 'seem' to occupy. CDemu is a virtual CD/DVD drive emulator and can mount DMG images. It is not in the repositories and needs to be installed via ppa -
```
sudo add-apt-repository ppa:cdemu/ppa
sudo apt-get update
sudo apt-get install gcdemu
```
[Note: If using Unity, you may have to manually add "gcdemu" to the "systray-whitelist" to enable its launcher icon the panel (dconf-Editor > desktop > unity > panel > systray-whitelist > add 'gcdemu' to the existing list)]

---

