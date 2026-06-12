---
title: "chrom* browser lag on desktop not laptop"
date: 2020-02-08
forum: General Help
---

### Post by maclenin on 2020-02-08
(Latest versions of) chromium and chrome browsers both run with significant lag on a desktop but without issue on a laptop.

I am running xubuntu 18.04.4 on both machines.

Desktop model: self-build
Desktop cpu (via lshw): Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz

Laptop model: acer swift 1 sf114-32
Laptop cpu (via lshw): Intel(R) Pentium(R) Silver N5000 CPU @ 1.10GHz

For example: via nyt.com - as video advertisements load - desktop browsers will lag for at least 5 seconds as I scroll, while laptop browsers scroll smoothly.

Disabling hardware acceleration does not resolve the issue.

Thanks for any guidance. 

NB: Firefox has no issues on either desktop or laptop.

---

### Post by Dennis N on 2020-02-08
I've also seen the momentary freeze when scrolling through some web sites with Chromium. I attribute this to some fault in the Chromium snap package - the corresponding non-snap version used in other distros seems O.K. Firefox's snap package doesn't have this problem.

My suggestion is to use Firefox instead until Chromium improves.

---

### Post by maclenin on 2020-02-09
Thanks for the note.

Historically, relying on Firefox is what I have done and continue to do (not only) in response to Chrom* misbehavior.

However, what makes this time around a bit different is (my noticing) the dramatic difference in Chrom* performance on desktop vs laptop, as described.

One works while the other doesn't.

Trying to understand "why".

Cheers!

---

### Post by Holger_Gehrke on 2020-02-09
According to ark.intel.com the N5000 has 4 cores and a variable clock at up to 2.7 GHz while the core 2 has 2 cores and a fixed clock at 3 GHz. So for a multi-threaded or multiprocess program the n5000 should be faster - more cores at similar clock frequency. Also the N5000 has newer SSE instruction set extensions. If chrome uses those on systems where they are available, it might also give the N5000 another advantage.

Holger

---

### Post by maclenin on 2020-02-12
I hear you re: cpu advantage.

I guess my reply is I would expect those advantages (N5000 over E8400) to be more applicable if we were talking CAD rendering and not "basic" browser performance.

All things considered, I keep wondering whether there's something else at play?

Historically, Chrom* updates (1 to 2 cycles) have resolved past browser performance issues. Recent updates (2 to 3 cycles) have yet to do the same (for my desktop).

Flash seems to play a role - though non-flash video and other rendering features (scrolling through online spreadsheets etc) are also impacted.

Am I simply being updated away from my "current" cpu?

Thanks for the insight!

NB: The issue first surfaced for me (on the desktop / E8400) after updates to [chrom* version 79]("https://ubuntuforums.org/showthread.php?t=2433276&p=13920218#post13920218").

---

### Post by maclenin on 2020-02-24
Holger!

I think you were right - it must have been the cpu.

All now up and newly cruising via: Intel(R) Core(TM) i5-9600K CPU @ 3.70GHz

Ye olde E8400 had run, and, essentially, without issue - for 10+ years - though, felt it was time for a refresh.

Your comments fueled the fire.

Cheers!

---

