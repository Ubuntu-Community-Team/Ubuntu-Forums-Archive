---
title: "GNMOE, KDE all mixed up"
date: 2008-06-25
forum: General Help
---

### Post by anjanesh on 2008-06-25
I just installed KDE desktop environment in Ubuntu in Add/Remove Programs.
Now when the PC starts and shutdown it shows a blue Kubuntu instead of the previous Ubuntu.

1. Adding an environment chaged the base OS ?

2. I installed a lot of programs like KGet etc etc - which are meant for KDE. But all these show up in my Ubuntu (GNOME) session too. Arent KDE programs to be listed in the menu is the session is KDE only ? Im now having just tooo many items in the menu list which I thought would appear only using different sessions (gnome, kde).

Thanks

---

### Post by Elfy on 2008-06-25
1 - it certainly appears change the image each time it does it - happened to me a few times.

2 - that is one of the reasons I stopped doing it and use a virtual machine if I want to play, you can edit the menu to not show the kde applications if you want to

---

### Post by Zorael on 2008-06-25
[list=1][*]Perform these commands in a terminal.
```
$ sudo dpkg-reconfigure gdm
```
Pick **gdm** instead of **kdm**.
```
$ sudo update-alternatives --config usplash-artwork.so
```
Pick **usplash-theme-_ubuntu_.so**.


[*]Yep, applications are environment-independent; you can use Nautilus in KDE and Amarok in Gnome. Were it me, I would edit my Gnome menu (using alacarte), create a section named 'KDE Apps' and move KDE stuff that you don't use into there. Then they'd be out of the way but not out of reach nor out of mind.
[/list]

---

### Post by anjanesh on 2008-06-25
Actually I want to check out all apps and note down the ones that best meets my needs as Windows (as Im migrating from Windows) and reinstall the whole base OS & then install the ones I selected.

Anyway, I've selected a lot (almost all except ones I know I wont use) and somehow a lot of dups have been installed for KDE apps.
For example - theres 2 KolourPaint, 2 KChart, 2 Kexi, KFormula etc etc.
Apparently one is for KDE 3.5.9 & the other for KDE 4.0.0-BETA.

What I dont get is, when I selected to install KDE environment, I assumed that its 4.
Do I have 2 KDEs on my machine or are the older KDE apps running on KDE 4 as well ?

Add/Remove programs should have version number as a separate column. I think I have double KDE apps - half of which are for KDE 3.5.x.

---

### Post by Zorael on 2008-06-25
Understandable. KDE is sort of in a state of transition at the moment; KDE 4 is up-and-coming and receives all the developer attention, as such it is growing fast. Kubuntu keeps ahead with the times (per Canonical policy decision) which ends up with partial KDE 4 presence in the repositories.

Unless you want to test it for the novelty and for bug-hunting, I suggest you  keep to KDE 3 for desktop use. KDE 4 apps can, of course, be run in any environment. They just need the Qt4 libraries. And may look a bit funky.

---

### Post by anjanesh on 2008-06-25
KDE is halting very often.
I cant seem to get many things done in KDE like change menu interface to the one like GNOME/Windows.

$ sudo update-alternatives --config usplash-artwork.so
changed the shutdown artwork only.
I just restarted the computer and it loads the kubuntu artwork.

With KDE I get networking issues - and sometimes on shutting down it shows some network error msg.

I guess Im going to stick to GNOME after I do a fresh install in a couple of weeks.
I just need a few KDE programs like KolourPaint for KDE 4 beta which works like MS Paint.

---

### Post by Zorael on 2008-06-25
> **anjanesh said:**
> $ sudo update-alternatives --config usplash-artwork.so
changed the shutdown artwork only.
I just restarted the computer and it loads the kubuntu artwork.
Right, I forgot. Perform this command after changing the usplash artwork to make it apply to booting.
```
$ sudo update-initramfs -u -k all
```

---

