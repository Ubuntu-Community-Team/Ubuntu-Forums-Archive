---
title: "Virtualbox Available to other Users"
date: 2015-02-14
forum: General Help
---

### Post by ktz84 on 2015-02-14
At the minute I have 3 users on my account. Myself, my brother & a more generic one called others. I'm the only with admin rights. At the min I have a bunch of directories shared under media. Under /media/myusername/VM/Vbox I have all my VMs including a Windows 7 image. This image I now want to make available to both my other two user accounts. My though on this was to move it out /media/myusername and instead move it /media/shared/VM/Vbox/Win7 and create a new group called everyone and add all 3 users to that group. I would then change the permissions on /media/shared to myusername:shared that way everyone will have rights to access it.

Will this work and even if it does is there perhaps a better way to manage this.

Thanks

---

### Post by v3.xx on 2015-02-14
Looks like a plan :)

I don't like moving directories around.  For me, it leads to confusion.  I like one access point so I have a 'data partition' for all to share.  

There is also limited sudo accounts (sudoers/visudo).

---

