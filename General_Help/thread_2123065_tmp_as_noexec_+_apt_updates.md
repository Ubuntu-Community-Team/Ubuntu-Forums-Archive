---
title: "/tmp as noexec + apt updates"
date: 2013-03-07
forum: General Help
---

### Post by shuverisan on 2013-03-07
Often I read that mounting /tmp in tmpfs as noexec causes problems with apt during system updates. I've been doing this on installs of Ubuntu Precise and Quantal and the only hint of an issue it gives is that the verbose output of the software updater says, 'Can't cache run scripts.' Everything otherwise finishes and works fine.

Has anyone experienced anything more severe on newer Ubuntu versions or other distros with /tmp as noexec?

---

### Post by schragge on 2013-03-07
I tried it once, but then quickly reverted the change. Cannot say why anymore. Quite possible that dpkg message *Can't cache run scripts* freaked me out. :)

[highlight]Update.[/highlight] To make *dpkg* happy, add the following to the file */etc/apt/apt.conf*:
```

DPkg::Pre-Invoke {"mount -o remount,exec /tmp";};
DPkg::Post-Invoke {"mount -o remount /tmp";};

```

---

