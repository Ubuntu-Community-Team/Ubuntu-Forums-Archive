---
title: "How could i write a script to do this?"
date: 2016-07-18
forum: General Help
---

### Post by ahawkua on 2016-07-18
/Documents$ cd bluegriffon/
ahawkua@ahawkua-Aspire-XC-703G:~/Documents/bluegriffon$ sudo ./bluegriffon

---

### Post by &amp;KyT$0P# on 2016-07-18
Pretty much all you have to do is literally just paste those two lines into a text file. (Shell scripting can be nice that way :D )
Your text file would look like this (assuming your shell is bash):
```
#!/bin/bash
cd ~/Documents/bluegriffon/
sudo ./bluegriffon
```

Then just set that as owner-executable ([FONT=Courier New]chmod o+x <file>[/FONT])

That being said why are you running [BlueGriffon]("http://bluegriffon.org/") as root?

---

