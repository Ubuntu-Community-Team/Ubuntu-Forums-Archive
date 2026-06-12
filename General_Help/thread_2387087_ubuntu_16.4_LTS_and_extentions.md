---
title: "ubuntu 16.4 LTS and extentions"
date: 2018-03-14
forum: General Help
---

### Post by caterr on 2018-03-14
Hi

I am new to ubuntu @ gnome.
I installed Ubuntu 16.4 LTS. I wanted to install extensions.
I installed the package
**gnome-tweak-tool**
but when I open the window, the "extensions" bar does not appear
Also in:
~ /.local/share
I do not have a folder with the name
**gnome-shell**
that is :
```

~ / local / share / gnome-shell

```
does not exist

ps:  I uninstalled Firefox, and I use Firefox-**esr,** and I can not install the  extensions via firefox-**esr**, because of the version of that browser

[URL="https://postimg.org/image/yn48z3smj/"][IMG]https://s9.postimg.org/yn48z3smj/Captura_de_tela_de_2018-03-14_14-20-44.png[/IMG]


Thank you for any tip

[/URL]

---

### Post by deadflowr on 2018-03-14
What does
```
echo $XDG_CURRENT_DESKTOP
```
show?

---

### Post by caterr on 2018-03-14
> **deadflowr said:**
> What does
```
echo $XDG_CURRENT_DESKTOP
```
show?

Thank you for the replica 

```

~$ echo $XDG_CURRENT_DESKTOP
Unity

```

---

### Post by deadflowr on 2018-03-14
Makes sense.
You are not running gnome, so the option would not be there.

Since you installed gnome-tweak-tool, it should have added gnome-shell as an option you can log into when you login at the login screen.

If not, install gnome-shell.
```
sudo apt update
sudo apt install gnome-shell
```
then logout when that finishes. 

At the login screen in the box where you input your password, click on the icon that will show in the right corner.
You should have a couple of options, choose GNOME to run the gnome shell desktop.
Then simply login as usual.

After that, the extensions options will show.

---

### Post by caterr on 2018-03-14
> **deadflowr said:**
> Makes sense. You are not running gnome, so the option would not be there.  Since you installed gnome-tweak-tool, it should have added gnome-shell as an option you can log into when you login at the login screen.  If not, install gnome-shell. ```
sudo apt update sudo apt install gnome-shell
``` then logout when that finishes.   At the login screen in the box where you input your password, click on the icon that will show in the right corner. You should have a couple of options, choose GNOME to run the gnome shell desktop. Then simply login as usual.  After that, the extensions options will show.    Oh, now it solved and I understood a lot. Thanks very mate :))   Unity is a graphical interface linked to ubuntu, separate from the gnome.  but I have a problem that started to occur.   If I "log off", on the login screen I get black screen. I am forced to Ctrl + Alt + F1, and then reboot ...  Is this binding with gnome-shell package?    Please, is it better to open another topic with this question?

---

### Post by QIII on 2018-03-14
Yes.  Please start a new thread for this issue.

---

