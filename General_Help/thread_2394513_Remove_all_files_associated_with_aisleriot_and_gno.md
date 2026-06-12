---
title: "Remove all files associated with aisleriot and gnome-mahjongg"
date: 2018-06-17
forum: General Help
---

### Post by cscj01 on 2018-06-17
I use the following command to remove aisleriot:```
sudo apt remove --purge aisleriot
```
Similarly, I use```
sudo apt remove --purge guile-2.0-libs
sudo apt remove --purge gnome-mahjongg
```to get rid of some libraries associated with aisleriot and gnome-mahjongg.

However, if I search the system for aisleriot or gnome-mahjongg, I find files in> /usr/share
usr/share/branding
usr/share/app-install/desktop
/usr/share/help-langpack/en_GB
/usr/share/locale-langpack/en_AU/LC_MESSAGESand other places.

I want to remove anything related to games.  How do I do this?

---

### Post by Holger_Gehrke on 2018-06-17
I'd be a bit more careful and check what the packages are and what they do. 'guile-2.0-libs' is an interpreter and runtime system for the programming language guile (a variant of scheme, which is a lot like lisp ...) that is used by many programs as an extension language. 'apt show <package-name>' will give you a description of <package-name>. To find out what package a file is part of you can use 'dpkg -S <filename-with-full-path>'. The stuff in /usr/share/app-install is used be the 'Software'-Application. The files in help-langpack and locale-langpack are basic language packages. The translated messages for all the basic gnome applications come in one big package per language.

Holger

---

### Post by cscj01 on 2018-06-17
> **Holger_Gehrke said:**
> I'd be a bit more careful and check what the packages are and what they do. 'guile-2.0-libs' is an interpreter and runtime system for the programming language guile (a variant of scheme, which is a lot like lisp ...) that is used by many programs as an extension language. 'apt show <package-name>' will give you a description of <package-name>. To find out what package a file is part of you can use 'dpkg -S <filename-with-full-path>'. The stuff in /usr/share/app-install is used be the 'Software'-Application. The files in help-langpack and locale-langpack are basic language packages. The translated messages for all the basic gnome applications come in one big package per language.

Holger

Thanks for the info about guile.  I reinstalled it.  Are you saying that I should leave the files and/or folders alone that have aisieriot and gnome-mahjongg in their names?

---

