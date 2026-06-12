---
title: "Remote Desktop"
date: 2008-05-23
forum: General Help
---

### Post by Sevets on 2008-05-23
I am attempting to set up a machine with Ubuntu and am having trouble finding resources about how to Remote Desktop (VNC or other) without having to login in locally first.  

The preferable method would be VNC as the users will be the most familiar with it and not have to download anything else.

Everything I have seen uses SSH tunneling and X forwarding, but I would really like (need) to use VNC without the local login.

It should work similarly to how windows clients can remote desktop into a box without someone having already logged in.

THANKS!

---

### Post by LinuxTechnology on 2008-05-23
I suggest that you type in the following command in the Terminal, under Applications>Accessories>Terminal.

[INDENT]rdesktop " "[/INDENT]

Where the parentheses indicate the IP Address for the computer (without the quotes, of course).

Hope this helps.

---

### Post by Sevets on 2008-05-23
I think I need to clarify a bit more.

I hope to be able to do this with windows clients.  

I am not even sure what configs to start looking for this or might it be a separate program or extension that could add this?

---

### Post by HermanAB on 2008-05-23
Two problems:
1. VNC doesn't work the same way as Windows RDP.  You have to log in first, then run the server.  
2. VNC is insecure.

The solution is to use SSH.  It can do everything VNC does, only better and securely.

There are various SSH clients and X servers available for Windows users.  The best known is Xming and PuTTY.

Cheers,

Herman

---

### Post by Sevets on 2008-05-23
I am able to SSH into the SSH server before a local login... I realize that SSH is more secure and everything, but I feel that I should be able to do the same with VNC.

I would be fine with workarounds or even just using the CLI if it was just for me but this needs to be graphical in nature for other Users. 

I understand the insecure nature of VNC with the sending of cleartext passwords and such, but we are using this in a secure environment.

Also I found System>Administration>Login Window in the remote tab and enabled the remote login but it doesn't seem to change anything for me?

---

