---
title: "Love framework problem"
date: 2017-04-21
forum: General Help
---

### Post by erzis on 2017-04-21
Hello,
I installed love framework yesterday. When I typed 'love' after that it started, but today when I type love this happens:

[HTML]
root@erzis:/home/erzis# love --version
LOVE 0.10.2 (Super Toast)
root@erzis:/home/erzis# love
Error: Could not initialize SDL video subsystem (No available displays)
stack traceback:
    [C]: at 0x7f0d46c9af20
    [C]: in function 'require'
    [string "boot.lua"]:375: in function <[string "boot.lua"]:275>
    [C]: in function 'xpcall'
[/HTML]

Any ideas? I use Ubuntu 16.04

---

### Post by yetimon_64 on 2017-04-21
> Error: Could not initialize SDL video subsystem (No available displays)
Does the application need to be run as root? How did you run it the first time, as your normal user or as root ?

Edit: just noted the solved tag on the thread; do you still have a problem here or is the solved tag wrong ?

---

