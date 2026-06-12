---
title: "How do i make ubuntu even smaller?"
date: 2008-05-29
forum: General Help
---

### Post by kdarkentity on 2008-05-29
As some of you know i have been working on a custom linux Os that i am calling K-OS GVE, i am currently in beta 1 of my 8.04 release and i am shooting to make this available as a live-cd, however i cannot seem to make the .iso image small enough to be able to burn to a cd.

Currently the image is 750mb in size but i am finding that there is little i can remove from it that i haven't already removed to make it small enough. For example, i have already removed ekiga, evolution, rytmbox and some bluetooth services but still i cannot produce an image under 750 mb's. 

I have been using remastersys to build my images, is there any way i can ultra compress my iso's? 

Or would it be better to just keep removing packages until i have an image small enough to burn to a cd?

What are some decent size and useless applications that come packaged with ubuntu 8.04 that i could safely remove?

---

### Post by Irony on 2008-05-29
Remove openoffice, its easy enough to install via the repositories.

---

### Post by mpsii on 2008-05-29
Isn't there a JEOS image of ubuntu that has the basic ubuntu environment?

---

### Post by bingoUV on 2008-05-29
yes, openoffice is huge and not so useful for its size.

Various language packs also take up a lot of space such as help files of applications, documentation etc. in 100 languages.

Go to /usr/share. You will find various themes, wallpapers, screensavers, iconsets, dictionaries, sounds, fonts, man pages, texinfo docs etc. You cannot use all of them. Remove the unnecessary ones.

---

### Post by kdarkentity on 2008-05-29
I will keep removing open office in mind, however i wanted to keep it available for people use right out of the box of the install. 

Is there anyhing else that is fairly useless for me to install. I have also already removed totem.

---

### Post by pointone on 2008-05-29
This may help:

```
for pkg in `dpkg --list | awk '/ii/ {print $2}'`; do echo -e "`dpkg --status $pkg | grep Installed-Size | awk '{print $2}'` \t\t $pkg" >> pkgs.tmp; done; sort -rg pkgs.tmp > pkgs; rm -f pkgs.tmp;
```

...to create a list of all installed packages sorted by installed size from largest to smallest in the file ./pkgs".

---

### Post by tamoneya on 2008-05-29
take a look at fluxbuntu.  It uses flux which is much smaller and lightweight.  It is even smaller than the xubuntu distro.

---

### Post by kdarkentity on 2008-05-30
After completly removing openoffice i managed to get my current .iso of K-OS GVE From 750 megs to a puny 213 megs. Now that almost dosen't seem right to me. Could removing Open office really free up 537 megs from the ubuntu distro?

---

### Post by WRDN on 2008-05-30
> **kdarkentity said:**
> After completly removing openoffice i managed to get my current .iso of K-OS GVE From 750 megs to a puny 213 megs. Now that almost dosen't seem right to me. Could removing Open office really free up 537 megs from the ubuntu distro?

Its possible.
I accidentally removed virtually all of the programs that ship with Ubuntu recently, just by trying to reinstall a single package.
If packages are dependent on one another, they can easily be deleted.

---

### Post by kdarkentity on 2008-05-30
Well actually i am looking at how much space open office uses in windows and actually it is roughly 450 megs so i guess that it does make sense. 

This is just one more reason why ubuntu is such a good os. Its core is tiny and yet it is still as good as or better than the windows os.

---

