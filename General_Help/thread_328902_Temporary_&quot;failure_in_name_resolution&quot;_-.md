---
title: "Temporary &quot;failure in name resolution&quot; - Problem?"
date: 2006-12-31
forum: General Help
---

### Post by Gamzarme on 2006-12-31
Hey. I've got a slightly problem that I think might be affecting my server I have recently setup.
When I book up by 5.10 Ubuntu server distro, before it gets to the log-on state, it goes through 'ok-ing' the various components to the operating system. They all check in except on, in which it tries to contact a time server and fails in the process.

Why does this happen?

I have successfully installed XAMPP/LAMP on this server and it works just fine, I can access it through a web browser on another computer (Firefox on my Windows machine). 


Also, another quick question: does it matter if I reboot or shutdown the machine when XAMPP/LAMP is still running? Or should I shut it down first?

---

### Post by snowx1000 on 2006-12-31
If the server can ping the net and what not, most likely the ntp list is old or that server has problems. You could disable the ntp service or edit /etc/ntp.conf and put different servers at the bottom if you would like to keep your time synced.

---

