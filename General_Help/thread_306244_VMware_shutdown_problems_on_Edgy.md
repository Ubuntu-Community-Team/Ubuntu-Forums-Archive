---
title: "VMware shutdown problems on Edgy"
date: 2006-11-24
forum: General Help
---

### Post by Macchi on 2006-11-24
Hello!

I am having prolems with VMware Server that prevents shut down of the host, my VAIO laptop running Edgy. I get a message that it is attempting to shut down the virtual network, but it gets stuck.

Any ideas on how to solve this?

---

### Post by Macchi on 2006-11-27
The problem turned out to be some weird interaction between Firestarter and the virtual (IP) plus hostname networks set by VMware Server.
I had to purge both applications and will later reinstall VMware, hoping for better stability, since VMware is a great tool.

---

