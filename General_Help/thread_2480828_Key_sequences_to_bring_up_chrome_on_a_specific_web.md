---
title: "Key sequences to bring up chrome on a specific webpage"
date: 2022-11-11
forum: General Help
---

### Post by 7-vric-8 on 2022-11-11
I have one of those four button USB keypads and what I want to figure out is what key sequence I need to program into one of those keys it to bring up  a single instance of specific application (dictanote) to be the topmost window no matter what state the application is in (running, not running, on top of the window stack or somewhere else).

Dictanote is a speech recognition application works with Linux and to make my notetaking workflow smooth, bring it up with a single button is very important.

Thanks in advance for your help.

---

### Post by Holger_Gehrke on 2022-11-11
What version of Ubuntu, what Desktop Environment and which GUI base system (X11 or Wayland) ? 

If you're running on X11, then you can write a small shell script using wmctrl  from the package wmctrl to find a window with the right title and raise it to the top or start the program if no window was found. Then you can use xbindkeys (package xbindkeys) to bind that script to a key.

If you're using Wayland I don't know how to do it.

Holger

---

### Post by 7-vric-8 on 2022-11-11
You know, I have no idea which window system running. How can I tell?
I'm running Ubuntu at 22.04 stock

---

### Post by Holger_Gehrke on 2022-11-11
The command 'loginctl' can be used to get the type of session you're running. Run 'loginctl' with no additional parameters to get the id of the session (first column of the output) then run 'loginctl showsession id -p Type' (replacing 'id' with the actual id you got from the first command). Should output 'Type=x11' or 'Type=wayland'.

You can choose the kind of session you want to run with the cog-like icon on the login screen. Since I'm running XUbuntu 22.04 I'm not absolutely sure, but I think on stock Ubuntu the cog only becomes active after you've chosen a user.

Holger

---

