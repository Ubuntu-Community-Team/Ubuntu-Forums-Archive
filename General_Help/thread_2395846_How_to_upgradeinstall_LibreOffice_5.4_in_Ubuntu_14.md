---
title: "How to upgrade/install LibreOffice 5.4 in Ubuntu 14.04 LTS"
date: 2018-07-07
forum: General Help
---

### Post by swarup on 2018-07-07
I use Ubuntu LTS 14.04. It has LibreOffice Version: 4.2.8.2, Build ID: 420m0(Build:2). 

I tried to install LO 5.4 using the guideline on this site:

[https://www.omgubuntu.co.uk/2017/07/how-to-install-libreoffice-5-4-on-ubuntu](https://www.omgubuntu.co.uk/2017/07/how-to-install-libreoffice-5-4-on-ubuntu)

It said to execute the following in a terminal window:

```
sudo add-apt-repository ppa:libreoffice/libreoffice-5-4
Enter your password when prompted, and then update and upgrade LibreOffice:

sudo apt update && sudo apt install libreoffice
```

I did the above, and a bunch of code rolled by the screen in the terminal window. But so far as I can tell, nothing got installed. When I open LO, it is still the same version I mentioned above.

---

### Post by swarup on 2018-07-07
Here is the solution: Run the commands shown in my first post. Then run:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Works like a charm. This will upgrade your LO office to version 5.4

---

### Post by Impavidus on 2018-07-08
Yes, you have to upgrade the package, not install, as it is already installed. Also, I'm not sure 14.04 already has the apt command. It may need the older apt-get. Your guide may have been too new for your system.

Of course, as Ubuntu 14.04 is getting rather old and has less than a year of support left, you could also consider to be bold and jump to a more recent Ubuntu release, which comes with a more recent version of libreoffice without resorting to a PPA. Ubuntu 16.04 comes with LO 5.1, 18.04 comes with 6.0. Ubuntu 17.10 has LO 5.4, but has almost reached end of life, so that's not an option. It's probably best to prepare for a fresh install of 18.04.

---

