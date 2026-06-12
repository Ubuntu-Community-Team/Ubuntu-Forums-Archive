---
title: "Can't get newest version of wine"
date: 2007-10-14
forum: General Help
---

### Post by Glunn11 on 2007-10-14
Hello Ubuntu community!
I've been working with Wine for a while, and realized that some applications in the Wine AppDB aren't working the way some maintainers have said they would. I realized that I do not have the newest version of Wine (0.9.7), even though I did follow the instructions for Ubuntu they provided on how to get Wine.

However, before I got the Internet, I did toy with an older version (0.9.46), and it seems to have stuck, even though I have uninstalled and reinstalled repeatedly.
Help!

-Glen

---

### Post by Footissimo on 2007-10-14
Hiya!

Did you do all this (i.e. putting the Wine repositories in your sources file).  Uninstall first then, from [here](http://www.winehq.org/site/download-deb)

> Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Feisty (7.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Edgy (6.10): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Dapper (6.06): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/etch.list](http://wine.budgetdedicated.com/apt/sources.list.d/etch.list) -O /etc/apt/sources.list.d/winehq.list

Then, you can install Wine from WineHQ like it were any other package, such as by using the Synaptic Package Manager under System->Administration. Alternatively, you can install from the terminal by running 'sudo apt-get update' to update APT's package information and then 'sudo apt-get install wine'.

Apologies if you have tried all this.  If you want to avoid the CLI totally then you can add the sources by going to system->admininstration-> software sources.

---

### Post by Glunn11 on 2007-10-14
> **Footissimo said:**
> Hiya!

Did you do all this (i.e. putting the Wine repositories in your sources file).  Uninstall first then, from [here](http://www.winehq.org/site/download-deb)



Apologies if you have tried all this.  If you want to avoid the CLI totally then you can add the sources by going to system->admininstration-> software sources.
Thank you for the prompt response! Yes, I have done that, three times, and still, when I type wine --version, I get the return message: Wine 0.9.46.
I'll try it again, though, for what it's worth.

---

### Post by Glunn11 on 2007-10-15
Nope - and this time, it downloaded version 0.9.41 (but I was able to use the Software Updates feature to update to, yet again, 0.9.46).

---

### Post by zvacet on 2007-10-15
> Binary packages are in the process of being built and it may take a few days for them to appear, but the source is available now. You can find out more about this release in the announcement. Check out our download page for packages for your distribution.


Read it at Wine HQ

---

### Post by HelixAgent on 2007-10-15
Try Automatix! It does everything for you and it will install the newest version of Wine, and you'll have some more software you could install.

---

### Post by Glunn11 on 2007-10-16
Automatix installs only 0.9.47, which is slight progress. However, it chooses to use a repository that seems to be nonexistent. Whenever my PC checks for upgrades, it locks up with Wine, as it says that it could not connect to the repository Automatix set for it.
I would compile from source, but the Wine documentation is very vague and expects people to know exactly what to do. In addition, it's only recommended for experts, anyways. I would think they would have a newer version than 0.9.46 in the Ubuntu binaries, chiefly because 0.9.46 is in the Ubuntu archives.

I'll just have to keep trying apt-get install/apt-get remove loops.

---

### Post by Glunn11 on 2007-10-16
I have successfully gotten 0.9.47, which I believe is the newest version available for Ubuntu. Don't know why or how it finally worked, but it did! Thanks!

---

