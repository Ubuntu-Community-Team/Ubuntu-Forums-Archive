---
title: "Ubuntu 8.04 aks for password at shutdown"
date: 2008-07-02
forum: General Help
---

### Post by zakhooi on 2008-07-02
Hi,

Since I upgraded to (x)ubuntu 8.04 I noticed that when I want to shutdown through the menu a window pops up asking me for the password.

It wasn't like that before.

Does anyone know how to get rid of this? I just want my lappy to shutdown without asking for a password.

Thanks in advance

---

### Post by cmnorton on 2008-07-02
This is from 7.04, but it might get you closer to solving your problem:

[https://answers.launchpad.net/ubuntu/+question/7998](https://answers.launchpad.net/ubuntu/+question/7998)

---

### Post by zakhooi on 2008-07-03
> **cmnorton said:**
> This is from 7.04, but it might get you closer to solving your problem:

[https://answers.launchpad.net/ubuntu/+question/7998](https://answers.launchpad.net/ubuntu/+question/7998)

Thanks for your reply, I fiddled with the settings in /etc/sudoers as described but with no luck.

I still get the password prompt, the problem just came along with the upgrade.

---

### Post by zakhooi on 2008-07-03
Strange thing is that for the reboot option (through the startmenu) it _sometimes_ not all the time whereas for the shutdown option (through the startmenu) it always asks for it.

I made sure the /etc/sudoers file is ok and I also tried to put my normal user in group-id '0', but still with no luck.

Any other ideas please?....

---

