---
title: "GnuCash Crashes after Upgrade to 14.04"
date: 2014-08-09
forum: General Help
---

### Post by DomIncollingo on 2014-08-09
I updated my laptop from 13.04 to 13.10, and then from 13.10 to 14.04.  After the upgrade, GnuCash crashes when I try to launch it.  GnuCash worked fine when I was on 13.04.

I tried launching gnucash from the command line, but the only output was four warning GTK messages.

Then I tried **strace gnucash 2>&1 | tee cash** from the command line.  The output file (cash) contains about 308, 500 lines!  The last line is **+++ killed by SIGABRT +++**.  I grepped for the words error and fatal, but didn't find anything suspicious.

Can anyone give me some ideas on how to diagnose this problem?  Thanks very much!

Dom

---

