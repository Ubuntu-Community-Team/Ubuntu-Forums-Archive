---
title: "How to configure Firestarter to be able to syncronize a PocketPC?"
date: 2006-12-09
forum: General Help
---

### Post by fedsal on 2006-12-09
Hello everyone,

I tried to synchronize my PocketPC with my desktop (Ubuntu 6.10) and I followed the advice given on this page:

[https://help.ubuntu.com/community/PocketPCHowto](https://help.ubuntu.com/community/PocketPCHowto)

On that page, under the heading "Routine for using a pocket pc" there is a line saying: 

"Make sure ports 5678, 5679 and 990 are not blocked by a firewall."

My problem is that I have no idea how to configure Firestarter to open these ports. 

I can create policies (inbound and outbound)for the ports mentioned (5678, 5679, and 990), but I do not know what IP address (there are three mentioned: local IP, remote IP, DNS server), host, etc. to use.

If by any chance you have any suggestions I would appreciate them very much.

Thank you.:)

---

### Post by kd7swh on 2006-12-09
you should be able to create policies (in\out) for those ports. I have had a lot of problems with firestarter. Starting on boot, and not covering all of my interfaces. I use shorewall now.

anyway, just make sure your policies includes the three ports inbound and out.

let me know how it works

---

### Post by fedsal on 2006-12-10
Hello kd7swh,

I appreciate the fact that you want to help but you did not address the issue I have.

As mentioned in my initial email, I can create policies (inbound and outbound) for the ports mentioned (5678, 5679, and 990), _but I do not know what IP address (there are three mentioned: local IP, remote IP, DNS server), host, etc. to use._.

Thank you again for trying to help.

fedsal

---

