---
title: "crontab -e problem"
date: 2012-11-01
forum: General Help
---

### Post by dolbyater on 2012-11-01
go to terminal and do 
**crontab -e**

[IMG]http://i.imgur.com/aFg8C.jpg[/IMG]

**question:**
1) if i want to add scheduler cron (as below) in crontab file,
 [HTML]*/1 * * * * /usr/bin/wget -O - -q "http://example.com/scheduler/cron"[/HTML]is that add below script below?
```
# m h dom mon dow command
```2) how to save the crontab file?
i try press "vi" then press "escape", but nothing happen.

---

### Post by rnerwein on 2012-11-02
> **dolbyater said:**
> go to terminal and do 
**crontab -e**

[IMG]http://i.imgur.com/aFg8C.jpg[/IMG]

**question:**
1) if i want to add scheduler cron (as below) in crontab file,
 [HTML]*/1 * * * * /usr/bin/wget -O - -q "http://example.com/scheduler/cron"[/HTML]is that add below script below?
```
# m h dom mon dow command
```2) how to save the crontab file?
i try press "vi" then press "escape", but nothing happen.

hi
i don't know the shown editor but i use in my .bashrc:
EDITOR=vi
VISUAL=vi
export EDITOR
export VISUAL

then cron is using "vi" as his editor
if these varibles are empty cron will ask you:

Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/vim.tiny

Choose 1-3 [2]: 2

you are working with nano.
to exit type: CTRL+x

---

