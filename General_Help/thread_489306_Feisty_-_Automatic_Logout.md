---
title: "Feisty - Automatic Logout"
date: 2007-07-01
forum: General Help
---

### Post by Houlala on 2007-07-01
Hi all,

I want to know if Feisty have an Automatic Logout option. In the System Menu, when you click on "Quit", a screen appears with several option (Logout, Halt, Reboot)...

Is there an option to tell to logout automaticly and dont ask what to do (like before) ?

Thanks
Cya

---

### Post by bigken on 2007-07-01
yes just right click the button

---

### Post by Houlala on 2007-07-01
Hu !? It doesn't work... 
When I right click on the "System > Quit", the screen appears again ^^

An other solution ? :/

---

### Post by DagMan on 2007-07-01
gconf-editor

and 
/apps/gnome-session/option

or thereabouts, if the option is still available in there.  I didn't test what the settings did and it was obscure.

---

### Post by Houlala on 2007-07-01
Oh ! Marvellous !!
Thanks DagMan !

So, I did : 
- Launch gconf-editor
- go in /apps/gnome-session/options
- untick the "logout_prompt"
- edit the value "logout_option" (change "Logout" to "logout")

It's done ^^
Thanks for your help !

---

