---
title: "vcn viewer?"
date: 2005-03-24
forum: General Help
---

### Post by lgb on 2005-03-24
Can anyone point me in the right direction to get this to work. I see the file in /usr/bin but I don't know the command for it. I've tried clicking on it and a dialog box opens to type the IP address but after entering it the box just closes.

---

### Post by Arto on 2005-03-24
I assume you mean /usr/bin/vncviewer? Try running it from a terminal (command line) window to see what goes wrong. Most likely you need to tell it also which display to connect to, so instead of e.g. the IP 10.0.0.1 you would enter 10.0.0.1:0, where :0 is the the display number (can be :1, :2, and so on).

You can get help for the program by typing "man vncviewer" on the command line.

---

### Post by lgb on 2005-03-24
I can't even open it from command and when I try "man vcnviewer" it say's there is none. The vcn viewer file is actually a shortcut to xrealvcnviewer. I've never had to enter anything other than a password in the past when using it under windows. I have a FC3 machine that I just need to enter the IP and password. I'm a noob and I'm at a loss...  :mrgreen:  Thanks!

---

### Post by ubuntu_demon on 2005-03-24
I always use "terminal server client" for viewing vnc (I think it uses vncviewer or something).... .. it's right in the internet menu.

---

### Post by lgb on 2005-03-24
[QUOTE=demon666_nl]I always use "terminal server client" for viewing vnc (I think it uses vncviewer or something).... .. it's right in the internet menu.[/QUOTE]

That's the ticket!  Thank you!

---

### Post by techmonkey on 2005-03-24
[QUOTE=lgb]I can't even open it from command and when I try "man vcnviewer" it say's there is none.[/QUOTE]

That's because it's *vnc*viewer. ;) It stands for Virtual Network Computing; Not Virtual Computing Network. :)

---

### Post by lgb on 2005-03-24
[QUOTE=techmonkey]That's because it's *vnc*viewer. ;) It stands for Virtual Network Computing; Not Virtual Computing Network. :)[/QUOTE]


  :oops: That makes a BIG difference.  :D

---

