---
title: "Monitor read/writes by application (similar to top; not like lsof)"
date: 2007-09-02
forum: General Help
---

### Post by kung fu buntu on 2007-09-02
I would like to know if there is any application that allows monitoring the system in terms of hard disk drive usage.
With **top** it's possible to monitor applications and check how much CPU and RAM they are using. I would like a similar tool that would allow me to sort applications in terms of disk usage. The purpose is to find out what the heck is chocking my system every now and then.
AFAIK this isn't possible with lsof as it's used to monitor open file handles and not the number of bytes read and written.

This kind of feature was almost possible in windows because the taskmanager had a field with the total number of bytes read and written. So if the application's field was changing too fast you would know that it was dumping to the HDD.
I'm surprised Linux doesn't have anything better... heck... doesn't have anything.

Thanks!

---

### Post by cwaldbieser on 2007-09-03
> **kung fu buntu said:**
> I would like to know if there is any application that allows monitoring the system in terms of hard disk drive usage.
With **top** it's possible to monitor applications and check how much CPU and RAM they are using. I would like a similar tool that would allow me to sort applications in terms of disk usage. The purpose is to find out what the heck is chocking my system every now and then.
AFAIK this isn't possible with lsof as it's used to monitor open file handles and not the number of bytes read and written.

This kind of feature was almost possible in windows because the taskmanager had a field with the total number of bytes read and written. So if the application's field was changing too fast you would know that it was dumping to the HDD.
I'm surprised Linux doesn't have anything better... heck... doesn't have anything.

Thanks!

atop does this, but it requires a kernel patch.
The sysstat tool pidstat seems to do this-- I am not sure if the version of sysstat that includes pidstat is in the repos.  On my Dapper system, it is not.  The home page is [http://perso.orange.fr/sebastien.godard/documentation.html]("http://perso.orange.fr/sebastien.godard/documentation.html")

---

