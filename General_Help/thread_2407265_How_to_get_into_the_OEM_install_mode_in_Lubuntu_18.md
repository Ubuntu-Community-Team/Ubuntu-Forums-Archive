---
title: "How to get into the OEM install mode in Lubuntu 18.04?"
date: 2018-12-01
forum: General Help
---

### Post by abdulla060 on 2018-12-01
Hi all.

I was planning to make a base image of Lubuntu that is installed on a VM to later deploy using Clonezilla onto other machines. However, when I press F4 and choose OEM install option on the start screen it just takes me to the normal installation process. so what am I missing here?

sorry for my bad English and thx in advance

---

### Post by sudodus on 2018-12-01
Most of the installation looks the same.

Did you continue the installation until the end?

What happened, when you booted into the installed (OEM?) system?

---

### Post by abdulla060 on 2018-12-01
nothing happened it just installed normally and there was no "prepare to ship to end user" button. also, I should mention that I after I choose OEM to install from the F4 menu I clicked on "start Lubuntu" then installed using the desktop shortcut rather than choosing "install Lubuntu" from the initial menu because this option does not exist I hope my explanation is clear.

---

### Post by sudodus on 2018-12-01
The dialogue (installing in UEFI mode) is promising, with the typical 'extra questions' for an OEM installation.

I should mention, that I install from the Lubuntu 18.04.1 LTS iso file **lubuntu-18.04.1-desktop-amd64.iso** (the first point release, which is debugged and polished compared to the original Lubuntu 18.04 LTS iso file.

**I selected OEM install from the grub menu** (at the very start of the live drive). I did not 'Try Lubuntu'.

... and after reboot there is the "prepare to ship to end user" icon on the desktop. See the attached screenshot.

So please try again, this time from **lubuntu-18.04.1-desktop-amd64.iso**. Good luck :-)

---

### Post by sudodus on 2018-12-01
I made a quick test in BIOS mode too. After selecting language

- I pressed **F4** and selected **OEM**,
- then selected **Install Ubuntu** (not try Lubuntu).

And the dialogue contains the typical first thing for an OEM installation 'You are installing in system manufacturer mode ...'. I think this is enough to feel confident that it will work in BIOS mode too.

---

### Post by abdulla060 on 2018-12-02
Yup using the **lubuntu-18.04.1-desktop-amd64** iso solved the problem looks like I was using the 18.10 release by mistake oops :P

---

