---
title: "Root Password In Shell Script"
date: 2016-02-08
forum: General Help
---

### Post by grace3 on 2016-02-08
Hello,

I have wriiten several shell scripts that include commands that require root. I always have to supply the password to the CLI manually. Is there anyway to do this within the script itself, so I don't have to interact with it.

Thanks, Grace

---

### Post by SeijiSensei on 2016-02-08
The easiest solution is run the script as root with sudo and eliminate any sudo references in the script itself.

If the script is designed to run from cron, putting the corresponding entry in /etc/crontab or /var/spool/crontab/root will run the script with root privileges.  Alternatively, if you want to script to run hourly/daily/weekly/monthly, create a symbolic link to the script from one of the /etc/cron.* directories.  For instance, to run a script with root privileges once per hour, use
```
cd /etc/cron.hourly
sudo ln -s /path/to/your/script

```

---

### Post by grace3 on 2016-02-09
I don't think I need to link it to cron. For example, I have a script that changes my mac address using macchanger. It's kind of a pain to use; because I have to disable networking, run the script and then reenable networking. I would rather just have the script do all of this; and then add the script to startup applications. If necessary, I'll put a sleep statement in the script so that the boot is complete before any of the commands actually run. I want to do this with other scripts as well.

---

### Post by SeijiSensei on 2016-02-09
Anything you want to run at boot can go in /etc/rc.local.  It's the last script run during boot up.  Everything in that file runs with root privileges.

---

