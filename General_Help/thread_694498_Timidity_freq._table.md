---
title: "Timidity freq. table"
date: 2008-02-12
forum: General Help
---

### Post by rosros-3 on 2008-02-12
I'm trying to tune a midi file with a table of frequencies for the 128
midi notes generated with scala (test.tbl: (128 integers, each line with
the frequency of a note in Hz*1000) using the -Z option.
I use TiMidity++ version 2.13.2, in Ubuntu 7.10 gutsy, since it is used
also as an ALSA sequencer client, I first killed that process.

However >timidity -Z test.tbl mymidi.mid
does not work (nor "timidity -Ztest.tbl mymidi.mid", "timidity
--freq-table=test.tbl mymidi.mid").

What is wrong?

---

