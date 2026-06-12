---
title: "clamavd crashing"
date: 2007-12-21
forum: General Help
---

### Post by ullal on 2007-12-21
I have installed and used exim4+clamav since Dec. 17. Everything worked well. Today I installed and configured in addition greylistd. All of a sudden clamavd has started crashing. The following log entries in syslog don't tell me anything:

Dec 21 17:27:49 ullserv kernel: [ 9106.610972] clamd[6519]: segfault at 000000000060bfff rip 00002b28bae72e05 rsp 00000000407fb5b0 error 4
Dec 21 18:47:53 ullserv kernel: [13910.032993] clamd[7231]: segfault at 000000000060bfff rip 00002aea56403e05 rsp 00000000407fb560 error 4
Dec 21 19:55:32 ullserv kernel: [17968.817501] clamd[10151]: segfault at 000000000060bfff rip 00002b9913028e05 rsp 00000000407fb560 error 4
Dec 21 20:03:39 ullserv kernel: [18455.109751] clamd[11104]: segfault at 000000000060bfff rip 00002b65752eee05 rsp 00000000407fb560 error 4
Dec 21 20:07:45 ullserv kernel: [18701.714188] clamd[12004]: segfault at 000000000060bfff rip 00002ba157c29e05 rsp 00000000407fb560 error 4
Dec 21 20:15:56 ullserv kernel: [19192.662454] clamd[13148]: segfault at 000000000060bfff rip 00002af995d05e05 rsp 00000000407fb560 error 4
Dec 21 20:22:34 ullserv kernel: [19590.837331] clamd[13805]: segfault at 000000000060bfff rip 00002b8d0bed5e05 rsp 00000000407fb560 error 4
Dec 21 20:24:07 ullserv kernel: [19683.542761] clamd[14404]: segfault at 000000000060bfff rip 00002ab07d584e05 rsp 00000000407fb560 error 4
Dec 21 20:44:33 ullserv kernel: [  107.078128] clamd[4592]: segfault at 000000000060bfff rip 00002ad5fb479e05 rsp 00000000407fb560 error 4
Dec 21 21:00:54 ullserv kernel: [ 1087.806265] clamd[6128]: segfault at 000000000060bfff rip 00002b1fb01c8e05 rsp 00000000407fb560 error 4

Can someone tell me what is happening?

---

