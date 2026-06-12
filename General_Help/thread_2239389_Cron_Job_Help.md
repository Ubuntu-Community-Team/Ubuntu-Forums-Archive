---
title: "Cron Job Help"
date: 2014-08-13
forum: General Help
---

### Post by mykrob on 2014-08-13
I need a cron job, script, or something to run every time the computer boots to disable an ACPI interrupt. The command that I pass if I run it in terminal is:
```

sudo su
echo "disable" > /sys/firmware/acpi/interrupts/gpe10

```

but for some reason, I have to run it twice in order for it to work. Not sure why, I just know that if I do it twice, ti works without fail. So, how so I execute this with proper privileges in a cron job to execute twice every time I boot? It has to be done with sudo su, because for whatever reason, if I run it with just sudo, I get a permission denied error.

Help?

Thanks

---

### Post by mykrob on 2014-08-13
nevermind. I just entered this command twice in the cron job

```

sudo su
crontab -e

#entered this into crontab>
@reboot echo "disable" > /sys/firmware/acpi/interrupts/gpe10
@reboot echo "disable" > /sys/firmware/acpi/interrupts/gpe10

```

---

### Post by SeijiSensei on 2014-08-13
If you want to run a command at boot, the easiest solution is to put it in /etc/rc.local.  That script is run with root privileges after all other startup scripts have finished.

---

