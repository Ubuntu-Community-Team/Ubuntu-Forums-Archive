---
title: "gnucash crashing since upgrading ubuntu 13.10 to 14.04"
date: 2014-05-07
forum: General Help
---

### Post by andy.stevens on 2014-05-07
Hi,

I allowed my laptop to do the distribution upgrade to 14.04 a couple of days ago (from 13.10), and since then GnuCash crashes on opening my data file.  It shows the splash screen with the various progress bars, and even gets as far as displaying the Scheduled Transactions that have come due since the last run, but then crashes just as I'm expecting the main window to be displayed.

Running it from the shell, I see the following output:

```
Found Finance::Quote version 1.18
In ice-9/boot-9.scm:
 157: 19 [catch #t #<catch-closure a041c20> ...]
In unknown file:
   ?: 18 [apply-smob/1 #<catch-closure a041c20>]
In ice-9/boot-9.scm:
 157: 17 [catch #t #<catch-closure a331420> #<catch-closure a331410> #f]
In unknown file:
   ?: 16 [apply-smob/1 #<catch-closure a331420>]
In ice-9/boot-9.scm:
 171: 15 [with-throw-handler #t #<catch-closure a3313a0> #<catch-closure a331380>]
In unknown file:
   ?: 14 [apply-smob/1 #<catch-closure a3313a0>]
   ?: 13 [call-with-input-string "(gnc:report-run 1)" ...]
In ice-9/boot-9.scm:
2320: 12 [save-module-excursion #<procedure a5efb88 at ice-9/eval-string.scm:65:9 ()>]
In ice-9/eval-string.scm:
  44: 11 [read-and-eval #<input: string a575bb8> #:lang ...]
  37: 10 [lp (gnc:report-run 1)]
In report.scm:
 766: 9 [gnc:report-run 1]
In ice-9/boot-9.scm:
 157: 8 [catch ignore #<procedure a5efa80 at gnucash/main.scm:112:4 ()> ...]
In unknown file:
   ?: 7 [lazy-catch #t #<procedure a5efa50 at gnucash/main.scm:114:18 ()> ...]
In ice-9/boot-9.scm:
 171: 6 [with-throw-handler #t #<catch-closure a331110> #<catch-closure a3310f0>]
In unknown file:
   ?: 5 [apply-smob/1 #<catch-closure a331110>]
In report.scm:
 770: 4 [#<procedure a5efa98 at report.scm:767:5 ()>]
 749: 3 [gnc:report-render-html # #t]
In html-document.scm:
 196: 2 [gnc:html-document-render # #t]
In ice-9/boot-9.scm:
 102: 1 [#<procedure a9b70a0 at ice-9/boot-9.scm:97:6 (thrown-k . args)> vm-error ...]
In unknown file:
   ?: 0 [apply-smob/1 #<catch-closure a3310f0> vm-error ...]
Aborted (core dumped)
```

Getting it to create a New file starts up without problem, it's only when I try to open my existing data file that it's crashing.  Any suggestions how I might get it working again, other than reinstalling the older distribution?


Andy.

---

### Post by savoym on 2014-05-24
Hi Andy, just curious but did you ever figure out what the problem was and whether you got Gnucash to work again?  I just upgraded my laptop as well to Ubuntu 14.04 from 13.10 and now I'm experiencing the same issue with Gnucash.   Thanks

---

### Post by DomIncollingo on 2014-08-09
I just updated to 14.04, and am also having this problem.  Has anyone found a solution yet?  Thanks.

Dom

---

### Post by DomIncollingo on 2014-08-09
Looks like the problem might be documented in this bug: [https://bugs.launchpad.net/ubuntu/+source/gnucash/+bug/1310650]("https://bugs.launchpad.net/ubuntu/+source/gnucash/+bug/1310650")

---

