---
title: "init.d scripts not working"
date: 2008-07-10
forum: General Help
---

### Post by Deidgar on 2008-07-10
I installed ubuntu server v8 and none of the scripts in init.d folder work.  I am sure this is some easy fix but I don't really understand upstart so don't know the fix.

for example, networking restart -> I get "-bash: networking: command not found"  but it's sitting right there if I ls.

---

### Post by lisati on 2008-07-10
How are you running them? If you're in the init.d folder, you will need to put './' in front of the script name.

---

### Post by Gunman1982 on 2008-07-10
How it works:

'sudo /etc/init.d/networking restart'
or
'cd /etc/init.d'
'sudo ./networking restart'

If you are logged in as root you can run the commands without sudo.

---

### Post by Deidgar on 2008-07-10
DOH!  yeah, I had a dumb attack today, forgot that part.  sorry, I thought something about the runlevels had changed.  Thanks!

---

