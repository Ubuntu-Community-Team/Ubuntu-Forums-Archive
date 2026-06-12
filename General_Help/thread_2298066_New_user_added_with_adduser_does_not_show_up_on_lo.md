---
title: "New user added with adduser does not show up on login screen in Ubuntu 14.04 LTS"
date: 2015-10-08
forum: General Help
---

### Post by Adrian_Moncloa on 2015-10-08
In Ubuntu 14.04 LTS:
 I tried adding this line:
                           greeter-show-manual-login=true 
to the file:
                          /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf 

but still the new user does not show at the login screen though he is listed in /home.

I have also tried adding the same line to /etc/lightdm/lightdm.conf without luck.

---

