---
title: "Swapfile Prioty"
date: 2020-05-03
forum: General Help
---

### Post by sana4va on 2020-05-03
[COLOR=#ff0000]Should I change the Priority of my swapfile? [/COLOR]

jc@jc-OptiPlex-GX620:~$ Sudo Swapon --show
[sudo] password for JC: 
NAME      TYPE SIZE USED PRIO
[COLOR=#ff0000]/swapfile file  25G 167M   -2
[/COLOR]
As you can see. I do not have much Ram. I plan to remedy that issue  soon. In the meantime, I increased the swapfile space enormously.

jc@jc-OptiPlex-GX620:~$ free -m
              total        used        free      shared  buff/cache   available
[COLOR=#ff0000]Mem:           3486        2082         707         227         697        1023
Swap:         25599         164       25435[/COLOR]

Thank you In advance

---

### Post by CelticWarrior on 2020-05-03
Welcome.

SWAP, be it a swapfile or a swap partition, is NO replacement for RAM. 25GB of swapfile is nothing more than a huge waste of space.
And if you're using a Dell Optiplex GX620 with 4GB RAM it's alrerady maxed out.
In summary, you need to adjust your workload and expectations accordingly.

---

### Post by HermanAB on 2020-05-04
For everything you never wanted to know about swap, read the swapon man page:
$ man swapon

---

