---
title: "Disable printing, or prevent the ability to print"
date: 2014-08-20
forum: General Help
---

### Post by skogdyret on 2014-08-20
This might seem odd, but is there a way where i can not permit my ubuntu system to use printers?

Reason is i live in a boarding like school where i can easely print stuff accidentally. And when I was browsing ... sites i almost accidentally hit CTRL + P and almost enter.

If I one time in the future accidentally print something i would have to run around like a maniac and ask people where the printer is and get there before anyone else...

---

### Post by sandyd on 2014-08-20
> **skogdyret said:**
> This might seem odd, but is there a way where i can not permit my ubuntu system to use printers?

Reason is i live in a boarding like school where i can easely print stuff accidentally. And when I was browsing ... sites i almost accidentally hit CTRL + P and almost enter.

If I one time in the future accidentally print something i would have to run around like a maniac and ask people where the printer is and get there before anyone else...

Try running
```

sudo service cups stop
sudo update-rc.d cups disable
```

That will disable Ubuntu's printing system (CUPS)

---

### Post by skogdyret on 2014-08-20
```
$ sudo update-rc.d cups disable
update-rc.d: warning:  start runlevel arguments (none) do not match cups Default-Start values (2 3 4 5)
update-rc.d: warning:  stop runlevel arguments (none) do not match cups Default-Stop values (1)
 System start/stop links for /etc/init.d/cups do not exist.

```

But i belive i got the cups service stopped, however, will this prevent the automatic installing of printers?

---

