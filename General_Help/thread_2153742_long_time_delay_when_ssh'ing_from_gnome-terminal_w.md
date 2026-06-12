---
title: "long time delay when ssh'ing from gnome-terminal while using ip address"
date: 2013-06-12
forum: General Help
---

### Post by lelcamel on 2013-06-12
Hi,

When I ssh to a remote server in the local network, i use it's IP address and for some reason there's a long delay between the stage of accepting the rsa key (which is immediate) until the prompt for password is displayed.
If i use Putty, it works flawlessly and prompts for password in the same second i click connect on Putty.
Anyone knows what could be the reason?

Thanks
lelcamel

---

### Post by efflandt on 2013-06-12
Many Linux server apps, like ssh, attempt to resolve any connecting IP to a name. If the IP does not resolve, there can be a delay connecting until DNS times out.

If you have a broadband router (or modem/router) that will usually handle DNS, and in many cases will forward or reverse resolve name vs. IP based on netbios names (used for Windows file/printer sharing).  So when you connect from PuTTY in Windows, maybe it knows the name of your client computer, and when you connect from Linux it does not.

One way to tell if DNS might be the issue is to type **who** after connecting by either method and see if it shows a name for your client computer or just an IP.

---

