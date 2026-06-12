---
title: "Moving from WinXP"
date: 2008-02-09
forum: General Help
---

### Post by fortune82 on 2008-02-09
I was searching around for the coolest looking and most useful theme for Ubuntu (Is theme the right word?) and I came across Beryl. I learned that Beryl was pretty much replaced by Compiz and Compiz Fusion.

What I'm trying to get at is, is this true? How would I install these to Ubuntu? Anything special I need to do? And would I be able to streamline the Ubuntu installation to automatically install Compiz/Compiz Fusion?

---

### Post by fourthofjuly on 2008-02-09
> **fortune82 said:**
> I was searching around for the coolest looking and most useful theme for Ubuntu (Is theme the right word?) and I came across Beryl. I learned that Beryl was pretty much replaced by Compiz and Compiz Fusion.

What I'm trying to get at is, is this true? How would I install these to Ubuntu? Anything special I need to do? And would I be able to streamline the Ubuntu installation to automatically install Compiz/Compiz Fusion?

Go to Applications > Add/Remove... > Select Other > Advance Desktop Effects Settings...

Ubuntu will install it for you...

---

### Post by jan quark on 2008-02-09
the newest ubuntu version 7.10 hast compiz pre-installed

so you need to activate your graphic card using the proper drivers

download the compizconfig-settings-manager to set up the effects you wish to run and that's it when everything works flawlessly

what is your graphic card?

---

### Post by AsoSako on 2008-02-09
Sorry for double post.  Please refer to my next reply...

---

### Post by AsoSako on 2008-02-09
Yes Compiz-Fusion is a merge between the Compiz and Beryl Projects.  If you are using 7.10 Compiz-Fusion is already installed and all you need to get from Synaptic in order to configure it is compizconfig-settings-manager.
Yes you would need to activate your graphics card, and maybe you should go to System > Preferences > Appearance > Visual Effects > and click on custom after installing the  compizconfig-settings-manager.

---

### Post by macogw on 2008-02-09
Ubuntu 7.10 (Gutsy, the latest release) comes with Compiz Fusion.  Just install compizconfig-settings-manager from Synaptic (System -> Administration -> Synaptic....checkboxes....autodownloads whatever you want) to get more customizability than the default install.


Beryl & Compiz are window managers.  They handle *just* how to do draw windows, where they are placed, etc.  Beryl & Compiz are different from other window managers (like Fluxbox, IceWM, Metacity, KWin, etc) in that they have a separate program drawing the window borders/titlebars.  Beryl & Compiz let you pick between Emerald or GTK Window Decorator. Emerald can do transparent borders.  GTK Window Decorator uses Metacity themes, which is kind of neat.  Metacity is Ubuntu's default window manager because Ubuntu uses GNOME as the desktop environment (a set of programs, common libraries, and configuration utilities that all "fit" together), and GNOME's default is Metacity.  Kubuntu uses KDE as the desktop environment (so it has a different look and different programs by default), and it's default window manager is KWin.  Fluxbox and IceWM (that I mentioned earlier) are standalone window managers.  They don't need to live inside a desktop environment, but that means you can do a very minimalist system with them (which is why I'm using Fluxbox right now).

---

### Post by fortune82 on 2008-02-09
i have an ATI X1900GT
AMD64 3500+
1GB of RAM

pretty much middle-of-the-road

EDIT: i was also thinking of installing gOS instead of Ubuntu. dos anyone have experience with gOS?

---

### Post by Ghuloomo on 2008-02-09
I have downloaded that compizconfig-settings-manager but when i click on custom an error window appears saying: "The Composite extension is not available" Even for the Normal and Extra options.

I have enabled my driver through Restriced Driver Manager, and i guess it's working fine. I can play videos, and the screensavers are working fine.

Is there something I need to do?

I'm using ATI 9600 128MB

---

