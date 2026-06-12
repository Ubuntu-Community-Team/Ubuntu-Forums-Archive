---
title: "Sunbird 0.2 GTK2.0+XFT - Seg Fault"
date: 2005-05-04
forum: General Help
---

### Post by usererror on 2005-05-04
I am having a problem running Sunbird.

i get the following error:

[b]***:/usr/local/mozilla/sunbird$ ./sunbird
./run-mozilla.sh: line 131:  7985 Segmentation fault      "$prog" ${1+"$@"}[/b]

when i go to line 131 of the run-mozilla.sh file it is a function that looks like it's supposed to start the program...

would this be happening because i am missing a dependancy?

thanks in advance!

---

### Post by markr on 2005-05-04
Had similar problems myself.

I think it is a 'feature' of sunbird.

I got around this by issuing the command 'sunbird -calendar' instead of just 'sunbird'

Mark.

---

### Post by usererror on 2005-05-04
I have tried that also, and this time the seg fault is slightly different. =(

[b]>:/usr/local/mozilla/sunbird$ ./sunbird -calander
./run-mozilla.sh: line 131: 11876 Segmentation fault      "$prog" ${1+"$@"}[/b]

I also use Firefox 1.0.3 and Thunderbird 1.0.2 and those work fine.  I installed those directly from Mozilla's download sources.

any other ideas?

thanks for your reply!

---

