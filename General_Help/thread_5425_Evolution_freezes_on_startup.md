---
title: "Evolution freezes on startup"
date: 2004-11-18
forum: General Help
---

### Post by paul.hendrick on 2004-11-18
Not sure why, but once i setup evo (with an exchange server for incoming mail) i cant start the program again without rebooting. this happens constantly. even when i killall evo processes, i still need to reboot.
i ran it from the terminal, and i get the below output. the "Invalid root" errors might be the problem, but even when rm'ing those ibex files, evo freezes on startup.
freezes = blank gtk window, no widgets being drawn etc.

any ideas?

```


(evolution-2.0:6574): camel-WARNING **: Invalid root: '/home/paul/.evolution/mai l/local/Drafts.ibex.index'

(evolution-2.0:6574): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution-2.0:6574): camel-WARNING **: block size: 1024 (1024) OK

(evolution-2.0:6574): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution-2.0:6574): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution-2.0:6574): camel-WARNING **: flags: unSYNC

(evolution-2.0:6574): camel-WARNING **: Invalid root: '/home/paul/.evolution/mai l/local/Outbox.ibex.index'

(evolution-2.0:6574): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution-2.0:6574): camel-WARNING **: block size: 1024 (1024) OK

(evolution-2.0:6574): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution-2.0:6574): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution-2.0:6574): camel-WARNING **: flags: unSYNC

(evolution-2.0:6574): camel-WARNING **: Invalid root: '/home/paul/.evolution/mai l/local/Sent.ibex.index'

(evolution-2.0:6574): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution-2.0:6574): camel-WARNING **: block size: 1024 (1024) OK

(evolution-2.0:6574): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution-2.0:6574): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution-2.0:6574): camel-WARNING **: flags: unSYNC



```

---

