---
title: "Looking for an app... [Resolved]"
date: 2006-12-20
forum: General Help
---

### Post by indigoshift on 2006-12-20
Hi --

Back in my Amiga days, I downloaded a handy little app called "openwin" off of Aminet.  This program allowed you to open a window to anywhere, via the CLI.  It was extremely handy.  If you were in the CLI and needed to see a window of the current directory, you simply typed in "openwin" and pop!  There was your window, showing you the pwd you were looking at in the CLI.

You could also specify a pathname.  So, if you were in the Work:blah/mystuff directory, but needed to instantly open a window showing your Preferences, you could type in "openwin system: prefs" and pop!  Preferences window.

I was wondering if there was any sort of Ubuntu analog to this cool little program?  If not, I suppose I should start coding one, but I thought I'd ask first, so as not to reinvent the wheel.

---

### Post by aysiu on 2006-12-20
I don't know how to get it to open the directory you're currently in, but I believe all file managers can open specified directories from the terminal. Here's an example using Konqueror to open /usr/share/icons.

---

### Post by deadlydeathcone on 2006-12-21
Yes, there certainly is!

In Bash either "." or "$PWD" can be used to represent the current directory, so for example in gnome you could open the working directory be typing "nautilus %PWD", or better, "gnome-open ." (without the quotes, of course).

"gnome-open" is especially handy as you can feed it any sort of file type (MIME type, really) and it will open it with the default set in GNOME, so "gnome-open /usr/share/penguins.txt" will open it up with gedit. If you also use bash aliases and the nautilus-open-terminal extension it makes the whole process, to put it badly, a thing of terrible, geeky beauty!

Here are the very simple aliases that I use:

```
alias g='gnome-open'
alias sg='sudo gnome-open'
alias naut='gnome-open .'
alias snaut='sudo gnome-open .'
```

---

### Post by indigoshift on 2006-12-21
*edits .bashrc*

Openwin is back!  ;) 

Who knew it was built-in*?  Thanks!

This OS gets cooler every day, I swear.



*er, besides you guys, I mean... :D

---

