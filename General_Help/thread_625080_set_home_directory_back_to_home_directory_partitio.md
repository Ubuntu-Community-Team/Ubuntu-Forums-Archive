---
title: "set home directory back to home directory partition"
date: 2007-11-27
forum: General Help
---

### Post by rob1101 on 2007-11-27
well i changed my home directory to a different partition with [this]("http://www.psychocats.net/ubuntu/separatehome") guide. im pretty sure this was a success and not the cause of my problem. 

i killed ubuntu not to long ago so i needed to reinstall. i chose manual reinstall and selected on partition as root and my home partition as my /home. the default admin user that you create during installation works fine, but i  did have a few more users. there files are there in the /home directory but the actual users them selves were not created with the installation. and creating new ones with the same name just gave me errors when i tried to logg in with them. 

so how do i fix this?

---

### Post by Cochise on 2007-11-27
you need to give the new users premission to write to the home folder from the previous installation. google chmod and look for the command for changing the user and group ownership of folders.

---

### Post by rob1101 on 2007-11-27
> **Cochise said:**
> you need to give the new users premission to write to the home folder from the previous installation. google chmod and look for the command for changing the user and group ownership of folders.

oh yea duh :P thx

---

### Post by Cochise on 2007-11-28
did you get it sorted?

---

