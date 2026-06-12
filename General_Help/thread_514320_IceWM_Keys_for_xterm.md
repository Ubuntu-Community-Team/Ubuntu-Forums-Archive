---
title: "IceWM Keys for xterm"
date: 2007-07-31
forum: General Help
---

### Post by mr4thjuly on 2007-07-31
I am not sure where to post this but here goes anyways.
I am trying to customize the Ctrl+Esc combination to open up the xterm window managed by IceWM. Please note I do not use IceWM for any other purpose but this. There is no GUI for me to use that will let me customize the Ctrl-ESC combo. Currently my xterm window opens as a user with almost root privileges . Is there a way to customize the key combination mentioned to prompt the user for his password when IceWm opens the xterm on pressing Ctrl-Esc.
Any help would be greatly appreciated.

---

### Post by aysiu on 2007-07-31
What do you mean by *almost root privileges*? You'll be prompted for your password if you enter a command with *sudo* in front of it, but you otherwise do not have anything remotely resembling root privileges.

---

### Post by kerry_s on 2007-07-31
xedit ~/.icewm/keys

key "Ctrl+Escape" xterm
or
key "Ctrl+ESC" xterm

if in doubt use xev to check what the key pressed is, i've seen some were "Ctrl" is "Control_L".

---

### Post by mr4thjuly on 2007-08-01
Kerry I already tried that. What I really want is for my xterm window to prompt me for my password when I hit Ctrl+esc and stay open. Oh and by the way neither "Ctrl+Escape" or "Ctrl+ESC" work at all. Is there a way to disable the Ctrl+ESC sequence since pressing those keys actually shows a menu in IceWM that I do not wish to see at all.  All I am trying to do is give purely xterm access to the people using my computer and have the xterm prompt them for a password without closing the window once the password is entered (There is only one account but a password is required). I also tried xev but it shows up as "Escape" so thats what I tried but it does not work at all. Any other suggestions?  
I really appreciate your help Kerry.

---

