---
title: "Share home directory"
date: 2008-01-27
forum: General Help
---

### Post by jmvidalvia on 2008-01-27
¿can different users share the same home directory?
I want then to have the same destination when they log in with ssh.
Is there any inconvenient, appart form the fact they must share the same configuration?
Thanks!

---

### Post by Mikecore on 2008-01-27
I would setup a "guess" user account and then just given them both the password. Then they would have the same home directory.  I'm sure there is others ways of doing this but this is probably the safest.

---

### Post by jmvidalvia on 2008-01-28
> **Mikecore said:**
> I would setup a "guess" user account and then just given them both the password. Then they would have the same home directory.  I'm sure there is others ways of doing this but this is probably the safest.

Thanks!
The fact is that these users are sharing a Samba folder with many files, and I would like to control who is connecting from out of our LAN with ssh and who is making changes in files.
All of them have got allready system accounts with no home directory and no shell, and that's why I wonder If I could give them the same home directory to allow connections from Internet keeping the same users structure.
Thanks again!
I am not able to imagine why It wouldn't work or whether it could be dangerous...

---

