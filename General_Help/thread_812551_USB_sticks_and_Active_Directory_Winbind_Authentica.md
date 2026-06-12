---
title: "USB sticks and Active Directory Winbind Authentication"
date: 2008-05-30
forum: General Help
---

### Post by samgurung on 2008-05-30
Dear All,

I have set up my ubuntu machine to correctly authenticate via an Active Directory server using winbind; but when a user logs in to the machine using his AD account he is unable to use his pen drive. Some issue with HAL security. Googling around i found a possible solution using pam_group.so -  but the funny thing is pam_group.so adds the AD user to all other groups (audio, dip, etc...) except to plugdev and admin. Any clues as to why this is happening would be much appreciated


Thanks,

---

