---
title: "Extraction"
date: 2007-01-19
forum: General Help
---

### Post by icehammer on 2007-01-19
Whenever i try to unzip any archive file, it always comes up with "Operation not permitted: You don't have rights"..

1. I installed ubuntu..
2. My 'group', initially was my own username, i manually set it to "admin".
3. if i need to perform a task which requires me to be root, i do sudo -i in the terminal, or change my group to "root"..

Nothing makes the archive budge still..!! It half extracts, and i can't even delete it then.. coz i don't have permissions!!! 

How can i get over this??

---

### Post by lamego on 2007-01-19
> 2. My 'group', initially was my own username, i manually set it to "admin".
That was correct, the default user main group is the group with the same name, that is not a problem because you are also member of other groups, you should not change this in the first place.

You have encountered problems because now you have folders and files owned by your "username" group and for wich you no longer have access.

Just set your primary group back to the group with your username,

---

