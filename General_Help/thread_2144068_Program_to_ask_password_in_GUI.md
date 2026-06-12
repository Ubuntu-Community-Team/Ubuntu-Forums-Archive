---
title: "Program to ask password in GUI?"
date: 2013-05-11
forum: General Help
---

### Post by Marcelo Ruiz on 2013-05-11
Hi All!

I am trying to use the sudo command with the -A option (I can't use the gksudo command for what I need). ](*,)
My problem is that I don't know how to set the ask password program nor know any of them. I spent a great deal of time searching for the solution online with no luck. :confused:
Does anyone know which program to use? I would like to know the name of the program that displays the GUI and require the user password when I execute "gksudo".
Thanks!

---

### Post by JRV on 2013-05-11
Use alacarte (Main Menu) to create a .desktop file (launcher) and start the command line with gksudo.

Your new .desktop file will be in /home/USER/.local/share/applications.

---

### Post by Marcelo Ruiz on 2013-05-11
Hi JRV, thanks for the suggestion. In this particular case it doesn't work because I am calling a script that needs to mount a network share, so I think I am forced to use the "sudo" command instead of "gksudo".

---

