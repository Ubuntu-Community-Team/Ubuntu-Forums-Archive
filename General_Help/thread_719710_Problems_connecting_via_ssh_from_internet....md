---
title: "Problems connecting via ssh from internet..."
date: 2008-03-09
forum: General Help
---

### Post by foldor on 2008-03-09
OK I have installed OpenSSH and got it up and running and working when I test it from a locally connected computer. I then forwarded port 22 on my Linksys WRT54GL router with DD-WRT v23SP2 firmware installed.

After this I try to connect using putty, by manually typing in the computers ip address and it does not work. I do not know if this is a Kubuntu problem or a router issue so I thought I would try here first.

I also tried opening port 5900 to try and use VNC and it also works when I manually type the LOCAL IP, but if I try and type the external IP it does not work. I have made sure I properly forwarded the ports and they are seen as being open on open port sites. So I thought maybe Kubuntu was disabling remote connections for some reason.

---

### Post by JawsThemeSwimming428 on 2008-03-09
I had a similar issue when trying to get NX Nomachine (ssh) running on my Mepis install. Try turning off your firewall and see if it works. If it works turn your firewall back up on try an figure out what is blocking it. I know in Guarddog you have to allow ssh connections.

---

### Post by foldor on 2008-03-09
Thats the thing, I installed guarddog and told it to turn off the firewall completely. When I did that, it stopped timing out, it just flat out refused me.

---

