---
title: "Gnome Desktop Environment Install"
date: 2017-06-30
forum: General Help
---

### Post by Darth4212 on 2017-06-30
I recently installed Ubuntu Studio and am loving it.....
Except for the XFCE Desktop Environment. 
It annoys me and I was wondering how, if it is even possible, to install the Gnome desktop environment on Ubuntu Studio.

---

### Post by Frogs Hair on 2017-06-30
Gnome Shell or Flashback ?

---

### Post by vanadium on 2017-07-01
This certainly will be possible. Install ubuntu-gnome-desktop to install gnome shell and all that comes with it.

---

### Post by Darth4212 on 2017-07-02
> **Frogs Hair said:**
> Gnome Shell or Flashback ?
Sorry I am sort of nooby but what the hell is Flashback?
[SIZE=1]Not meaning any disrespect by saying "what the hell" using that as sort of a way to display my confusion wanted to say that before hand before any problems show up [/SIZE]:p

---

### Post by Darth4212 on 2017-07-02
> **vanadium said:**
> Install ubuntu-gnome-desktop to install gnome shell and all that comes with it.
I was reading, I forget exactly where, that this might cause problems. I just want to be sure so I don't mess anything up. :)

---

### Post by again? on 2017-07-02
> **Darth4212 said:**
> I was reading, I forget exactly where, that this might cause problems. I just want to be sure so I don't mess anything up. :)

Install via terminal and make a note of new packages to be installed before you confirm.
I use xsel to copy the list to a file. 
xsel removes the terminal formatting and leaves you with one long line of packages.
```
sudo apt install xsel
```

Install ubuntu-gnome
```
sudo apt install ubuntu-gnome-desktop
```

Before confirming installation, highlight the new packages, open another terminal and run
(If you copy the following command, make sure to go back and highlight the new packages again before running)
```
echo $(xsel) > ubuntu-gnome-packages.txt
```
Creates a file in your home directory.
Check the file before continuing.

If you need to revert the ubuntu-gnome install, run
```
sudo apt remove $(cat ubuntu-gnome-packages.txt)
```

---

### Post by Frogs Hair on 2017-07-02
> **Darth4212 said:**
> Sorry I am sort of nooby but what the hell is Flashback?
[SIZE=1]Not meaning any disrespect by saying "what the hell" using that as sort of a way to display my confusion wanted to say that before hand before any problems show up [/SIZE]:p

The Flashback Session has traditional menus similar to Ubuntu Mate. You can find images of both the Flashback Session and Gnome Shell with a search. 
Installing a gnome session will include nautilus as the file manager , so you will have Thunar and Nautilus. There maybe other duplications as well.

---

