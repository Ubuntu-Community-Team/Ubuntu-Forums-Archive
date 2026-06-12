---
title: "How to automatically run a root command on boot?"
date: 2007-05-01
forum: General Help
---

### Post by devmnky on 2007-05-01
Hello there,

I have a command to turn on my laptop's cooling fan forcefully but requires root permissions to do it.

The command is
```
sudo bash -c 'echo "force_on: 1" > /cat/proc/acpi/toshiba/fan '
```

I tried entering that command as a service but it didn't work.

Any ideas?

Thanks,

Leonardo

---

### Post by mexlinux on 2007-05-01
You can add your command at the end of
/etc/rc.local

---

### Post by devmnky on 2007-05-01
Thanks mex!  It worked out. :)

---

