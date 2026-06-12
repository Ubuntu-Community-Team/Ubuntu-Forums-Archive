---
title: "preferring IPv6"
date: 2020-05-16
forum: General Help
---

### Post by Skaperen on 2020-05-16
there is an option in the rsync command --ipv6 (or just -6) that the man pages says "prefers" IPv6.  so i tried it on a few hosts.  one of them did not have an AAAA record.  what happened is that rsync reported that host did not have an address and exited with status 10.  it did not fall back to IPv4 for that host.  my understanding of the word "prefer" is not to exclusively insist on it and exclude all else.  the man page shows no other option that could do this.

it would be nice if we had a genuine way to do this ... prefer IPv6 if it works (reasonably quickly) and fall back to IPv4 if IPv6 is not working for whatever reason ... and do this across the board for every application (at least for TCP and SCTP where success can be easily determined).

in the mean time, can someone tell me of a command line application that does this correctly (to be a nice tool to check IPv6 connectivity)?

---

