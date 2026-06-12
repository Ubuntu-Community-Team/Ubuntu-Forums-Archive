---
title: "Eterm colours"
date: 2008-05-26
forum: General Help
---

### Post by Voorhees1979 on 2008-05-26
Hi Everyone

First I will show a picture so you can see what I am about to say:

[http://img408.imageshack.us/my.php?image=screenshotsr8.png](http://img408.imageshack.us/my.php?image=screenshotsr8.png)

Basically this is the last tweek to my desktop, pretty much have it how I want with Eterm kind of embedded. The problem is, is when i type "ls" to list my drives contents all of the folders are shown in blue or other colours. This is the same in the standard terminal.

Can anyone help me getting all listing text to a different colour, grey or red. I can change the terminal font colour but not the listing colours. Blue folder listing on a blue wallpaper is a nightmare to read :(

Many Thanks for any help

---

### Post by dizee on 2008-05-26
Hi

Try editing ```
alias ls="ls --color=auto"
``` in the file .bashrc in your home directory, replacing "auto" with a colour of your choice.

---

### Post by Voorhees1979 on 2008-05-27
Hi 

Thanks for the reply. That works fine with the normal terminal but not with Eterm.

I have found to get the listing the same colour as the font selected is to type "ls -s"

Thats is the only way I have found to do it.

Cheers

---

