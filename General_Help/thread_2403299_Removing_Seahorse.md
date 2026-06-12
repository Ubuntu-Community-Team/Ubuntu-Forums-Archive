---
title: "Removing Seahorse"
date: 2018-10-09
forum: General Help
---

### Post by feartheterrapin on 2018-10-09
I do not fully understand the benefit of Seahorse. I see it saves most my web passwords, but Firefox can do that to. I also see it saves my VPN passwords, but I thought OpenVPN could do that for me if I wanted. And I don’t see any configuration where I designate what passwords can be saved and which ones not. To my limited knowledge, Seahorse seems to be no more than a password collection tool that complains when you leave it in the locked mode. I am sure Seahorse does more, but...what would happen if I removed it? Would I break some other function? What I be subject to extreme inconveniences. I was hoping to get some advice before learning by trial and error.

---

### Post by DuckHook on 2018-10-09
> **feartheterrapin said:**
> &#8230;I was hoping to get some advice before learning by trial and error.
A good policy.

Seahorse is integral to your GUI/system and must not be removed. If you ever use GPG or SSH keys, for example, Seahorse manages these keys for a seamless experience in your GUI-based apps that depend on such keys. It is also the management app for Chromium keys/certs, so while FF takes care of its own keys/certs, Chrome/Chromium offloads to Seahorse.

BTW, I encourage you to learn by trial and error. The best way to do so is not on your base install, but in a VM that you can roll back to some unbroken prior snapshot.

---

### Post by feartheterrapin on 2018-10-10
Thanks for the reply and providing good reasons not to remove Seahorse.  But I do not need Sehorse saving my Firefox passwords or VPN passwords.  I do not see any configuration to prevent this behavior.  Is there anything I can do to prevent Seahorse from saving these passwords?

---

### Post by DuckHook on 2018-10-10
You can remove these keys from within seahorse itself. If you are sure about what you want, navigate to the key entries in seahorse and just remove them.

*EDIT*

Pardon me. Did not read properly your request to permanently switch off such behaviour. Will do some research and get back you you.

---

### Post by DuckHook on 2018-10-10
You may find these links of interest:

[https://superuser.com/questions/969484/what-is-gnome-keyring-seahorse-and-why-its-storing-my-passwords-in-plaintext](https://superuser.com/questions/969484/what-is-gnome-keyring-seahorse-and-why-its-storing-my-passwords-in-plaintext)
[https://www.linux.com/learn/intro-to-linux/2018/2/how-manage-pgp-and-ssh-keys-seahorse](https://www.linux.com/learn/intro-to-linux/2018/2/how-manage-pgp-and-ssh-keys-seahorse)
[https://help.gnome.org/users/seahorse/stable/pgp-delete.html.en](https://help.gnome.org/users/seahorse/stable/pgp-delete.html.en)

According to my research, all that you need to do is delete the offending key. This should henceforth make a well developed app ask you for its passphrase each time it needs to connect.

---

### Post by feartheterrapin on 2018-10-10
I will take a look at the links.  But I have tried deleting the offending web site and VPN password entries.  They simply get re-populated when I use them again.  Thanks for the extra research.

---

