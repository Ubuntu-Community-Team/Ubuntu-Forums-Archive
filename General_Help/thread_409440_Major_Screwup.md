---
title: "Major Screwup"
date: 2007-04-14
forum: General Help
---

### Post by mtuller on 2007-04-14
I really did it here. I was getting errors when trying to access pages in my web folder. It looked like it was because of permissions, so I went to change the user to www-data, which is the user which Apache runs under. I was in /var and wanted to chown ./www I forgot the www and changed all of var  to www-data as the user. I went to change that back, and the sudo files are now set incorrectly, and I can't change them back. When I try sudo, I sudo: /var/run/sudo owned by uid 33, should be uid 0get 

I never set the root password, so I can't login to that. Is there anything I can do to get the sudo files back to root so that I can fix this mess?


Mike

---

### Post by aysiu on 2007-04-14
Boot into recovery mode and type: ```
chown -R root:root /var
reboot
```

---

### Post by mtuller on 2007-04-14
Thank you. I will try that on Monday.

---

