---
title: "[SOLVED] Can't login to Dapper - where can I look at the log?"
date: 2007-12-13
forum: General Help
---

### Post by willz06jw on 2007-12-13
Hey guys let me start by saying thanks for the help,

I went back to an Ubuntu computer I haven't used in a couple months and it won't login.  It is not the username and password, because of the following:

If I use the wrong username and password it says incorrect username or password;  If I use the correct username and password it flickers and then returns me to the ubuntu login screen.

Where are the log files so I can see what it happening, or if there are any ideas thoes are much appreciated!

Thanks,
Will

---

### Post by xeth_delta on 2007-12-13
You can try having a look at **/var/log/Xorg.0.log**, **/var/log/messages**, and of course, issuing a **dmesg**. Since it seems you have problems with the X server, you will most likely find information on Xorg.0.log. Also, check that your system and home partitions are not full.

Xeth

---

### Post by willz06jw on 2007-12-13
how do I check the hard drive space at the command prompt?

Thanks,
Will

---

### Post by Butthead on 2007-12-13
Hmm, "df" (without the quotes?). :confused:

---

### Post by xeth_delta on 2007-12-13
> **willz06jw said:**
> how do I check the hard drive space at the command prompt?

Thanks,
Will

```
df -h
```

Remember to first make sure the partition is mounted before checking the space.

---

### Post by willz06jw on 2007-12-13
He was right, my hard drive was 100% full.  The command prompt command I used to find the diskspace was df.

again, thanks for your help,
Will

---

### Post by xeth_delta on 2007-12-13
> **willz06jw said:**
> He was right, my hard drive was 100% full.  The command prompt command I used to find the diskspace was df.

again, thanks for your help,
Will

You're welcome! Good luck!

---

