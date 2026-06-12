---
title: "duplicity - how not to fill up remote backup disk?"
date: 2013-01-31
forum: General Help
---

### Post by luislupe on 2013-01-31
Hi,

I've set up a laptop to backup home folder to a nfs remote share (in LAN) via duplicity.

The problem I'm encountering is that duplicity fills the remote disk with newer data.  It only deletes older backup data when the disk is full.

As the disk is used for many purposes, so I need to configure duplicity to delete data older than x weeks, but don't find any option in the gui.

How can I solve this problem?
Ubuntu 12.04 LTS.

---

