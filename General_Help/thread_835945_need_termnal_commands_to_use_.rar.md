---
title: "need termnal commands to use .rar"
date: 2008-06-21
forum: General Help
---

### Post by ayet on 2008-06-21
can you pls give me terminal commands to install a program that can open .rar files, tnks:KS

---

### Post by ad_267 on 2008-06-21
sudo apt-get install unrar

It's included in the ubuntu-restricted-extras package if you want to get that, adobe flash plugin, mp3 and wma etc codecs, microsoft fonts and other stuff all in one go.

sudo apt-get install ubuntu-restricted-extras

Oh and you can use:
```
apt-cache search --names-only rar
```
to search for stuff

---

### Post by ibutho on 2008-06-21
You need to enable the multiverse repository in your /etc/apt/sources.list file and then do
```
sudo aptitude update
sudo aptitude install unrar
```

---

### Post by werries on 2008-06-21
also, the "rar" package may be useful along with "unrar"

---

### Post by sksurhio on 2008-06-21
> **werries said:**
> also, the "rar" package may be useful along with "unrar"

The better thing I had done is to first install wine. search the proper from packages.ubuntu.com. After with the help of win, install WinRar. After the installation, you didn't need to enter any terminal command but just to run WinRar from menu and open the package easily with all winRar functionalities:KS

---

### Post by ad_267 on 2008-06-21
> **sksurhio said:**
> The better thing I had done is to first install wine. search the proper from packages.ubuntu.com. After with the help of win, install WinRar. After the installation, you didn't need to enter any terminal command but just to run WinRar from menu and open the package easily with all winRar functionalities:KS

No. You can use rar with the built in file roller, you don't have to use the command line at all but you can if you want to. No need to install wine just for rar archives. Why does everyone try and use Windows software in Ubuntu when the stuff in Ubuntu does the job perfectly!?

---

### Post by TVC15 on 2008-06-21
Hi all,


Why make things difficult if there is a simple solution integrated in the GUI?
By default, Ubuntu installs the Archive Manager (look in Applications -> Accessories.
The Archive Manager handles .rar files easily.

The way I use it is to right-click on a .rar file and choose "Open with Archive manager".
As simple as that!

Have fun

---

### Post by ibutho on 2008-06-21
> **TVC15 said:**
> Hi all,


Why make things difficult if there is a simple solution integrated in the GUI?
By default, Ubuntu installs the Archive Manager (look in Applications -> Accessories.
The Archive Manager handles .rar files easily.

The way I use it is to right-click on a .rar file and choose "Open with Archive manager".
As simple as that!

Have fun

There could be a specific reason why he asked for a terminal command and not a GUI application. For file roller to work with rar files, you first need to install the unrar packages anyway.

---

### Post by starscalling on 2008-06-21
sudo apt-get install rar unrar p7zip p7zip-full

file roller can then also use them.

---

