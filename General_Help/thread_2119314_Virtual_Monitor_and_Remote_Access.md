---
title: "Virtual Monitor and Remote Access"
date: 2013-02-23
forum: General Help
---

### Post by Hubok on 2013-02-23
I am using Ubuntu 12.04.1 64-bit with Xen virtualization on Virpus. Essentially, the Ubuntu installation has no monitor, so I need to make a virtual one and use it for simple remote access. I don't have physical access to the machine, only a text SSH client.

Is there a way that I can make a "fake" monitor from SSH and access the computer remotely (as if it was a normal Ubuntu computer)?

---

### Post by dcstar on 2013-02-24
> **Hubok said:**
> I am using Ubuntu 12.04.1 64-bit with Xen virtualization on Virpus. Essentially, the Ubuntu installation has no monitor, so I need to make a virtual one and use it for simple remote access. I don't have physical access to the machine, only a text SSH client.

Is there a way that I can make a "fake" monitor from SSH and access the computer remotely (as if it was a normal Ubuntu computer)?

To enable Desktop Sharing (using VNC protocol), install the **dconf-tools** package and then:

```
gsettings set org.gnome.Vino remote-access enabled true
```

---

### Post by Hubok on 2013-02-24
> **dcstar said:**
> To enable Desktop Sharing (using VNC protocol), install the **dconf-tools** package and then:

```
gsettings set org.gnome.Vino remote-access enabled true
```

What packages do I need besides dconf-tools? I tried the command you specified and it gave me a -bash command not found error.

---

