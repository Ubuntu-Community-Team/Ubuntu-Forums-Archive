---
title: "[SOLVED] How do I install compiz fusion and Beryl?"
date: 2008-05-25
forum: General Help
---

### Post by Hyper Tails on 2008-05-25
Hello I new here And I saw videos on youtube on compiz-fusion and beryl so i tried out ubuntu 7.10 in virtual box and I think it a good os and easy to use.
last night at midnight I decided to use wubi to dual boot my laptop to ubuntu 8.04 and windows vista homepreduim and I enabled desktop effects and I wanted to install compiz fusion and beryl and it seems you have you use that command thing (like MS-DOS) And I don't know how :confused:

Any help will be accepted because I really really want to do this
if you know please reply

---

### Post by mano cazalet on 2008-05-25
you can use synaptic to before getting used to the terminal ;)

open it in system/administration

and search for:
compizconfig-settings-manager
emerald
fusion-icon

install these 3 packages

just to show you there is no reason to panic, in terminal this should look like this:

```
sudo apt-get install compizconfig-settings-manager emerald fusion-icon
```

one line instead of 3x clicks + 3searches plus confirmations

after this there will be a Advanced Desktop Effects and an Emerald entry in system/preferences menu, use emerald to adjust your window borders and the desktop effect for the cube and stuff. remember to change your horizontal virtual size under general options/desktop size settings to 4 and enable window decoration plugin

---

### Post by SkonesMickLoud on 2008-05-25
> **Hyper Tails said:**
> so i tried out ubuntu 7.10 in virtual box

Just know that most people have issues getting Compiz running even though they have Ubuntu installed on their system, so don't get too frustrated if it's tough to do on a virtual box.

---

### Post by Forlong on 2008-05-26
It's not possible to run Compiz at all on Virtual Box atm.

---

### Post by _DD_ on 2008-05-26
First of all (if you have an nvidia or ATI card) you should go and enable the proprietary drivers in the restricted drivers manager.

Then you can go enable desktop effects (in 8.04 its in the same settings window as setting your wallpaper).

Finally, so you can configure the effects you want, you need to install the settings manager...

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Forlong on 2008-05-26
I'm sorry... I missed that Hyper Tails actually did install Ubuntu.

Please post the output of ```
compiz
``` then. It's not necessary to install anything. Compiz Fusion is installed by default.

---

### Post by Hyper Tails on 2008-05-26
THANKS!!!111!!! for the help
up and running

But I have bad news:
I decided to enable this and that I like to enable When I click on ANY open windows I click on ANY spot EVEN a button AND it thinks I`m acullaly dragging it.
So i can`t click anywhere on the window (can`t even right click on the desktop) When i click none it works but i want to have effects to work with my laptop at school when i`m taking notes in class( i think my ubuntu os is best to take notes in class and i think my vista part is best for other things such as programing robots)
If you a solution please reply
And again thanks for the help with the installion

---

### Post by Forlong on 2008-05-27
Sounds like a setup issue.
Try resetting all Compiz settings:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by Hyper Tails on 2008-05-27
Problem solved:smile:
I got the animations working and i got the desktop cube and that so thanks for the help!!

Many thanks!!!111!!!!

---

