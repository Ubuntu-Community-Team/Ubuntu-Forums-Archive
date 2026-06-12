---
title: "[SOLVED] How to make sshd not require reverse lookup?"
date: 2007-10-16
forum: General Help
---

### Post by pinkunicorn on 2007-10-16
My sshd requires incoming connections to have working reverse name lookups. If I'm in a hotel or something I might not have that and then not be able to reach my server, so I'd like to make it stop require reverse lookups. But how? I don't see anything obvious in /etc/ssh/sshd_config or in "man sshd".

---

### Post by hvc123 on 2007-10-16
apparantly(imtrying now)

you can add "UseDNS no" to your sshd_config (at the bottom) and restart sshd by 

./sshd restart in /etc/init.d or restart ya machine

---

### Post by pinkunicorn on 2007-10-16
Thanks!

---

