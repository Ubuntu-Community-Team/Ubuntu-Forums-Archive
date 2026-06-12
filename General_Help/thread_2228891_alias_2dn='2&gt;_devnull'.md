---
title: "alias 2dn='2&gt; /dev/null'"
date: 2014-06-10
forum: General Help
---

### Post by marbew on 2014-06-10
Hello guys, after i created my new alias 
alias 2dn='2> /dev/null'
I would like to use it for instance with this command: grep -r -l "kalip" /etc/* 2dn
the answer by bash is:

ledeer@android-recc3es50fa20:~$ sudo grep -r -l "kalip" /etc/* 2dn
grep: /etc/blkid.tab: No such file or directory
grep: 2dn: No such file or directory

How is possible to let see an alias to grep after all options?

---

