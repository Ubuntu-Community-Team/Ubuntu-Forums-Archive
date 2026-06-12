---
title: "Variable inside Bash Script - Not getting used (variable name used instead)"
date: 2021-04-23
forum: General Help
---

### Post by Alan5127 on 2021-04-23
Hi All,

I am trying to write a bash script using a variable to run some backups.

This is my script:

```
#!/bin/bash

vDateTime=$(date +%Y%m%d-%H%M)

echo $vDateTime

rsync -r -a -v -e 'ssh -p22' username@192.168.1.105:/var/ media/Data2/Backups/ServerXYZ/\$vDateTime/
```


When I run the script it correctly 'echos' the date and time, showing, say:  20210424-1527

However, the rsync creates a new directory called '$vDateTime' (rather than '20210421-1527') - both without the quotes.


I tried it on a single command line, and it works fine thus:

```
bash -l -c "var=$(date +%Y%m%d-%H%M); rsync -r -a -v -e 'ssh -p22' username@192.168.1.105:/var/ /media/Data2/Backups/ServerXYZ/\$var/
```


Once I get that working, I want to run a similar command, across multiple machines, and get all the backups to have the same folder name (YYYYMMDD-HHMM), and then run a zip on the backup folders.

I can just concatenate everything into one big 'bash -l -c ...' command, but I'd like to understand why the script is failing, and what I am missing.



Hope that makes sense - please ask me to clarify if not.

Thanks,

Alan.

---

### Post by HermanAB on 2021-04-24
Look into the use of the *export* keyword for variables.

---

### Post by Alan5127 on 2021-04-24
Thanks Herman.

Tried exporting the variable like this as per the bash man page, but it still fails:


```
#!/bin/bash

export vDateTime=$(date +%Y%m%d-%H%M)

echo $vDateTime

rsync -r -a -v -e 'ssh -p22' username@ServerX:/var/ /media/Data2/Backups/ServerX/\$vDateTime/

rsync -r -a -v -e 'ssh -p22' username@ServerY:/var/ /media/Data2/Backups/ServerY/\$vDateTime/


```


There's no immediately obvious reason why it is working for the echo command, but not for the rsyncs.


Alan.

---

### Post by Alan5127 on 2021-04-24
Found that the issue was actually escaping the variable name.

This works:

```
#!/bin/bash

export vDateTime=$(date +%Y%m%d-%H%M)

echo $vDateTime

rsync -r -a -v -e 'ssh -p22' username@ServerX:/var/ /media/Data2/Backups/ServerX/$vDateTime/

rsync -r -a -v -e 'ssh -p22' username@ServerY:/var/ /media/Data2/Backups/ServerY/$vDateTime/
```


Alan.

---

### Post by HermanAB on 2021-04-24
Beware of unbalanced quotes.

---

