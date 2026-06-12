---
title: "Critical-chain: What should I do?"
date: 2022-05-18
forum: General Help
---

### Post by wyattwhiteeagle on 2022-05-18
Are critical-chains good or bad?
Why are some entries colored Red?
What should I do?

```
$ systemd-analyze critical-chain
```
```

The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.


graphical.target @21.262s
&#9492;&#9472;multi-user.target @21.261s
  &#9492;&#9472;cups-browsed.service @21.260s
Red &#9492;&#9472;cups.service @18.169s +3.081s
      &#9492;&#9472;network.target @18.082s
    Red &#9492;&#9472;NetworkManager.service @14.350s +3.728s
          &#9492;&#9472;dbus.service @14.344s
            &#9492;&#9472;basic.target @14.137s
              &#9492;&#9472;sockets.target @14.137s
                &#9492;&#9472;uuidd.socket @14.137s
                  &#9492;&#9472;sysinit.target @13.988s
                Red &#9492;&#9472;systemd-timesyncd.service @13.617s +370ms
                  Red &#9492;&#9472;systemd-tmpfiles-setup.service @12.901s +631ms
                    Red &#9492;&#9472;systemd-journal-flush.service @4.366s +8.530s
                      Red &#9492;&#9472;systemd-journald.service @3.714s +650ms
                            &#9492;&#9472;systemd-journald.socket @3.693s
                              &#9492;&#9472;system.slice @3.667s
                                &#9492;&#9472;-.slice @3.667s

```

---

### Post by #&amp;thj^% on 2022-05-18
> **wyattwhiteeagle said:**
> Are critical-chains good or bad?
Why are some entries colored Red?
What should I do?


Nothing, The red just highlights entries that have a +?ms value after the @.... As per the systemd-analyze manual page:
>  systemd-analyze critical-chain [UNIT...]  prints a tree of the
   time-critical chain of units (for each of the specified UNITs or for the
   default target otherwise). The time after the unit is active or started
   is printed after the "@" character. The time the unit takes to start is
   printed after the "+" character. Note that the output might be misleading
   as the initialization of one service might depend on socket activation
   and because of the parallel execution of units.
So it just highlights units that actually take time to start, like real services (cups.service,NetworkManager.service ...) as opposite to simple targets that are just met and don't "start".

---

