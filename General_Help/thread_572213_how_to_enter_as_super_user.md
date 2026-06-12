---
title: "how to enter as super user"
date: 2007-10-10
forum: General Help
---

### Post by agentbugs on 2007-10-10
i have heard dat this is a problem in ubuntu....u cant get in as super user....can anyone help me with this....?

---

### Post by LaRoza on 2007-10-10
> **agentbugs said:**
> i have heard dat this is a problem in ubuntu....u cant get in as super user....can anyone help me with this....?

Use "sudo" to run something as root, or "gksudo" if it is a GUI program. To create a root account, not recommended, you can enable it.

---

### Post by 3rdalbum on 2007-10-10
> **LaRoza said:**
> Use "sudo" to run something as root, or "gksudo" if it is a GUI program. To create a root account, not recommended, you can enable it.

Clarification: To use sudo, you put it straight before the command that you want to run as root, for instance:

```
sudo nano /etc/fstab
```

If you would rather get an actual root terminal, you do this:

```

sudo su
....run whatever commands you want here

```

---

### Post by thirddeep on 2007-10-10
Or if you want to run with root's environment, use "su -".

And if you really want a root password
```
sudo passwd root
```

Thd.

---

