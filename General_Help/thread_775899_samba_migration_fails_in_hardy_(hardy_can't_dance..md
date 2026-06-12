---
title: "samba migration fails in hardy (hardy can't dance...)"
date: 2008-04-30
forum: General Help
---

### Post by elustran on 2008-04-30
I'm getting prompted for login, domain, and password, and I didn't used to.  The share I'm connecting to required no password.  When I leave the login fields blank, I get no love. I had some shares already written into fstab, and those don't connect either.

---

### Post by zeitgeist87 on 2008-07-17
I have the exact same problem. On Gutsy everything worked out of the box and I could simply access my windows shares. Now on hardy I get prompted for username, password and domain. I tried every possible combination and also changed my working group but it was no use.

Yesterday I managed to get nautilus to show the content of the share but it only worked for a few seconds and I couldn't access any files. Since then I was unable to recreate this behavior.

I hope there is a solution to this.

"smbclient //windowsbox/share" works perfectly in a console with a blank password but I can't get it to work in gnome.

Edit: I tried it the other way round and shared something on my Ubuntu hardy machine. It was visible on the windows machine but I couldn't access it. I also tried to access it localy:

smbclient //localhost/share
Password: 
Anonymous login successful
Domain=[HOME] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

---

