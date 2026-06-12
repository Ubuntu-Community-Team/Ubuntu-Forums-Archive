---
title: "Run script as root at boot"
date: 2012-12-14
forum: General Help
---

### Post by Pacopag on 2012-12-14
Hi.  I'm wondering where to put a script that I want to run at boot.  When I google it, there are several options, but many are to run script automatically at LOGIN.  I want this script to run no matter who logs in.

Is the right place /etc/rc.local?

Thanks.

---

### Post by Lars Noodén on 2012-12-14
/etc/rc.local will run at boot after all other startup scripts are run.  It will run regardless of who logs in or even if anyone logs in at all.

---

### Post by aromo on 2012-12-14
rc.local will work.  Alternatively you can:

```
sudo crontab -e
```

This opens vi to edit the root's scheduled tasks.  Append the following line:

```
@reboot /path/to/command
```

Save and exit.

---

