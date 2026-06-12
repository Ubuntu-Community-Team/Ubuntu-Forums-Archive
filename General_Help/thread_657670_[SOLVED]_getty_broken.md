---
title: "[SOLVED] getty broken"
date: 2008-01-03
forum: General Help
---

### Post by Daniel15 on 2008-01-03
**Edit: Found the solution at [http://ubuntuforums.org/showthread.php?t=582962](http://ubuntuforums.org/showthread.php?t=582962), it's a known bug. Please lock/delete this topic :)**

Hi everyone,
 The tty terminals (CTRL+ALT+F1 to F6) appear to be not working properly on my sistem. If I switch to one, there's nothing on the screen, just a flashing cursor. /etc/event.d/tty1 to /etc/event.d/tty6 exist and seem to be fine, and "getty" seem to be running fine:
> 
daniel@daniel-laptop:~$ ps aux | grep getty
root      4735  0.0  0.0   1696   520 tty4     Ss+  11:17   0:00 /sbin/getty 38400 tty4
root      4736  0.0  0.0   1692   516 tty5     Ss+  11:17   0:00 /sbin/getty 38400 tty5
root      4738  0.0  0.0   1696   520 tty2     Ss+  11:17   0:00 /sbin/getty 38400 tty2
root      4739  0.0  0.0   1692   516 tty3     Ss+  11:17   0:00 /sbin/getty 38400 tty3
root      4740  0.0  0.0   1696   520 tty1     Ss+  11:17   0:00 /sbin/getty 38400 tty1
root      4741  0.0  0.0   1696   520 tty6     Ss+  11:17   0:00 /sbin/getty 38400 tty6
daniel   28902  0.0  0.0   2980   776 pts/0    R+   13:10   0:00 grep getty

Any idea what could cause the ttys to not work properly?

---

