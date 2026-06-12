---
title: "Nautilus - Please help!"
date: 2006-08-28
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-08-28
When I start nautilus, it crashes, then reopens, etc. So I run it from the terminal, and I get: 

```
giga@ubuntuzilla:~$ nautilus
Segemntation fault
giga@ubuntuzilla:~$
```

Please help! Is there a way I can reconfigure nautilus? Or diagnose the problem?

---

### Post by Rui Pais on 2006-08-28
hi,
did nautilus work as another user or with admin powers?
try to launch it with
```
gksudo nautilus
```
same problem?

to check if nautilus is broken or is just a borked configuration maybe delete (or move to another place) the folder .nautilus...
Close any session
login from the console (ctrl+F1)
rm -rf ~/.nautilus
login from gdm and see if it's ok.

hope that helps

---

### Post by s_h_a_d_o_w_s on 2006-08-28
gksudo seemed to work, until I plugged in my sony psp. It closed, and opened,but not with sudo. i get this output:

giga@ubuntuzilla:~$ gksudo nautilus
(nautilus:28118): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


i'll try the other thing you mentioned

---

### Post by s_h_a_d_o_w_s on 2006-08-28
did the second thing. here's what I get after:

 nautilus

** (nautilus:29163): WARNING **: Can not caclulate _NET_NUMBER_OF_DESKTOPS

** (nautilus:29163): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:29163): WARNING **: Can not get _NET_WORKAREA

** (nautilus:29163): WARNING **: Can not determine workarea, guessing at layout
Segmentation fault

How can I fix this?

---

### Post by Rui Pais on 2006-08-28
uhmmm... seems something is broken. 

Can you start other graphical apps like gnome-terminal, synaptic, etc.? 
And did your desktop is rendered as usual (with background, menus and icons)?

BTW, have you tried to remove and reinstall nautilus again?

---

### Post by s_h_a_d_o_w_s on 2006-08-28
Thanks for responing so fast!

terminal works fine
ni icons or anything for my desktop
i have dona a apt-get remove then install nautilus, still doesn't work

---

### Post by Rui Pais on 2006-08-28
> **s_h_a_d_o_w_s said:**
> Thanks for responing so fast!
No problem... (not much a help yet, sorry :()

> i have dona a apt-get remove then install nautilus, still doesn't work
that's bad... lets hope its just a config problem.

Do you mind to redo the logout/login in a console again and do:
```
mkdir tmp_gnome_config
mv ~/.gnome* tmp_gnome_config/
```
and then login again from GDM.

---

### Post by s_h_a_d_o_w_s on 2006-08-28
let me just make sure i am righht. When you say console window, you mean logout, then log-in, but as a session, to choose failsafe terminal?

I trie the reinstall again, didn't work. 

If i could find out where nautilus is reading it's workarea info, maybe it wouyld work. I'll try the method you described.

---

### Post by Rui Pais on 2006-08-28
> **s_h_a_d_o_w_s said:**
> let me just make sure i am righht. When you say console window, you mean logout, then log-in, but as a session, to choose failsafe terminal?

Sorry, i mean close gdm session and login using ctrl+F1 (or F2, F3,...)
to make sure your old gnome configs are moved away before new login.

---

### Post by s_h_a_d_o_w_s on 2006-08-28
How do i do that? Sry, i'm only 13, but I am learning and loving ubuntu!

---

### Post by Rui Pais on 2006-08-28
> **s_h_a_d_o_w_s said:**
> How do i do that? Sry, i'm only 13, but I am learning and loving ubuntu!

close gnome (if there isn't a close button or an exit press CTRL+ALT+Backspace)
when you get gdm login screen press CTRL+F1
login there and type
```
mkdir tmp_gnome_config
mv ~/.gnome* tmp_gnome_config/
mv ~/.nautilus* tmp_gnome_config/
```
then login again using gdm (usually at CTRL+F7)

It should start a gnome session with a fresh configuration.



13 kids are such a lucky ones this days!! 
When i was 15 i learned basic with a new ZXSpectrum :cool:  
No apt for install apps just a tape recorder :???: 
(I still have nightmares with the tape recorder!)

---

### Post by s_h_a_d_o_w_s on 2006-08-28
I vcan't get to it. I kill X with ctrl alt bkspc, and I go to a terminal for 2 secs, then the gdm greeter loads. Msybe there is a way to delete all nautilus info and data? Or maybe a substitute to nautilus?

---

### Post by Rui Pais on 2006-08-28
> **s_h_a_d_o_w_s said:**
> I vcan't get to it. I kill X with ctrl alt bkspc, and I go to a terminal for 2 secs, then the gdm greeter loads.
Give it time. Wait till gdm greeter loads and *then* press CTRL+F1.

---

### Post by skymt on 2006-08-28
> **Rui Pais said:**
> Give it time. Wait till gdm greeter loads and *then* press CTRL+F1.

CTRL+ALT+F1. CTRL+F1 doesn't work, at least for me, and I haven't changed it.

---

### Post by Rui Pais on 2006-08-29
> **skymt said:**
> CTRL+ALT+F1. CTRL+F1 doesn't work, at least for me, and I haven't changed it.

yes, sorry, CTRL+ALT+F1. It was too late, i was tired and don't think much about it.

ALT+F1, F2,... works when change from console to console, not from graphical one to a text console.

Thanks for the correction.

---

