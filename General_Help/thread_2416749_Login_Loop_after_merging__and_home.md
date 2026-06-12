---
title: "Login Loop after merging / and /home"
date: 2019-04-14
forum: General Help
---

### Post by thomasbur on 2019-04-14
G’day, I’ve made a mistake.
I copied my /home partition over to the / partition, deleted the /home partition, and then extended /. I’ve deleted the entry in fstab for /home. I’ve now got the login loop issue, please help :).

Edit: for clarity

---

### Post by oldfred on 2019-04-14
Most suggest separating / from /home if you have room.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Impavidus on 2019-04-15
You most likely messed up permissions or ownership when copying the files from your /home partition to your root partition. While using the live disk as instructed by oldfred, can you also mount the root partition of your installed system and check ownership and permissions of /home/username and its contents?

---

