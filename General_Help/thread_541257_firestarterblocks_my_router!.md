---
title: "firestarterblocks my router!"
date: 2007-09-02
forum: General Help
---

### Post by skymera on 2007-09-02
sometimes when i start ubuntu i have no internet connection.
even though its enabled.

so i opened firestarter and in terminal typed

sudo /etc/init.d/networking restart

and firestarter showed that its blocking DHCP, DNS, MDNS, from my router.

but if i restart, its fine!?

why is this happening?

---

### Post by por100pre1 on 2007-09-02
Try allowing all connections from your router's IP address. :-k

---

### Post by skymera on 2007-09-02
why should that need to be done?

if it works right now as it is?

nice suggestion, thanks

---

### Post by por100pre1 on 2007-09-02
I know my suggestion sounds really dumb, but I have seen this before. I think it's a firestarter issue, but that rule can work as a workaround. :)

---

### Post by skymera on 2007-09-02
yeah i add my router to firestarter,

thanks :D

---

