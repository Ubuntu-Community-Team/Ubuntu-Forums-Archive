---
title: "Vlock added failled login attempt and causing lockout using Pam"
date: 2015-09-23
forum: General Help
---

### Post by jared32 on 2015-09-23
Versions:
OS - Ubuntu 14.04.3 LTS
vlock - 2.2.2-3

Hello,

I'm still very new to Ubuntu (Couple of weeks) and I'm doing some hardening on an Ubuntu vm. My friend and I have been using PAM for authentication and we noticed today that we were getting locked out. We narrowed it down to my having discovered and begun using vlock. So we tested vlock and when I am at the lockout screen and I press [Enter] in order to get the password prompt, We get a failed loggin attempt in the background. 

Some sites mentioned looking at the vlock config file in /etc/pam.d but I noticed there isn't one there.

Any thoughts on how I should proceed to debug this or where I should look?

Again I'm new to this OS and community so if I am not providing enough information, please let me know what else I can provide.

Thanks in advance,

Jared

---

