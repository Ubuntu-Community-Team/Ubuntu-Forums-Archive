---
title: "GIMP is always crashing, any other clones of Photoshop for Lubuntu?"
date: 2019-08-13
forum: General Help
---

### Post by ardouronerous on 2019-08-13
Running Lubuntu 18.04.

GIMP is always crashing on me now and it's affecting my photomanipulation hobby. In all my years of using GIMP from Lubuntu 12.04 to 16.04, GIMP has always been my go-to-software for my hobby, but now, all of a sudden, it keeps on crashing.

These crashes wouldn't have affected me so much if there was a crash recovery option in GIMP, but there is not.

The reason why I like GIMP is that it's a little different but somewhat similar to Photoshop, are there any other clones of Photoshop available on Lubuntu that doesn't have much of a severe learning curve?

Thanks.

---

### Post by cruzer001 on 2019-08-13
Gimp 2.10, have you tried it?

Available from gimp as a flatpak or from launchpad as a ppa.

---

### Post by ardouronerous on 2019-08-13
Thanks, I'll give the PPA a try, since I've never install via flatpak before.

What is the PPA link? Also, what's the difference between installing from PPA and flatpak?

---

### Post by cruzer001 on 2019-08-13
[http://ubuntuhandbook.org/index.php/2018/04/how-to-install-gimp-2-10-in-ubuntu-18-04-17-10-via-ppa/](http://ubuntuhandbook.org/index.php/2018/04/how-to-install-gimp-2-10-in-ubuntu-18-04-17-10-via-ppa/)

The flatpak runs fine,been running it for serveral months.

---

### Post by ardouronerous on 2019-08-13
How do I install GIMP via flatpak? I've never installed a flakpak before, so I need guidance, thanks.

---

### Post by cruzer001 on 2019-08-13
As I remember just go to the gimp site and click on the package.  Flatpak dependencies will be installed.

---

### Post by deadflowr on 2019-08-13
Follow the setup guide here:[https://flatpak.org/setup/Ubuntu/]("https://flatpak.org/setup/Ubuntu/")
[s]and then you can just install it through the Software Store
In Software it'll be list as from Source:dl.flathub.org.[/s]

Nevermind, you're on Lubuntu so no gnome-software (Ubuntu Software Store)

That said if grabbing it directly from gimp's website doesn't work you can install it via command line

```
flatpak install flathub org.gimp.GIMP&#65532;
```

---

### Post by ardouronerous on 2019-08-13
When installing GIMP via flatpak on the Terminal, I got this message:

```
flatpak install https://flathub.org/repo/appstream/org.gimp.GIMP.flatpakref
The remote 'flathub', refered to by 'org.gimp.GIMP' at location https://dl.flathub.org/repo contains additional applications.
Should the remote be kept for future installations? [y/n]:
```

I don't understand what I'm saying y/n to.

---

### Post by Dennis N on 2019-08-13
You might give Krita a look and see if it does what you want.
Article comparing Gimp and Krita:
[https://www.makeuseof.com/tag/krita-free-gimp-alternative/](https://www.makeuseof.com/tag/krita-free-gimp-alternative/)
It's a KDE program so I installed it as an AppImage on Ubuntu 18.04.

Also see: [https://www.makeuseof.com/tag/5-photoshop-alternatives-can-run-linux/](https://www.makeuseof.com/tag/5-photoshop-alternatives-can-run-linux/)

---

### Post by deadflowr on 2019-08-13
> I don't understand what I'm saying y/n to.


It's asking if you want to add the flathub repository to your system or not.
Adding will allow updating (via flatpak command line) if new versions come out.

It'll also allow you to install other flatpak apps via command line.

---

### Post by ardouronerous on 2019-08-13
Okay, so y, since I want GIMP to be updated automatically.

---

### Post by SeijiSensei on 2019-08-14
I'm running the repository version of GIMP without a problem.

Does your machine have swap space?  How much?  GIMP often [needs swap]("https://ubuntuforums.org/showthread.php?t=2424008") if you're editing large images.

---

### Post by Autodave on 2019-08-14
Also running the repository version on 2 machines with no issues.  Could you give us some specs on your equipment?

---

