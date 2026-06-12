---
title: "using hardware to optimize drive write speeds"
date: 2007-10-01
forum: General Help
---

### Post by tedder on 2007-10-01
Okay, here's the issue. I have a couple of SATA drives in my machine. I'm using an application that causes about 4 streams of data to be written to drive #2 at the same time, and I want to read 1-2 out at this same time too.

It's just a 7200rpm SATA drive. It can't handle the bandwidth caused by these big data streams that want to write out across the disk.

So, I know two decent options:
1. RAID (with striping). This means I will either have 4 drives in a 1+0 form, or two in a RAID 1 format and hope nothing happens.
2. Use a 'cache' for writing this data. I can use a 15k or 10k drive for the writes, and read off the slower drive. That means these need to be connected in some fashion- perhaps writes go in to the fast drive but the files don't appear until they streamed in to the slower drive. Basically using the fast drive as a buffer.

If there is some way to do this buffer/caching transparent of software (ie configured in Linux, but not through applications), I could save myself a big headache, plus the expense and space needed for redundant RAID disks.

Could LVM handle this sort of thing? Anything else? Hell, if I don't find a decent solution, I may write some quick perl to move completed files from the 'cache' to the real drive. Or hack the original software.

---

