---
title: "install konqueror in ubuntu?"
date: 2007-05-10
forum: General Help
---

### Post by waldorf on 2007-05-10
I use ubuntu and was thinking about giving konqueror a try for web browsing. When I went to install it in synaptic it looked like I had to install all sorts of other stuff. That made me nervous

Is it possible just to install konqueror in a very simple form for the sole purpose of web browsing?

If so, how? Aptitude?

Thanks in advance.

---

### Post by deanjm1963 on 2007-05-10
konqueror is not a standalone package, it needs quite a few kde libs as its a main part of the core of kde.

If you've got the diskspace install it with the needed libraries, it works fine under gnome and it's a great alternative to firefox or epiphany if you feel like a change.

---

### Post by strabes on 2007-05-10
Don't bother with konqueror for web browsing, especially if you're using ubuntu. It will take up lots of memory because you'll have to load tons of kdelibs to run it. There are many good browsers for gnome.

---

### Post by turbojugend_gr on 2007-05-10
If you want to try Konquerror you ll need to install all those dependancies. I would suggest you to install KDE if you have the space to try more of it in is native state. If you don't have the space then Epiphany is a good alternative to Firefox.

---

### Post by jerrylamos on 2007-05-10
If you want to run Konqueror then install Kubuntu.  It's all set up there.  Do note Konqueror does not do AOL Mail.

If you want to run Firefox then Ubuntu or Xubuntu is your choice.  Xubuntu isn't set up to browse a local LAN.

You can test all these out on CD Live first to see what you'd like to try.  If you want both Firefox and Konqueror, then install Kubuntu and add Firefox.  That's a lot smaller package than Ubuntu with Gnome desktop plus Konqueror which is dependent on the whole KDE desktop package.  You don't need two desktop packages eating up Linux resources.

Or else do as I do, this is a quad boot system, sometimes I have one or another installed in a different partition.  It's easy to copy files back and forth.

Cheers, Jerry

---

### Post by iLemon on 2008-01-02
Is there an easy option to install konqueror and its dependencies without installing KDE?  I like using it to browse samba shares but I am not really instrested in any of the other KDE programs.  Or the way it bloats my Applications menu.

---

### Post by jamaisvu on 2008-01-02
> **iLemon said:**
> Is there an easy option to install konqueror and its dependencies without installing KDE?  I like using it to browse samba shares but I am not really instrested in any of the other KDE programs.  Or the way it bloats my Applications menu.
[FONT=Franklin Gothic Medium]
No. Konqueror depends heavily on the core of KDE. It's what makes it so quick in KDE.

Oh, and there are things going for Konqueror in terms of browsing -- have a look at:
[http://www.webstandards.org/action/acid2/](http://www.webstandards.org/action/acid2/)[/FONT]

---

### Post by sumguy231 on 2008-01-02
Just installing Konqueror shouldn't install any of the KDE base applications with the exception of KDesktop, KFind, and KControl - KDesktop won't show up in the menu and the other two may or may not. If they do you can just remove them with the menu editor. 

Despite what everyone else is saying, the KDE library dependencies should only concern you if your computer is already noticeably inadequate. I'm not sure of the exact filesize, but I have a feeling if it's too much for you then you have larger problems.

Edit: Oh, and do an 'aptitude show konqueror' for a full list of the dependencies.

---

