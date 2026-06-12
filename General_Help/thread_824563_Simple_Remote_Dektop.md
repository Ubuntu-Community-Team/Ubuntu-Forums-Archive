---
title: "Simple Remote Dektop?"
date: 2008-06-10
forum: General Help
---

### Post by stanger192 on 2008-06-10
Hey all

Ive just set up ubuntu server edition on a old pc to use as a samba file server/utorrent box, and i would like to set up remote desktop on this machine, as the server will run without a monitor. The problem i have is that all the "how-tos" i have found on the net seem like overkill for what i want (i dont need remote login as the server is set to autologin or resumeable sessions)
Basically all i want is to be able to view and use the server desktop(xdm and fluxbox)that is running on the server in a window on my ubuntu desktop.

So can anyone help me acheive this?

---

### Post by itix on 2008-06-11
I can only be of help if you have another ubuntu machine.

Use the "terminal server client" found under *apps. => internet => terminal server client*

just enter the ip assigned by your router in the "computer" field and enter the user name of the user on the server in the "user name" field and that users password in the password field. 

I tried reaching my eeepc from my other linux machine to make sure it worked doing this but it just fails me. I am however sure that this is what you are looking for.
If you are well educated in the networks area, you might have better luck than me.

---

