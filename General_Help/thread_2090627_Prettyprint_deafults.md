---
title: "Prettyprint deafults"
date: 2012-12-03
forum: General Help
---

### Post by t2nator on 2012-12-03
How could i configure my server to print using the prettyprint option without having to type "lp -o prettyprint file.txt"? In other words, I want to be able to type "lp fle.txt" and the header prints automatically..

---

### Post by ohnonot on 2012-12-03
i don't understand "my server" but you can always put a shell script called lp in ~/bin 
-containing this:
/usr/bin/(or wherever that prog is)lp -o prettyprint $1

---

