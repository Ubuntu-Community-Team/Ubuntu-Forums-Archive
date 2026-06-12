---
title: "dnscrypt-proxy: 'Could not execute systemctl' error when installing"
date: 2024-08-14
forum: General Help
---

### Post by goudron on 2024-08-14
I am trying to install *dnscrypt-proxy* in Ubuntu 24.04 from the official repository:

```
sudo apt install dnscrypt-proxy
```

At the moment, the current version is *2.0.45+ds1-1.2ubuntu0.24.04.1*

During installation, I get the following error:

```
Could not execute systemctl:  at /usr/bin/deb-systemd-invoke line 148.
```

I opened the *deb-systemd-invoke* file using *nano*. The 148th line has the following content:

```
system('systemctl', '--quiet', @instance_args, $action, @start_units) == 0 or die("Could not execute systemctl: $!");
```

Please tell me what is preventing the installation and how can I fix it?

---

### Post by currentshaft on 2024-08-14
66

---

### Post by goudron on 2024-08-15
Thank you, it's works :)

---

