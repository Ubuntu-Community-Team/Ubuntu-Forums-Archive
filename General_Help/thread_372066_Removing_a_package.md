---
title: "Removing a package"
date: 2007-02-27
forum: General Help
---

### Post by flummoxed on 2007-02-27
Hey yo,

I recently tried to install a .deb package from [www.getdeb.net](www.getdeb.net). During the install, it got messed up, I don't quite remember how. Anyways, now when I try to access apt-get or synaptic, it gives me an error telling me the package needs to be reinstalled, but I can't find an archive for it. When I try and reinstall it through double clicking the package and going through the process again, it doesn't work.

I tried removing the package, but it won't let me get that far, it only gives me that error message.

Any ideas for fixing this?

---

### Post by Maestro23 on 2007-02-27
You can try:

> sudo dpkg --purge packagename

---

### Post by taurus on 2007-02-27
Try

```
sudo dpkg -r **package_name**
```

---

### Post by flummoxed on 2007-02-27
Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

This is what I get when using either of those commands.

---

### Post by taurus on 2007-02-27
What is the name of that package?  And what is the exact error message when you run this command from a terminal?

```
sudo aptitude update
```

---

### Post by flummoxed on 2007-02-27
I don't get an error message running sudo aptitude update, and the package is brasero_0.5.1

---

### Post by taurus on 2007-02-27
What about

```
sudo aptitude upgrade
```

---

### Post by flummoxed on 2007-02-27
E: I wasn't able to locate a file for the brasero package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by taurus on 2007-02-27
Did you remember to run it with the sudo?

---

### Post by flummoxed on 2007-02-27
yes

---

### Post by flummoxed on 2007-02-27
I got a solution on the irc channel.

sudo dpkg --purge --force-remove-reinstreq brasero

did the trick

---

### Post by Maestro23 on 2007-02-27
> **flummoxed said:**
> I got a solution on the irc channel.

sudo dpkg --purge --force-remove-reinstreq brasero

did the trick

Good deal man.

---

### Post by bravemosquito on 2007-02-28
> **flummoxed said:**
> I got a solution on the irc channel.

sudo dpkg --purge --force-remove-reinstreq brasero

did the trick

Didn't work to me. I tested bnetd, after 2 days when tried to remove it Synaptic surprised me :) bnetd package still marked as [COLOR="SeaGreen"]installed[/COLOR]

---

