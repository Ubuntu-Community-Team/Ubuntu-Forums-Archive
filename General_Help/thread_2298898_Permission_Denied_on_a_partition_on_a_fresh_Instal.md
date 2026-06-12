---
title: "Permission Denied on a partition on a fresh Install."
date: 2015-10-14
forum: General Help
---

### Post by Ifaistos on 2015-10-14
Hello everyone :-)

I just installed latest ubuntu on laptop.
The Partitions are as shown on attached photo.
However I cannot access the "Data" folder, which is mounted under /home/evan/Data.
It has the lock on it as shown on the second attached photo.

Could someone please tell me what I did wrong and how to fix it?

I guess it has smt to do with permissions.

Thanks everyone !

---

### Post by yancek on 2015-10-14
Open a terminal and run the command below to find the owner:group and permissions.  If you don't understand that, post the output here.

```
ls -ld /home/evan/Data
```

---

### Post by Ifaistos on 2015-10-14
drwxr-xr-x 4 root root 4096 &#927;&#954;&#964;  14 19:05 /home/evan/Data

I guess it belongs to root?
What did I do wrong?
Can someone tell me? (For future reference..)

.. and how to fix it...  a GUI solution would be appreciated if possible.

---

### Post by Dennis N on 2015-10-14
You need to change owner/group of the mount point directory:

If your user name is evan,

```
sudo chown -R evan:evan /home/evan/Data
```

(this changes the owner and group of this directory and any files and directories inside)

---

### Post by Ifaistos on 2015-10-14
Thanks !! It worked !!

Could you please tell me what I needed to do while I was setting up the partitions to avoid this?

---

### Post by bab1 on 2015-10-14
> **Ifaistos said:**
> Thanks !! It worked !!

Could you please tell me what I needed to do while I was setting up the partitions to avoid this?
You did nothing wrong.  Root is the only user that can partition HDD's.  This is just one of the maintenance jobs you have to do when installing things.  Since youare the administrator you have sudo rights to ask root to finish the the task.

---

### Post by Ifaistos on 2015-10-14
Thank you Bab1 :-)

---

