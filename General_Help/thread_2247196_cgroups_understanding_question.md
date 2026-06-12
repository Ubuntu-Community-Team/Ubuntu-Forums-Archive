---
title: "cgroups understanding question"
date: 2014-10-06
forum: General Help
---

### Post by SeaKing on 2014-10-06
Hey,

I'm currently take a look at cgroups and there is a question about cpu.shares (and blkio.weight):

If I mount the cgroups file system I get the following preconfigured values:
cpu.shares 1024
blkio.weight 1000
tasks all currently running PIDs

If I create 2 subgroups: group1 and group2 and give them the following values:
group1:
cpu.shares 1024
blkio.weight 1000
tasks some PIDs

group2:
cpu.shares 2048
blkio.weight 500
tasks some PIDs

Now the question is: Who are the ressources shared?
cpu: 25% System, 25% group1, 50% group2
or
cpu: 100% System, 25% group1, 70% group2

blkio: ~40% System, ~40% group1, ~20% group2
or
blkio: 100% System, 66% group1, 33% group2

---

