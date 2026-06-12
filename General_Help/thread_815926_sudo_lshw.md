---
title: "sudo lshw"
date: 2008-06-02
forum: General Help
---

### Post by p.becks on 2008-06-02
Hello,

I use this script to get some system info in a text-file. (collect.sh)

#!/bin/bash
sudo lshw -C memory -C network -C display -C multimedia > /home/patrick/scripts/HARDWARE/collect.txt
#memory
cat /home/patrick/scripts/HARDWARE/collect.txt | grep -C1 slot..DIMM | sed -e '/--/d' -e '/serial:/d' -e 's/  //g'> /home/patrick/scripts/HARDWARE/mem4.txt
#video
cat /home/patrick/scripts/HARDWARE/collect.txt | grep -C2 *-display:0 | grep product | sed -e 's/product://g' -e 's/  //g'> /home/patrick/scripts/HARDWARE/video4.txt
#ethernet
cat /home/patrick/scripts/HARDWARE/collect.txt | grep [Nn]etwork | sed -e  '/\*-network/d' -e 's/product://g' -e '/description:/d' -e 's/  //g' > /home/patrick/scripts/HARDWARE/net5.txt
#audio
cat /home/patrick/scripts/HARDWARE/collect.txt | grep -C1 "Audio device" | grep product | sed -e 's/product://g' -e 's/  //g' > /home/patrick/scripts/HARDWARE/audio4.txt
exit

It used to work great (run from within Conky) see Conky config-file below

TEXT
${color yellow}${font Arial:size=10}
HARDWARE DETECTED:${execi 30 /home/patrick/scripts/HARDWARE/collect.sh}

But now i won´t work anymore. (i DOES work from the command-line though!)

I use Ubuntu 8.04 (fully updated) and Conky 1.51

Do you have an idea what is wrong?


(could it be a sudo-problem?)

---

### Post by p.becks on 2008-06-02
While i was typing the above message, i noticed that sudo lshw worked again within Conky. I have no clue why it does now. (i did sudo somthing else in the mean time)

---

### Post by geirha on 2008-06-02
When you use sudo it remembers your password for a while (15 min or so), which is probably why it suddenly worked after you used sudo for something else. It's possible you can make this work by replacing "sudo" with "gksudo" which will ask you for the password graphically instead of from the cli.

Another way might be to allow your user to run the lshw command without typing a password. You do that by running ```
sudo EDITOR=vim visudo
```
(replace vim with a different editor if you don't fancy vim)
and adding a line like the following to the end of the file:
```

*yourusername* ALL=NOPASSWD: /usr/bin/lshw

```

---

### Post by p.becks on 2008-06-02
THANKS YOU! (i think that did the trick)

---

