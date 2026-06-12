---
title: "Is there a version of NX for Windows?"
date: 2007-06-25
forum: General Help
---

### Post by thenetduck on 2007-06-25
Know this is a Linux forum but wanted to know if there was a version of NX Server for windows. Also if I had a Ubuntu server running Windows Server 2003 on VMWare, could I remote login with NX by NoMachine? or will I have to use windows terminal server? Thanks!

The Net Duck

---

### Post by southernman on 2007-06-25
Google is sooooo great! :p
[http://www.google.com/search?q=NX+Server+for+windows&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a]("http://www.google.com/search?q=NX+Server+for+windows&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

The answer to your question is yes. Which one you'd want to use, well that's a matter of preference.

hth's

---

### Post by thenetduck on 2007-06-25
That's for the client side of things. On the download page it doen't list anything that says download the "Terminal Server" .

Thanks though.

The Net Duck

---

### Post by southernman on 2007-06-25
> **thenetduck said:**
> That's for the client side of things. On the download page it doen't list anything that says download the "Terminal Server" .

Thanks though.

The Net Duck
It's out of my scope but I see:

free edition
server
node
client
server manager
companion

with their own download sections. *shrugs*

I ran across this link that may help you out:

[http://stuffem.wordpress.com/2007/03/13/geek-gal-setting-up-nx-terminal-server-on-ubuntu/]("http://stuffem.wordpress.com/2007/03/13/geek-gal-setting-up-nx-terminal-server-on-ubuntu/")

---

### Post by emalyse on 2007-06-26
Hello- as NX server is basically compressed X over SSH so it's less suited as a terminal server option for Windows which does not use X. The nearest equivalent on windows would be Citrix and then remote desktop/terminal server though of course the number of connections and desktops is restricted on the non server products though registry hacks exist to re enable multiple logins (which was there on the pre releases of XP and then got patched on actual release). You can use NX server/ FreeNX as a gateway to remote desktop though that would mean allocating a separate NX server as your gateway.

---

