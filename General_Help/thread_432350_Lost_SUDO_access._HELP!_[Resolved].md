---
title: "Lost SUDO access. HELP! [Resolved]"
date: 2007-05-03
forum: General Help
---

### Post by Chaoticwhizz on 2007-05-03
While trying to configure permissions access for komba2 I somehow removed almost all the groups from my login. My login was the main login so there are no other logins on this PC with admin access. From what I understand logging in as root isn't possible even in tty.I rebooted into Windows and edited the /etc/group file using Wordpad to include my name with adm, admin, and root. I saved the file and rebooted back to Kubuntu and still no change. id's output is just:

uid=1000(chaoticwhizz) gid=1000(chaoticwhizz) groups=1000(chaoticwhizz)

I am using Kubuntu Fiesty. I can access the ext3 filesystem from Windows with a software addon. I am completely lost. ANy help would be greatly apprecaited

---

### Post by aysiu on 2007-05-03
This will help you:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Chaoticwhizz on 2007-05-03
Thank you. Going into Recovery mode and and entering the following fixed it
```
addgroup chaoticwhizz admin
```

---

