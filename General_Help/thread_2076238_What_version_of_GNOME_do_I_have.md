---
title: "What version of GNOME do I have?"
date: 2012-10-25
forum: General Help
---

### Post by oxf on 2012-10-25
Hi,

I installed Precise and then changed it from Unity to Gnome but am confused as to which version of GNOME I have now. Is there a simple terminal command that tells me what I'm running.

Also I am completely confused between GNOME classic, shell, fallback etc. Are these Gnome 2, 3 or what? Could someone please clarify

Thanks

---

### Post by danielbauwens on 2012-10-25
Yes, just type:

```
gnome-session --version
```

And Gnome shell is to get your old looks back (bottom bar etc..)

---

### Post by oxf on 2012-10-25
> **danielbauwens said:**
> Yes, just type:

```
gnome-session --version
```And Gnome shell is to get your old looks back (bottom bar etc..)

Thanks! :)
Veronica

---

### Post by wheeze on 2012-10-25
> **oxf said:**
> Also I am completely confused between GNOME classic, shell, fallback etc. Are these Gnome 2, 3 or what? Could someone please clarify

Those are all GNOME 3. GNOME 3 is really the underlying libraries and applications that the interfaces, also called the Desktop Environment (DE) use.

GNOME Shell is the newest interface, it does not replicate the old GNOME experience. It's the E that most people complained about when GNOME 3 first hit the market, and is usually mistakenly called GNOME 3.

GNOME Classic most closely resembles the old environment but with subtle differences. GNOME Classic, fallback and GNOME Panel are all names for this environment, leading to much confusion.

---

### Post by oxf on 2012-10-26
> **wheeze said:**
> Those are all GNOME 3. GNOME 3 is really the underlying libraries and applications that the interfaces, also called the Desktop Environment (DE) use.

GNOME Shell is the newest interface, it does not replicate the old GNOME experience. It's the E that most people complained about when GNOME 3 first hit the market, and is usually mistakenly called GNOME 3.

GNOME Classic most closely resembles the old environment but with subtle differences. GNOME Classic, fallback and GNOME Panel are all names for this environment, leading to much confusion.

Thanks, thats helpful :)

---

### Post by danielbauwens on 2012-10-26
Downloading GNOME shell on Ubuntu Software Center gives you the ability to choose Gnome Classic as interface in the login screen.

---

