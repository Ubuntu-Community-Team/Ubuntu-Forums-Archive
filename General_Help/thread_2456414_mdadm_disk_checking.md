---
title: "mdadm disk checking"
date: 2021-01-11
forum: General Help
---

### Post by unixcommando on 2021-01-11
Hello,

    I'm running Ubuntu 20.04LTS on a Raspberry Pi 4 as a NAS on my network.  I have a JBOD with 4 10T disks in a RAID5 configuration using mdadm.  At least once a week mdadm performs a check on my metadevice which being so large takes 3 days to complete during which IO slows to a crawl.  If I were using this as a general file store or video library this would be fine, but I'm using the NAS as a backend for my home VMware lab and it kills performance of my vCenter as well as my VMs.  

    Everything I can find on mdadm says that the checkarray routine is initiated from cron, but I'll be damned if I can find a cron job anywhere, there is nothing /etc/cron.d, there is nothing in /var/spool/cron.  There is a dpkg-reconfigure for mdadm which allows you to make a binary selection as to whether it should check the array once a month, but that's only a binary pick, either on or off.

    Where exactly is schedule that runs this check?  I want my array checked but not so frequently, I can't have my NAS dependent applications crushed 3 days out of every week, that just won't do.

Thanks
-Bob

---

### Post by TheFu on 2021-01-11
Tip: Don't use USB to connect to RAID devices. There will always be problems. Always.

Schedules on all Unix systems are controlled by cron.  There are a number of different places for "crontab" files. Which gets used depends on who the person that setup the crontab and what they like/know/understand.  /etc/cron.*. And check the anacron files too.

You can tell mdadm to only run the checks when the array isn't busy.  I don't recall how, but it wasn't hard to find.  You can also force the check if you like when you want it using cron. I have a daily scan in /etc/cron.daily/  The mdadm manpage has more.

---

### Post by unixcommando on 2021-01-11
Thanks for the suggestions, but there's nothing in any /etc/cron.*, and anacron isn't on the box.  This is a real head scratcher.

-Bob

---

### Post by deadflowr on 2021-01-12
mdcheck is a systemd service in 20.04.
look at 
```
systemctl status mdcheck_start.timer
systemctl status mdcheck_start.service
```

Interestingly, this wasn't the way it shipped for 20.04 originally,
See: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1852747]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1852747")

I would think you can simply disable the timer,
or mask it.

---

### Post by unixcommando on 2021-01-12
Thanks, this is the first I've seen of these services, all the google searches, even for 20.04, talk about cron.  I don't want to stop it, I just want to change when it runs, it seems to run weekly, if I could insure it only runs once a month I think I'd be ok.

---

