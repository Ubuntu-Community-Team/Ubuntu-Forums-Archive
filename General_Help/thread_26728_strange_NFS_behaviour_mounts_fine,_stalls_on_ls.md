---
title: "strange NFS behaviour: mounts fine, stalls on ls"
date: 2005-04-13
forum: General Help
---

### Post by IndieRockSteve on 2005-04-13
ok, I got a new laptop, Thinkpad T22 to replace my older T20. My T20 has Kanotix w/ many debian updates. I'm trying out Ubuntu on my T22. So far not bad. BUT. I have a file server which I have 5 drives exported via NFS. All the linii(linux's?) I've installed on my T20 never had a problem mounting and using these drives. I've had Mandrake and Kanotix on it. Now, in Ubuntu all the drives mount but only 1 allows me to run ls. whether I manually mount them, mount them in fstab, doesn't seem to matter. I've mirrored the users/uid's so the three owners on the server match on both laptops. I don't see anything in the logs other than:

kernel: nfs warning: mount version older than kernel

also, I noticed I have no /etc/defaults/portmap file but the portmap package is installed and portmap seems to run fine.

so now I'm stuck. I'd love to stick with Ubuntu for a little longer and play around, but this is baffleing me and I can't think of any reason why.

---

### Post by IndieRockSteve on 2005-04-14
bump

---

### Post by dninja on 2005-09-02
[QUOTE=IndieRockSteve]bump[/QUOTE]
 Ever got a response from this? Ever fixed it?

---

