---
title: "DEBUG... when launching lubuntu-software-center from Terminal"
date: 2014-09-04
forum: General Help
---

### Post by TitoHL on 2014-09-04
Hi guys: 
I am learning to write scripts and found a slight problem when launching lubuntu-software-center from the terminal.
My script is:
```
#!/bin/bash
/usr/bin/lubuntu-software-center &
```
Lubuntu Software Center opens in a separate window, but I get this output in LXTerminal:
```
DEBUG 2014-09-04 20:31:37,269 __init__ 44 Opening config file
DEBUG 2014-09-04 20:31:37,309 __init__ 44 Opening config file
Reading package lists... Done
Building dependency tree      
Reading state information... Done
DEBUG 2014-09-04 20:31:38,807 __init__ 44 Opening config file

```
This does not happen with any other program, only lubuntu-software-center 
What does this mean?

---

