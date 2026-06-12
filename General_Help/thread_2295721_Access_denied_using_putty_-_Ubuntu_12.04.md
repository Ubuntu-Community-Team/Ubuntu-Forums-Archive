---
title: "Access denied using putty - Ubuntu 12.04"
date: 2015-09-21
forum: General Help
---

### Post by KiwiJJ on 2015-09-21
Hi,
User1 can login to the Ubuntu 12.04 server using Putty fine. 
User2 cannot login using Putty and gets access denied. 
When I login as user2 from the VMware console it logs in fine so the password is correct. 
In the Auth.log I see this: pam_unix(login:auth): authentication failure; logname=user2 
FAILED LOGIN (1) on '/dev/tty1' FOR 'UNKNOWN', Authentication failure
In sshd_config I have an AllowGroups which allows group1 User2 is a member of group1
anybody have any ideas ?

---

