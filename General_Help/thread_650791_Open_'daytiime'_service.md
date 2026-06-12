---
title: "Open 'daytiime' service"
date: 2007-12-26
forum: General Help
---

### Post by jsatubnutufroums on 2007-12-26
Hi,
I want to start 'daytime' and 'echo' services. How can I do that?
Thank you.

---

### Post by heindsight on 2007-12-26
First, you'll need to install xinetd:
```
sudo aptitude install xinetd
```

Next you'll need to enable the daytime and echo services by editing their config files
in /etc/xinetd.d (you should only need to change the disable option from yes to no)

Finally tell xinetd to reload the configuration:
```
sudo invoke-rc.d xinetd reload
```

Note that by default, anyone will be able to connect to these services. You can (if you want),
restrict access to only allow connections from certain addresses, to disallow connections from
certain addresses, or to only accept connections from a specific network interface, by adding
only_from, no_access or bind options to the configuration files (have a look at the xinetd.conf man page
```
man xinetd.conf
```
for details on these and other configuration options).

---

### Post by jsatubnutufroums on 2007-12-27
> **heindsight said:**
> First, you'll need to install xinetd:
```
sudo aptitude install xinetd
```

Next you'll need to enable the daytime and echo services by editing their config files
in /etc/xinetd.d (you should only need to change the disable option from yes to no)

Finally tell xinetd to reload the configuration:
```
sudo invoke-rc.d xinetd reload
```

Note that by default, anyone will be able to connect to these services. You can (if you want),
restrict access to only allow connections from certain addresses, to disallow connections from
certain addresses, or to only accept connections from a specific network interface, by adding
only_from, no_access or bind options to the configuration files (have a look at the xinetd.conf man page
```
man xinetd.conf
```
for details on these and other configuration options).
Thank you.:)

---

