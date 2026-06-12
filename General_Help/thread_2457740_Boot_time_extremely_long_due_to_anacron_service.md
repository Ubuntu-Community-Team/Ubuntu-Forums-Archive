---
title: "Boot time extremely long due to anacron service"
date: 2021-02-08
forum: General Help
---

### Post by kuza91 on 2021-02-08
Hello people,
i am actually running ubuntu 20.04 in dual boot on a MSI notebook.
The booting time some time doesn't takes to long, yet some time it takes ages and even on start the computer fail to load  immediately the internet browser or the terminal but needs additional time in order to start.
I tried to run :

```

systemd-analyze Startup finished in 4.102s (kernel) + 22min 24.238s (userspace) = 22min 28.340s 
graphical.target reached after 2min 19.268s in userspace

```

and in particular when i do :
```

systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.


graphical.target @2min 19.268s
&#9492;&#9472;multi-user.target @2min 19.268s
  &#9492;&#9472;anacron.service @22min 11.006s
    &#9492;&#9472;basic.target @29.445s
      &#9492;&#9472;sockets.target @29.445s
        &#9492;&#9472;snapd.socket @29.444s +640us
          &#9492;&#9472;sysinit.target @28.609s
            &#9492;&#9472;systemd-update-utmp.service @27.923s +684ms
              &#9492;&#9472;systemd-tmpfiles-setup.service @27.485s +383ms
                &#9492;&#9472;systemd-journal-flush.service @3.578s +23.904s
                  &#9492;&#9472;systemd-journald.service @2.881s +696ms
                    &#9492;&#9472;systemd-journald.socket @2.870s
                      &#9492;&#9472;system.slice @2.862s
                        &#9492;&#9472;-.slice @2.862s



```


it seems that the anacron service is the main cause of the slowness !

Any idea on how to solve the problem?
Thanks in advance

---

