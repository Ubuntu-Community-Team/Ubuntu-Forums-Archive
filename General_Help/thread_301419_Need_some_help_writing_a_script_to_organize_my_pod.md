---
title: "Need some help writing a script to organize my podcasts"
date: 2006-11-17
forum: General Help
---

### Post by benanzo on 2006-11-17
need help with bash script to manage podcasts
I am trying to output the contents of my podcast folder to a logfile containing the full paths to each podcast file on their own lines. I am having trouble when there are multiple mp3s in a single directory.

My current script:
```
#!/bin/bash
# output engadget contents to logfile

# Variables
ENGADGET='/home/ben/podcasts/engadget'
LOG='/home/ben/podcasts/podcasts.log'
#

cd $ENGADGET
echo $(pwd)/$(ls -1 | grep .mp3) >> $LOG
```

This works if there is only 1 mp3 in the folder.

/home/ben/podcasts/engadget/engadget1.mp3

but if there are multiple files it does this:

/home/ben/podcasts/engadget/engadget1.mp3 engadget2.mp3

I want it to do this:

/home/ben/podcasts/engadget/engadget1.mp3
/home/ben/podcasts/engadget/engadget2.mp3


it doesn't help me if I want another script to be able to manage those files directly just by checking the logfile for the files to manage rather than checking each individual directory for the files.

I really appreciate any help. Thank You!

---

### Post by marcog on 2006-11-17
Change

```
echo $(pwd)/$(ls -1 | grep .mp3) >> $LOG
```

to

```
for i in $(ls | grep .mp3); do echo $(pwd)/$i; done > $LOG
```

---

### Post by benanzo on 2006-11-17
Great help, Thank you!

---

