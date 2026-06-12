---
title: "TightVNC over SSH: &quot;Server did not offer supported security type!&quot;"
date: 2008-04-28
forum: General Help
---

### Post by oldweasel on 2008-04-28
I am attempting to connect from an XP machine to my Ubuntu box (Hardy Heron)over a SSH connection using TightVNC. 

I have a SSH tunnel with port 5900 forwarded, and the TightVNC viewer connects to the Ubuntu box and attempts to negotiate protocols, then I receivethe error message "Server did not offer supported security type!". 

Any ideas on how to resolve this issue?

---

### Post by dli8ilb on 2008-06-18
bump.  i am having the same issue as you only without an SSH tunnel on parsix linux.  funny thing is, a google search for the error message offered this page as the only relevant result... ???

anyhow, one way way to connect is with both encryption and password disabled, which is not a very good idea. 

using only a password (no encryption) and i get "Authentication failure": 

```
Connected to 192.168.1.65 port 5900
RFB server supports protocol version 3.7
Connected to RFB server, using protocol version 3.7
Authentication scheme: (null)
Authentication failure
```

using tightvnc-1.3.9

any other ideas??

---

### Post by dli8ilb on 2008-06-18
okay, got it working with a password by using gconf-editor.
navigate to Desktop >> Remote Access >> VNC Password 
it's Base-64 so you will have to [encode your password]("http://www.javazoom.net/services/base64/base64.jsp"). 

still no word on the encryption issue though.

---

### Post by westy79 on 2008-09-19
bump.

I am having the EXACT same issue as oldweasel and there doesn't seem to be a resolution for this. I have done a lot of searching and still haven't come across an answer.

Anyone have some fresh ideas?

---

### Post by mreyeros on 2008-09-24
I was havingthe same issue and resolved it by removing the "Require Encryption" option in the advanced tab of the Remote Desktop Preferences window

Hope this helps

---

### Post by jakarrasko on 2009-01-26
Whith TightVNC from Vista (viewer) to Ubuntu (server)...now working ;D

Go to "Main Menu (System)>Preferences>Remote Desktop" and ONLY check these options:

- "Allow other users to view your desktop"
- "Allow other users to control your desktop"

Don't forget to set a password !!

Thanks to **mreyeros** ;)
[COLOR="DarkGreen"]
From Extremadura (Spain)[/COLOR]

---

