---
title: "System time update as non root user."
date: 2007-07-20
forum: General Help
---

### Post by wmutahi on 2007-07-20
Hi All,
I have an application which is not run by a non super user but I would like it to update the system time at certain intervals. Is there a way to make a non super user update system time without using sudo?,
If anyone could help.
Thankyou.

---

### Post by brent113 on 2007-07-21
The files for local time are kept in a root owned system folder, so as far as I know, you will always have to run it as root.

You can look at this too: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29")

---

### Post by Mr. C. on 2007-07-21
Are you looking to simply ensure the time is accurate ?

MrC

---

