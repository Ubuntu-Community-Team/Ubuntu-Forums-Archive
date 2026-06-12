---
title: "Checkpointing and restoring a process with crtools - should it work?"
date: 2015-10-11
forum: General Help
---

### Post by interglossa on 2015-10-11
I wanted to checkpoint (dump) a process and restore it later (presumably after a reboot) and discovered that this functionality was added with the checkpoint-restore tools in the crtools package which is presented as a single utility.

I tried
  crtools dump -t 3916
  Error (ptrace.c:75): Unseizeable non-zombie 3916 found, state S
and assumed the user needed permissions I didn't have.  Then I tried

  sudo crtools dump -t 3916
  Can't open self pagemapError (parasite-syscall.c:257): Parasite exited with 1
  Error (parasite-syscall.c:577): Dumping pages failed with 1
  Error (cr-dump.c:1506): Can't dump pages (pid: 3916) with parasite

Has anyone succeeded in getting this to work? (Running ubuntu 14.04)

---

