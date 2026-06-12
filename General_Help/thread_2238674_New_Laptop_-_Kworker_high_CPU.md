---
title: "New Laptop - Kworker high CPU?"
date: 2014-08-09
forum: General Help
---

### Post by mykrob on 2014-08-09
Got a new laptop, a Toshiba E45-B4200. All the hardware seems to work just perfect, right out of the box. I do have an occasional hiccup, and it looks like it may be due to the process Kworker running abnormally high.
I have read several threads on the topic, and they all seem to be a hackjob with no definitive resolution.

That said, I'd like to see if any of you can offer some assistance with helping me pinpoint the cause of the runaway process and figure out how to resolve it. My hardware specs are attached. Let me know whatever you need from me to be able to help.

Thanks

[ATTACH]255349[/ATTACH]

---

### Post by mykrob on 2014-08-11
I tried the instructions here to kill the offending interrupt, but it seems that nothing I do is able to append the file:

[http://carlocapocasa.com/crushing-the-kworker-uprising-or-how-to-fix-your-linux-lenovo-ideapad-y560p/](http://carlocapocasa.com/crushing-the-kworker-uprising-or-how-to-fix-your-linux-lenovo-ideapad-y560p/)

---

### Post by mykrob on 2014-08-12
bump

---

### Post by mykrob on 2014-08-12
OK, so i found how to disable the ACPI interrupt that is causing the problem:

```

sudo su
myk@E45-B4200:~$ sudo su

root@E45-B4200:/home/myk# echo "disable" > /sys/firmware/acpi/interrupts/gpe10
root@E45-B4200:/home/myk# cat /sys/firmware/acpi/interrupts/gpe10 
46093046   disabled

```

but now I need help getting a cronjob to pass this command and actually work. I think my previous cron jobs were not working due to permissions.

---

