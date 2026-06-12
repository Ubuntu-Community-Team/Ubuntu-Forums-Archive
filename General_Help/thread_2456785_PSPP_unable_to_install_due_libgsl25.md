---
title: "PSPP unable to install due libgsl25"
date: 2021-01-19
forum: General Help
---

### Post by hbuntux on 2021-01-19
I tried to install pspp "program for statistical analysis of data" but is not in ubuntu repositories (sudo apt-get install pspp shows that is not available).

I downloaded the package from [https://pkgs.org/download/pspp](https://pkgs.org/download/pspp). But when I tried to install by dpkg, it warned me that  libgsl25 dependencies are not installable and libspread-sheet-widget (>= 0.6) depencency is neccesary but my version is 0.3.1.

Then I tried to install from PPA [https://launchpad.net/~adamzammit/+archive/ubuntu/pspp](https://launchpad.net/~adamzammit/+archive/ubuntu/pspp) however again warned me about libgsl25. Even I could see the app icon installed, I couldn't launch it and I had to uninstall it because it broke the system due to unsolved dependencies.

¿There is someway to install pspp?

---

### Post by #&amp;thj^% on 2021-01-19
A long story, short version: [url]https://askubuntu.com/questions/1234137/why-is-the-pspp-program-not-present-in-the-ubuntu-20-04-lts-focal-fossa-reposito[/url
This seems to work as well, same version as SeijiSensei's link below: [https://pkgs.org/download/pspp](https://pkgs.org/download/pspp)

---

### Post by SeijiSensei on 2021-01-19
I eventually created a 20.10 virtual machine using VirtualBox just to run the 1.4.0 version of pspp that was compiled for Groovy. You can find it here: [http://archive.ubuntu.com/ubuntu/pool/universe/p/pspp/pspp_1.4.0-3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/pspp/pspp_1.4.0-3_amd64.deb)

---

### Post by hbuntux on 2021-01-19
Thanks so much.
Just added this repository and was able to install pspp.
[HTML]deb http://de.archive.ubuntu.com/ubuntu groovy main universe[/HTML]

---

### Post by #&amp;thj^% on 2021-01-19
> **hbuntux said:**
> Thanks so much.
Just added this repository and was able to install pspp.
[HTML]deb http://de.archive.ubuntu.com/ubuntu groovy main universe[/HTML]

Now you have installed remove the PPA, else you will end up with a nightmare for an OS<<<Unless your using 20.10 now.

---

