---
title: "sources.list.d permission denied"
date: 2023-10-02
forum: General Help
---

### Post by kubasienczyk on 2023-10-02
I'm trying to install Open VPN using the official instructions available here:

[https://community.openvpn.net/openvpn/wiki/OpenVPN3Linux](https://community.openvpn.net/openvpn/wiki/OpenVPN3Linux)

However, I'm failing at this step:

```
# curl -fsSL https://swupdate.openvpn.net/repos/openvpn-repo-pkg-key.pub | gpg --dearmor > /etc/apt/trusted.gpg.d/openvpn-repo-pkg-keyring.gpg
```

The terminal prompts:

```
bash: /etc/apt/sources.list.d/openvpn3.list: Permission denied
```

What do I do? Thanks!

---

### Post by btindie on 2023-10-02
> **kubasienczyk said:**
> 
```
# curl -fsSL https://swupdate.openvpn.net/repos/openvpn-repo-pkg-key.pub | gpg --dearmor > /etc/apt/trusted.gpg.d/openvpn-repo-pkg-keyring.gpg
```


The hash (#) at the beginning of the command signifies that you need to run it as *root*. So prior to running them you first need to type
```
$ sudo -i
```
to become root. Once done, press [FONT=system]Ctrl+d[/FONT] to exit the root session. You can use [FONT=system]sudo[/FONT] along with [FONT=system]tee[/FONT] but it's easier to just use [FONT=system]sudo -i[FONT=arial].[/FONT][/FONT]

The other commands that begin with a dollar sign, you run as your normal user.

---

