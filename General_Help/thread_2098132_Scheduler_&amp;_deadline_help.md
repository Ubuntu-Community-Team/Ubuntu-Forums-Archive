---
title: "Scheduler &amp; deadline help?"
date: 2012-12-25
forum: General Help
---

### Post by bilekbp on 2012-12-25
Hello, in order to tweak my Ubuntu 12.10 installation for my SSD I've been following some instructions that state that I should use deadline in scheduler. However, I don't understand how to determine if I'm currently using deadline or not.

I'm using:
```
cat /sys/block/sdb/queue/scheduler
```
Output:
noop [deadline] cfq 

What do the [] mean here? That I'm using it?

If I'm not, how do I edit /etc/rc.local to change this?

My /etc/rc.local:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

Thank you!

---

### Post by Cheesemill on 2012-12-25
Yes, you're using the deadline scheduler. The square brackets surround the option being used. For example I use bfq and my output is:
```
rob@arch:~$ cat /sys/block/sdb/queue/scheduler
noop deadline cfq [bfq]
```

---

### Post by bilekbp on 2012-12-25
Thank you very much!

---

