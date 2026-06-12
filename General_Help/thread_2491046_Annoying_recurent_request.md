---
title: "Annoying recurent request"
date: 2023-09-24
forum: General Help
---

### Post by guezuh2 on 2023-09-24
Request to input password it says: "Authentication needed
A program want to access the default password deposit 
but it is blocked."  I write the computer password but doesn't want it, it says is wrong.
What can I do to get rid of it?
It is in Spanish take a look its attached.
Thanks lots.

---

### Post by dragonfly41 on 2023-09-24
I don't speak Spanish but at a guess this might be related to AdBlocker (unblock this site)

[https://entreunosyceros.net/deposito-de-claves-inicio-sesion/](https://entreunosyceros.net/deposito-de-claves-inicio-sesion/)

or

[https://help.gnome.org/users/seahorse/stable/keyring-unlock.html.es](https://help.gnome.org/users/seahorse/stable/keyring-unlock.html.es)

I would not post my password into such an unknown popup.
You might do some detective work to see what process is attached to that popup window. Then delete the source app.

I use Stacer(GUI) to monitor and kill processes but here is a discussion on using CLI.
[https://discourse.ubuntu.com/t/viewing-and-monitoring-processes-in-linux/26024](https://discourse.ubuntu.com/t/viewing-and-monitoring-processes-in-linux/26024)

---

### Post by send2 on 2023-09-25
What program is it wanting for your to enter your password for? Are you trying to update your system? if so it needs your root password. If it is a program, what is the program and what where you doing when the message asking for your password came up? It looks like a particular application wants your password to access your password manager.

---

### Post by guezuh2 on 2023-09-25
If I put the root password it's rejected, so I have no idea what is it... no mention about the app or anything indicating where that comes from. Sorry.
Extrange isn't it?

---

### Post by guezuh2 on 2023-09-25
Thanx, I'm gonna have to learn a bit more to be able to do your recommendation.

---

### Post by dragonfly41 on 2023-09-26
When the popup window appears run this command in your terminal


```
ps ww -o ppid=,pid=,cmd= -q `xprop _NET_WM_PID | sed 's/_NET_WM_PID(CARDINAL) = //'`
```

Sourced from:   [https://kb.froglogic.com/misc/find-process-for-window/](https://kb.froglogic.com/misc/find-process-for-window/)


Then click on the popup window and process should be identified in terminal.

Incidentally I use Yakuake as a dropdown terminal which can be toggled. But your standard terminal is fine.

---

### Post by guezuh2 on 2023-09-26
Can't do it. When the thing appears locks the computer stays on top of the screen until I click on cancel or press the escape key.

---

### Post by dragonfly41 on 2023-09-26
O.K.
Try tips here to prevent the app window stealing focus ..

[https://askubuntu.com/questions/1084032/how-to-prevent-new-windows-from-stealing-focus](https://askubuntu.com/questions/1084032/how-to-prevent-new-windows-from-stealing-focus)

---

### Post by Shibblet on 2023-09-26
Is it just looking for a language package?  I find that happens after an update.  Language packs, for some reason, need a SU password.

---

### Post by guezuh2 on 2023-09-27
Did not work at all :(

---

### Post by guezuh2 on 2023-09-27
I don't think is a language package it says password deposit". What is a SU password? Any way...

---

### Post by guezuh2 on 2023-09-27
Thank you everybody I'm gonna live it like that. I think is a hacker so there is no fix. Good day.

---

### Post by guezuh2 on 2023-10-01
Look what I found this is the source of the request it's in files and I can't remove it as you can see the option "quitar" = remove is grayed off. [IMG]https://ubuntuforums.org/attachment.php?attachmentid=292814&stc=1[/IMG]

---

