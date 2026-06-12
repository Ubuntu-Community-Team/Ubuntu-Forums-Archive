---
title: "SSH doens't work behind proxy?&gt;"
date: 2006-08-21
forum: General Help
---

### Post by moufranica on 2006-08-21
Dear Gurus,
I am trying to login to my SSH account from Gnome Terminal. I have set the $http_proxy variable, but it seems ssh is not using that variable. What do I do? I am using 6.06.

---

### Post by Lunar_Lamp on 2006-08-21
Do you have control of your proxy?  What port are you trying to use?  It may be that your proxy blocks connections on certain ports for 'security reasons' (I know the one I use at work does).

---

### Post by ProjectGod on 2006-08-21
open up TCP port 22 on the proxy firewall. incoming and outgoing.

---

### Post by moufranica on 2006-08-25
> **Lunar_Lamp said:**
> Do you have control of your proxy?  What port are you trying to use?  It may be that your proxy blocks connections on certain ports for 'security reasons' (I know the one I use at work does).

Hi, I require a proxy to connect to the internet. Proxy is using port 8080, and the proxy allows only port 22 and 443 traffic. I have ssh running on port 443. My issue is that the ssh client is not using the default network proxy setup in gnome enviroment to connect to. That is $http_proxy is not being used. Hope someone can help. Cheers!

---

### Post by Gio2k on 2006-09-01
I have the same problem. At the student residence i live, my internet connection works through two proxies, an http one (port 80), and a SOCKS 5 one (port 1080). Under windows i used putty and configured it to use the SOCKS 5 proxy, which is the one that allows me to connect with ssh to other machines.
However, i don't know a way to configure ssh under Ubuntu to use a socks 5 proxy. Anyone has an idea?

---

