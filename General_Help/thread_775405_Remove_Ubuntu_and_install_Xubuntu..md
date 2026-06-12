---
title: "Remove Ubuntu and install Xubuntu."
date: 2008-04-30
forum: General Help
---

### Post by mc2000 on 2008-04-30
I'm dual booting Vista/Ubuntu. I didn't use Wubi. Everything is great but I want to uninstall Ubuntu and try Xubuntu now. How should I do it? Any tips would be greatly appreciated, thanks.

---

### Post by laborg on 2008-04-30
Just install Xubuntu with

```
sudo apt-get install xubuntu-desktop
sudo apt-get remove ubuntu-desktop
```

when logging choose xfce, voilá xubuntu!

---

### Post by kesman on 2008-04-30
This doesn't give you all the applications that a fresh xubuntu install would give. Running:
```

sudo aptitude install xubuntu-desktop

```
will install MUCH more stuff.

---

### Post by ryanhaigh on 2008-04-30
```
sudo apt-get remove ubuntu-desktop
``` 
This won't remove gnome and all the other dependancies, you will still have the whole system minus one metapackage. If you want to completely remove ubuntu it is probably easier just to install using the cd over the top of the current install.

---

### Post by laborg on 2008-04-30
so
```
sudo aptitude install xubuntu-desktop
```
will install much more stuff than
```
sudo apt-get install xubuntu-desktop
```
?

sure ?

---

### Post by mc2000 on 2008-04-30
I tried sudo apt-get install xubuntu-desktop but after restart I couldn't access it.

---

### Post by angry_johnnie on 2008-04-30
You know, you don't really need to remove ubuntu in order to try xubuntu.
Just install it, and you will be able to choose an XFCE session when you log in.

The difference between apt-get and aptitude is not the number of packages that get installed.  It's just that aptitude is better at keeping track of things.  Should you ever feel like removing XFCE, you would just have to **sudo aptitude remove xubuntu-desktop**.  If you used apt-get instead of aptitude, you would have to **sudo apt-get remove --purge every single package that got installed**.

Aptitude just makes it easier.

---

### Post by ryanhaigh on 2008-04-30
When you login/at the login screen look for a button on the bottom left that says options, go to select session and select xfce (or xubuntu not sure what it puts there).

---

