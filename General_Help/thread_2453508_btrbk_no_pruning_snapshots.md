---
title: "btrbk no pruning snapshots"
date: 2020-11-11
forum: General Help
---

### Post by LewisTM on 2020-11-11
Hi everyone,

I've been using btrbk for a while to create btrfs snapshots and back them up to external drives. Creation and transfer work fine by executing [FONT=Courier New]btrbk run [/FONT]as a cron job. However, no matter how I configure things, I can't get the program to delete snapshots according to any preservation policy.

I'll spare you my complex setup and focus on a test case using a minimal config. 

My test btrbk.conf file contains:
```
volume /btrfs/homedrive
 subvolume @test
   snapshot_dir            snaptest
   snapshot_preserve       1m 
```
 
I then run [FONT=Courier New]btrbrk run[/FONT] repeatedly as root. This creates a bunch of snapshots in /btrfs/homedrive/snaptest (e.g., "@test.20201111", "@test.20201111_1" and so on sequentially). According to the policy, btrbk should preserve a single monthly snapshot for 1 month, meaning that any other snapshot that was created should be cleaned up at every run. Yet they all remain untouched, no error is reported; it just decides to retain all snapshots not matter what.

I'm obviously missing something. Any guru out there experienced with btrbk?

---

### Post by LewisTM on 2020-11-15
Turns out it needed to explicitly state:
```
snapshot_preserve_min      latest
```
in the config. If not specified, the value defaults to "all" meaning that all snapshots are kept and preservation policies are not applied.
Thanks to btrbk author for the tip!

---

