---
title: "Whats wrong with this syntax?"
date: 2012-11-30
forum: General Help
---

### Post by AsherSevyn on 2012-11-30
/usr/local/apache2/bin$ pwd /usr/local/apache2/bin

---

### Post by Tony Flury on 2012-11-30
> **AsherSevyn said:**
> /usr/local/apache2/bin$ pwd /usr/local/apache2/bin

The pwd command doesn't take a path as an argument :

[man pwd]("http://unixhelp.ed.ac.uk/CGI/man-cgi?pwd")

So it generates a syntax error when you provide a path.

---

### Post by zero2xiii on 2012-11-30
+1 for Tony Flury

Why do you wish to give an argument to pwd?

I assume you might want to change directory. TO do this use the cd (Change Directory, and some times, Current Directory) command followed by a path eg:
cd $HOME/Desktop

Cherz

---

### Post by lisati on 2012-11-30
> **zero2xiii said:**
> +1 for Tony Flury

Why do you wish to give an argument to pwd?

I assume you might want to change directory. TO do this use the cd (Change Directory, and some times, Current Directory) command followed by a path eg:
cd $HOME/Desktop

Cherz
+1 for this

"cd" is what I normally use to **c**hange **d**irectory. Although "pwd" *can* mean **p**resent **w**orking **d**irectory, I first read it as "password".

Please post back so we know if you're trying to set a password or wanting to navigate your file system.

---

