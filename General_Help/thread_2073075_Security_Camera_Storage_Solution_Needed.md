---
title: "Security Camera Storage Solution Needed"
date: 2012-10-18
forum: General Help
---

### Post by MrVining on 2012-10-18
Very small business with limited resources, no IT department so the guy who likes computer gadgets and plays Warcraft (that’s me) is the go to guy for "my computer wont print"... Not that I'm complaining I just have no formal training and limited reading skills.

We are in chronic need of a storage solution. I have up to 10 cameras streaming up to 40 Mbps each. Rarely do all 10 record but it is possible, frequently 1 - 3 are recording. The system we were using had semi intelligent recording (when motion triggered a camera to stream, the software would choose the storage directory that had the most available space that was not currently being used, it worked GREAT with 5 drives and no raid). Now we are forced into new software that will ONLY record to one directory. It can be a share or hardware w/e but it will only record to one.

The problem I'm running into is that with a raid 5 or even with raid 10 that is just way way too much seeking. Especially if we ever want to actually view one or two streams that were captured earlier.

Best I can tell we need one of two things. An intelligent file sharing system that will choose to save incoming files on inactive drives, OR some sort of hybrid system with SSD cache that will hopefully last long enough to give a raid controller time to permanently write the files before the SSD fills up.

I'm hoping to build a dedicated storage server for this probably running Ubuntu with 7200 rpm 1.5TB SATA drives. Any insight or advice will be much appreciated as I'm pretty newbish.

---

