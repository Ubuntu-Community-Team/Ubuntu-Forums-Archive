---
title: "Latest Update"
date: 2006-12-21
forum: General Help
---

### Post by richardspirit on 2006-12-21
I just got the notifications for new updates to edgy and so I went ahead and installed them. It has been running now for over an hour and seems to be stuck in a loop trying to configure mono-gac...there seems to be an error that says there is no more space on device but the harddrive is far from full...

any help would be appreciated...

---

### Post by taurus on 2006-12-21
Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by richardspirit on 2006-12-21
> **taurus said:**
> Applications -> Accessories -> Terminal
```
df -h
```

should I end force end the update before running that?

---

### Post by taurus on 2006-12-21
Just open another terminal and look at your disk space situation first!

---

### Post by richardspirit on 2006-12-21
/dev/hda1             110G  9.4G   95G   9% /
varrun                126M  144K  125M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
procbususb             10M  104K  9.9M   2% /proc/bus/usb
udev                   10M  104K  9.9M   2% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   18M  108M  15% /lib/modules/2.6.17-10-386/volatile
/dev/scd0             4.1M  4.1M     0 100% /media/cdrecorder
/dev/sda1             994M  323M  671M  33% /media/JUMPDRIVE

---

### Post by richardspirit on 2006-12-21
> **richardspirit said:**
> /dev/hda1             110G  9.4G   95G   9% /
varrun                126M  144K  125M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
procbususb             10M  104K  9.9M   2% /proc/bus/usb
udev                   10M  104K  9.9M   2% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   18M  108M  15% /lib/modules/2.6.17-10-386/volatile
/dev/scd0             4.1M  4.1M     0 100% /media/cdrecorder
/dev/sda1             994M  323M  671M  33% /media/JUMPDRIVE

As you can see there is plenty of space on my harddrive as only 9% is being used

---

### Post by richardspirit on 2006-12-21
*bump*

Is anybody going to help me?

---

### Post by richardspirit on 2006-12-21
You know I started using Ubuntu partly because of the great help that I could get on these forums but lately it seems to be a waste of time....perhaps I would be better of with purchasing support with a different distro...at least when I ask for help I will get it....

---

