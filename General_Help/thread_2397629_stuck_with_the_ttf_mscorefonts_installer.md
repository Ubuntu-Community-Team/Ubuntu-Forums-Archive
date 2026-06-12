---
title: "stuck with the ttf mscorefonts installer"
date: 2018-08-01
forum: General Help
---

### Post by christon74 on 2018-08-01
Good afternoon fellow ubunters:smile:
I thought upgrading to 18.04 LTS would be a cake walk, but it's not:confused:
In the beginning, everything seem to just roll, until I got this nagging screen about True type fonts for the web EULA, with a rather long text and <ok> at the end. Typing "enter" does not help. There still seems to be some process going on in the background. I cannot exit the terminal window or kill the terminal, and it seems I cannot even restart the computer. What if I force restart it? Do I end up with a not workable system? 
Thanks for any answer.

---

### Post by howefield on 2018-08-01
Press the tab key to highlight the OK button and then press enter, next screen will most likely be a Yes or No question, again tab and enter to proceed.

---

### Post by christon74 on 2018-08-01
Wow! thanks a lot! _ Aaargh! I was too rash, and before receiving your answer I killed the terminal. As a result, I guess the install is incomplete, so Ubuntu 18.04 does not load, neither does the older version (16.04LTS). Only solution, download 18.04LTS, burn it to a DVD and install it this way. Which means I have obviously lost some data. Silly me, silly me!!!

---

### Post by Impavidus on 2018-08-01
Don't assume you've lost data. With the live disk (=install disk) you should be able to access your hard drive and copy any files you want to an external drive before installing Ubuntu.

---

### Post by christon74 on 2018-08-01
Thank you impavidusO:) but I have already done a fresh install of 18.04 LTS. It has taken some time. All is not lost however_ I am not a "back-up pro", but when I need important documents, I know how to save them to an external hard disk, and thanks to a small LaCie  hard drive, I have retrieved the most important things. All I need do now is import all my e-mail contacts.

---

### Post by christon74 on 2018-08-02
Good morning again fellow ubuntersO:)
Again! I have got this "end-users agreement for microsoft software" screen and I am stuck again. I have tried enhancing the OK hitting the tab key to no avail. no key does the trick. I have tried a combination of alt+ tab, shift+tab. Nothing. Or should I simply kill the terminal? I was just trying to install the third party codecs and extras.....

---

### Post by slickymaster on 2018-08-02
Threads merged and SOLVED tag removed from the title

---

### Post by steeldriver on 2018-08-02
If you are having trouble with the ncurses interface, you can run the configurator manually with a simple text-based interface using

```

sudo dpkg-reconfigure --frontend=readline ttf-mscorefonts-installer

```

---

### Post by martinfreya on 2018-08-30
I had the same problem (Xubuntu 18.04.1)
In an old item (november 30 2016) I found the solution:
Code:
wget [http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb](http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb) -P ~/Downloads
will download the package to your Downloads folder, and
Code:
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
will install the package.

It turned out to be the solution!!
Martin

---

### Post by oldos2er on 2018-08-30
> **christon74 said:**
> Wow! thanks a lot! _ Aaargh! I was too rash, and before receiving your answer I killed the terminal. As a result, I guess the install is incomplete, so Ubuntu 18.04 does not load, neither does the older version (16.04LTS). Only solution, download 18.04LTS, burn it to a DVD and install it this way. 

Not being able to install ttf-mscorefonts-installer won't render your system unbootable. Since you installed 18.04 it's a moot point though.

---

### Post by HermanAB on 2018-08-30
BTW, the Redhat Liberation fonts are exactly the same as the MS TTF fonts and have been available for many years already:
[https://www.redhat.com/en/blog/liberation-fonts](https://www.redhat.com/en/blog/liberation-fonts)

---

