---
title: "Conky output to text file...."
date: 2020-09-23
forum: General Help
---

### Post by Furycd001 on 2020-09-23
HI guys.. I'm trying to pipe conky to a text file & I want it to only output once & not multiple times. I've tried using the command at the bottom along with changing the "update_interval" in my conky.conf to something like "22", but conky seems to write twice or sometimes more to the file. I've looked on google but can't seem to find anything useful, though I could have missed something. Anyway.. Any way I can make conky output only once to the file & not multiple times :? 

[Oh and here's my conky.conf....]("https://termbin.com/cmb3")

```
timeout 0.1s  conky -q -c /home/furycd001/Dots/conky/terminal.conf > /tmp/conkynote.txt
```

---

### Post by Furycd001 on 2020-09-23
Solved by changing "total_run_times" to 1 in my conf file....

---

