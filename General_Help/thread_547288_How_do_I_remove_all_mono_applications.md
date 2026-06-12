---
title: "How do I remove all mono applications?"
date: 2007-09-09
forum: General Help
---

### Post by fwilliams on 2007-09-09
Will someone please post away to remove all mono applications and any libraries or programs relating to mono.  If this can not be done, please recommend a distribution.  Thanks, it was a nice distribution until they started including that mono stuff without giving me a choice.

---

### Post by ryno519 on 2007-09-09
> **fwilliams said:**
> Will someone please post away to remove all mono applications and any libraries or programs relating to mono.  If this can not be done, please recommend a distribution.  Thanks, it was a nice distribution until they started including that mono stuff without giving me a choice.

```

sudo apt-get remove mono* libmono*
sudo apt-get autoremove

```

should take care of mono and all applications which depend on it.

May I ask why you want to remove it?

---

### Post by rsambuca on 2007-09-09
You can use the synaptic package manager and just remove mono-common, and it will automatically remove all the libraries and tomboy, etc.

I don't see what the big deal is, personally.

---

### Post by kerry_s on 2007-09-09
get a clue, you have always used mono whether you knew it or not. there are no distro's with out mono. gtk is mono.

---

### Post by fwilliams on 2007-09-09
Do not want it on my system.  Just a personal preference.  If the installer asked me up front weather I wanted to include these applications I would say no.  To me it smells to much like Microsoft.  I am sure many people would choose to install them, I just did not have a choice.

Thanks for the quick response to the thread.

---

### Post by fwilliams on 2007-09-09
Thanks.  I did not know the GTK was mono.  I am pretty new to Linux.

---

### Post by ryno519 on 2007-09-09
> **kerry_s said:**
> get a clue, you have always used mono whether you knew it or not. there are no distro's with out mono. gtk is mono.

Last I checked GTK was a graphical toolkit written in C with C/C++(gtkmm) bindings. Mono is a runtime environment and a code base which has wrappers for the Gtk toolkit. They are not one and the same. That is a gross misstatement. Gtk != Mono

---

### Post by kerry_s on 2007-09-09
> **ryno519 said:**
> Last I checked GTK was a graphical toolkit written in C with C/C++(gtkmm) bindings. Mono is a runtime environment and a code base which has wrappers for the Gtk toolkit. They are not one and the same. That is a gross misstatement. Gtk != Mono

[http://www.mono-project.com/FAQ:_General](http://www.mono-project.com/FAQ:_General)

---

### Post by ryno519 on 2007-09-09
> **kerry_s said:**
> [http://www.mono-project.com/FAQ:_General](http://www.mono-project.com/FAQ:_General)

And? I don't seem to see the "Gtk is Mono" section.

---

### Post by kerry_s on 2007-09-09
> **ryno519 said:**
> And? I don't seem to see the "Gtk is Mono" section.

okay so i said it wrong, shoot me. gtk is tied to mono which intern is a part of gnome. anyways the point is mono is going to be a big part of everything, there is no way to avoid it, it is open source.

---

### Post by ryno519 on 2007-09-09
> **kerry_s said:**
> okay so i said it wrong, shoot me. gtk is tied to mono which intern is a part of gnome. anyways the point is mono is going to be a big part of everything, there is no way to avoid it, it is open source.

*bang*

Gtk+ isn't tied to mono at all.

---

