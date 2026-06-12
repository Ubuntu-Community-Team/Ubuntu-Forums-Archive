---
title: "As Muon is Deceased, what are the Possibilites? Synaptic, or..."
date: 2024-09-20
forum: General Help
---

### Post by ne29914 on 2024-09-20
Running Lubuntu, and Muon is apparently dead. What's a good replacement for package management?
Synaptic looks like a good candidate, are there other suggestions?

Thanks.

---

### Post by guiverc on 2024-09-20
I don't use *package managers* often, but if I do, it's mostly aptitude.

Its a terminal based package manager, but I tend to do all package management at terminal anyway (*which maybe why it suits me best*).

Some details provided by `apt info aptitude` include

> Description: terminal-based package manager

 aptitude is a package manager with a number of useful features,
 including: a mutt-like syntax for matching packages in a flexible
 manner, dselect-like persistence of user actions, the ability to
 retrieve and display the Debian changelog of most packages, and a
 command-line mode similar to that of apt-get.
 

Lubuntu still includes Plasma-Discover

FYI:  I'm never using `aptitude install` for non-interactive installs; I use `apt` for those, but when I want a package manager to search & tag for install multiple packages (eg. wallpapers), `aptitude` is my go to.

---

### Post by QIII on 2024-09-20
Muon never impressed me, although it was standard with Kubuntu.  I think Synaptic is a much better option as a graphical interface if you don't want to use apt in the command line.

---

### Post by ne29914 on 2024-09-20
Thanks.
Sorry that I was unclear: I need a GUI manager.

---

### Post by TenPlus1 on 2024-09-22
Synaptic Package Manager is still one of the best, you just have to be careful in what you are doing.

---

### Post by Rubi1200 on 2024-09-22
> **TenPlus1 said:**
> Synaptic Package Manager is still one of the best, you just have to be careful in what you are doing.
+1
Totally agree.

I would recommend installing and using Synaptic.

---

### Post by ne29914 on 2024-09-22
Synaptic installed.
Thanks for all your feedback.

---

