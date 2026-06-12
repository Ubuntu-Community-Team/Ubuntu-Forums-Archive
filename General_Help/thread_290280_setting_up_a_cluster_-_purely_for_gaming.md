---
title: "setting up a cluster - purely for gaming"
date: 2006-11-01
forum: General Help
---

### Post by Jacks0n on 2006-11-01
Hi! I'm part of quite a large family, and I'm usually the one that does all the upgrades, or buys new computers for people. Anyway, I've been left with a few computers around the place over the years, and normally just pluck out the hard-drive to use as backup, and the box is left there collecting dust.

But I had an idea .. why not set-up a cluster for gaming? Not for running a gaming server, but a client. Because basically all of the latest cpu/gpu intensive games only run on windows, I'm thinking of setting up a virtual machine. what I've got to work with is...

      CPU | GPU
1. P4 3.4 ghz with ht / Ati x800
2. Core Duo 2.0 ghz / Ati x1600
3. ~1.4 ghz P4 / Geforce 4 mx something.. I think 400.
4. ~1.8 ghz P4 / radeon r200

3 using 10/100 lan cards, with 1 gigabit. and I have a 10/100 switch.

First off, I don't know too much about clustering.. I did a few searches, but no one seems to have tried this before that I know of (clustering purely for gaming). So I was wondering if it's possible to set-up a cluster with ubuntu, and if not, what linux distro do you think I should use for this?

-Thanks, Jackson

P.s. I realize the overhead of running a vm, and could likely be just as fast as 1 computer alone. I'm mainly just doing this out of interest...

---

### Post by Jussi Kukkonen on 2006-11-01
Realtime games are an area clusters will probably do very badly in (unless the games are designed for that architecture, but that would ruin the point, wouldn't it?). Games need a low latency, high bandwidth connection between memory, cpu and gpu; preferably with caches in every possible place. The result of each calculation that is done is going to be needed very soon, in milliseconds, so there's not much that can be parallelized -- this is a situation that's pretty hard to help by clustering...

---

