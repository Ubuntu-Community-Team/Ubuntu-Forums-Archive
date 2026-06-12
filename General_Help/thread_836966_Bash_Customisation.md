---
title: "Bash Customisation"
date: 2008-06-22
forum: General Help
---

### Post by Nullack on 2008-06-22
So with all this compiz stuff, I want to tweak out my BASH sessions :)

Currently Im using this, you can try it in a BASH terminal session by using the following commans

```
export PS1='${debian_chroot:+($debian_chroot)}|\[\033[00;34m\]\u\[\033[00m\]\[^\]\[\033[00;34m\]\h\[\033[00m\]\[\033[00m\]:\[\033[00;33m\]\W\[\033[00m\]|\[\033[00;36m\]\$\[\033[00m\] '
```

NOTE: This change is not permanent. You need to edit your bash startup script to make it stick.

Also another tweak I'm using is better colours in man pages. To do this install most

```
sudo apt-get install most
```

Then activate the coloured man page by the following command in your bash terminal:

```
export PAGER="most"
```

Now you have IMHO a much better man page layout. Try it with say:

```
man sudo
```

Whos got some cool ps1's? Or other nice stuff? Lets get this rolling :KS

---

### Post by King_Critter on 2008-06-22
Perhaps I'm just paranoid, but that looks suspiciously close to the disguised "sudo rm -rf /" that were popping up a while ago. :-/ 

What's the command do?

---

### Post by Nullack on 2008-06-22
Its good to be paranoid :)

Just run it in a BASH terminal as a low privileged user.

What it does is change the look of the BASH prompt and file listings.

Its not permanent, to make it permanent you have to edit the BASH config file.

---

