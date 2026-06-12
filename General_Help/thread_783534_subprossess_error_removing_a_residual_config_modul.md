---
title: "subprossess error removing a residual config module"
date: 2008-05-05
forum: General Help
---

### Post by nowshining on 2008-05-05
since I do use the kernel sources from kernel.org I decided after a few months that I didn't need the Gutsy kernel taking up space on the HD, and so i'lll just keep TWO around - the active kernel + one older version of the kernel and so I removed kernel 2.6.xx of the Gutsy kerenl, but seeing a residual config section appear showing residual config file and I removed them one by one until this one won't go away (linux-ubuntu-modules-2.6.22-14-generic) and gives the following:

```
E: linux-ubuntu-modules-2.6.22-14-generic: subprocess post-removal script returned error exit status 1
```

My knowledge is at a sort of dead-end on how to remove this ol' config/residual file using synaptic.

.................

The solution was to remove the following, and then it removed successfully:

sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.22-14-generic.postrm
sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.22-14-generic.list

---

