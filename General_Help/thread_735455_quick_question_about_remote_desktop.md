---
title: "quick question about remote desktop"
date: 2008-03-25
forum: General Help
---

### Post by rabid9797 on 2008-03-25
i have used remote desktop before, but now I need to remove whatever underlying vnc program it is using. I recently installed tightvncserver so i can use it with java, but it tells me(whenever i try to initiate a server on :0 ) that there is already a server running there. I assume that this is the another server running for Remote Desktop. so how can i remove that one so i can use tightvncserver on :0 ?

---

### Post by rabid9797 on 2008-03-25
okay, well, i did some research on my own and found that gnome uses Vino as the remote desktop program. there is a vino-session running in proccesses and also in the session startup. i uninstalled vino and removed vino from the session but i still get the same error when starting up the server.

is it maybe talking about the x server? if so, how can i get around this?

EDIT: here is the error message

```

[rabid9797@rabid9797-laptop ~]$ vncserver -geometry 1024x768 -depth 24 :0

Warning: rabid9797-laptop:0 is taken because of /tmp/.X0-lock
Remove this file if there is no X server rabid9797-laptop:0
A VNC server is already running as :0
[rabid9797@rabid9797-laptop ~]$ 

```

---

### Post by HermanAB on 2008-03-25
Well, 'ps -e' will tell you what is running and if there is no VNC running, just delete that lock file.

---

### Post by rabid9797 on 2008-03-25
i didn't see any other instances of vnc of anything running(besides my tightserver), are you sure its okay to delete that file?

---

### Post by rabid9797 on 2008-03-26
well, i tried deleting the file, but then i just got another message about another locked file. really doubt that these are here just for redundant purposes in being safe, or that they were just left when i stopped vino.

can anybody help me out?

---

