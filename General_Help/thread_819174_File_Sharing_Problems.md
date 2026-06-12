---
title: "File Sharing Problems"
date: 2008-06-05
forum: General Help
---

### Post by JemW on 2008-06-05
OK...

Desktop running Hardy
3 laptops on the network - two running XP Pro the other running Vista (Windows version matters not as I get the same result from both).

I need file sharing with a level of security / access control. I am the only user on the Hardy machine. I can successfully share a folder with the laptop users giving them guest / read only access, but I have another folder on the Hardy machine for which I alone require write / delete access from my XP Pro laptop. I can manage to get username / password read access by sharing but with only the first box in 'Sharing' ticked, i.e. no write access for 'others' and no access for those 'with no user account'. When I look at the permissions tab for this 'restricted' folder, it seems to indicate that the owner (my user name) has folder 'create / delete access' but clearly I don't - I open the folder from my laptop with my username / password when prompted, the folder opens - I can read but *not* create / rename / delete.

Help appreciated...

---

### Post by Quintin Riis on 2008-06-05
Find the share in question in /etc/samba/smb.conf

add 

writable = yes

to the share.

---

### Post by JemW on 2008-06-05
> **Quintin Riis said:**
> Find the share in question in /etc/samba/smb.conf

add 

writable = yes

to the share.

Excellent. Of Course. Thank you.

---

