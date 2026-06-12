---
title: "ssh display question"
date: 2008-01-09
forum: General Help
---

### Post by chopsticks on 2008-01-09
When I use 
ssh -X servername
I can open a X window at the client end. 
But if I have already logged to the server by typing 
ssh servername
Then how could I open the window at the client end?

Thanks!

---

### Post by geirha on 2008-01-09
As far as I know, you can't add X11 forwarding to a connection allready established. You can make X11 forwarding default though, by editing /etc/ssh/ssh_config on the client. Then you don't need to specify the -X.

---

