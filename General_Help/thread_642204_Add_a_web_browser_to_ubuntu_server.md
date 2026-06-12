---
title: "Add a web browser to ubuntu server?"
date: 2007-12-16
forum: General Help
---

### Post by leonv12 on 2007-12-16
I am running ubuuntu server as a backup (with rsync) for several clients.  I chose server because I wanted to keep the clients completely out of the box. 

I now wish I could access a web browser from the boxes to look at things like up and down bandwidth.  I want the login to still appear as a command, and when logged in, I still want the interface to be commnad line (with a command to open the browser).

Any suggestions on how I can add browser functionality without converting to GUI? 

Thanks in advance,
Leon

---

### Post by Seisen on 2007-12-16
You could try using elinks or lynx which are text based browsers that won't pull a bunch of dependicies like installing firefox would.

---

### Post by mellowd on 2007-12-16
yup, elinks and lynx are your best bet. If you want to look at graphs that mrtg and munin produce though you are going to need a gui. 

What I do is run both munin and mrtg on my server and access the graphs from any other pc like so: server-ip\munin or server-ip\mrtg respectively

---

