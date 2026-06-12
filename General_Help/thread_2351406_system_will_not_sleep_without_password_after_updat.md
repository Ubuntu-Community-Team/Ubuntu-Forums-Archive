---
title: "system will not sleep without password after update"
date: 2017-02-03
forum: General Help
---

### Post by ezrider on 2017-02-03
To get my system to sleep i have to edit this file **/usr/share/polkit-1/actions/org.freedesktop.login1.policy **so the system will suspend without asking for password. After certain system updates this file must get overwritten because i find the system will not sleep again without password.

How can i get this fie to be not be overwritten or is there some other way that i dont have to edit it by hand each time?

Thanks,

Stephen.

---

### Post by ajgreeny on 2017-02-03
What version of Lubuntu?
You should not need to use a password to suspend your machine, so there must be something amiss here.

Has this always been the case for you?

---

### Post by ezrider on 2017-02-03
Its 16.04.1 LTS. 
Its ok if i click shutdown > suspend, but asks for password if computer is not used.
Has always done this unless i edit that file.

---

### Post by ajgreeny on 2017-02-03
Do you mean it will not go into suspend mode automatically from your power-manager settings?

I don't fully understand what you mean by "Its ok if i click shutdown > suspend, but asks for password if computer is not used."

---

### Post by ezrider on 2017-02-04
sorry yes i mean automatically. currently its set to suspend after 30 mins.

---

