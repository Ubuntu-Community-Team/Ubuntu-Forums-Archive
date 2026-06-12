---
title: "Password strength issue"
date: 2019-11-04
forum: General Help
---

### Post by baiteh on 2019-11-04
Hi - I've been asked to implement a password policy of my Ubuntu users and have come up with the following;

sudo apt install  -y libpam-pwquality
sed -i 's/^PASS_MAX_DAYS.*/PASS_MAX_DAYS   365/g' /etc/login.defs
sed -i "s/^passw.*.pam_pwquality.*/password        requisite                       pam_pwquality.so retry=3 minlen=10 ucredit=-1 lcredit=-1 dcredit=-1  ocredit=2/g" /etc/pam.d/common-password

However the min length is only being set to 8 characters - any ideas?

All the other settings are working just fine...

---

