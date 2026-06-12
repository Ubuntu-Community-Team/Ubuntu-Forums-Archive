---
title: "Troubleshooting a Segmentation Fault"
date: 2017-01-24
forum: General Help
---

### Post by andrew.hull on 2017-01-24
I am trying to run a program called GridEx which depends on OpenCASCADE. After setup, I receive a segmentation fault when trying to run the program.

Ubuntu Version: Ubuntu 16.04.1

I believe the issue may reside in a bad directory path or its inability to find a correct file; however, I am having trouble determining the source of the segfault. I have run 'strace' to begin trouble shooting. I have attached the output of strace. [ATTACH]273359[/ATTACH]
Or see here: [http://pastebin.com/JMirL6Fc](http://pastebin.com/JMirL6Fc)

I have also attempted to run gdb. I have received the following error:

[ATTACH=CONFIG]273358[/ATTACH]


Any hints at the source of the segfault?! I have been troubleshooting for weeks and have had no luck.

Let me know if any further information about my system or the programs may help debug my issue.

Thank You!

---

### Post by dragonfly41 on 2017-01-24
I can remember trying to debug a segmentation fault and found this very old thread helpful to get traceback.

[https://bugs.launchpad.net/bzr-gtk/+bug/923824](https://bugs.launchpad.net/bzr-gtk/+bug/923824)

this is just an idea and may not be relevant to your fault but it helped me (see post #1 in above thread).

[COLOR=#333333][FONT=monospace]> I advise to temporarily modify /usr/lib/python2.7/dist-packages/gobject/constants.py to say[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]raise ImportError("no static plz")[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]somewhere at the top, then you will get a proper backtrace and can easily identify the culprit.[/FONT][/COLOR]

---

