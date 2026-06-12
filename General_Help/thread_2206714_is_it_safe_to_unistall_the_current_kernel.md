---
title: "is it safe to unistall the current kernel?"
date: 2014-02-20
forum: General Help
---

### Post by lvm on 2014-02-20
Will it update grub.cfg and watever else necessary automatically to boot from the previous one, or I'll have to it manually? And, if yes, should I change anything else apart from grub.cfg?

For the curious: upgraded 12.04 internet proxy running squid and privoxy from 3.2.0-58 to 3.2.0-59 - got lockups. As soon as another machine attempts to use the proxy, it (proxy machine) dies - no reaction to keyboard, network, etc, and no useful messages in syslog; but when I try to use internet locally on the proxy machine and via the same proxy software it works just fine. Booting back to 3.2.0-58 fixed the issue.

---

### Post by sudodus on 2014-02-20
Removing (uninstalling) the kernel with for example Ubuntu Tweak or Synaptic can do it with desktop versions. If a server, you use the command line.

```
sudo apt-get remove linux-image-3.2.0-59-generic
```

if you did not do it already. Then it should be enough to run

```
sudo update-grub
```

to get a correct grub menu and default boot option (without the removed kernel) unless you have tweaked your system to boot another option than the first one (in the grub menu).

---

### Post by mcduck on 2014-02-20
One warning to keep in mind is that uninstalling the latest kernel will also uninstall the kernel metapackage which is responsible of getting the kernel updates for you. So you'll need to manually keep track when there's a new kernel and reinstall the metapackage at that point to get back to normal kernel updates.

What I'd probably do instead is just modify grub.cfg to boot the last used kernel rather than the first on the list. That way you can keep the latets kernel around and continue getting the updates (in hope they fix your probelm) but don't need to switch to the version you need to use for now every time you boot the machine.

---

