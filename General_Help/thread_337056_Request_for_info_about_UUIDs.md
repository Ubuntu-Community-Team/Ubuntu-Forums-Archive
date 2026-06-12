---
title: "Request for info about UUIDs"
date: 2007-01-12
forum: General Help
---

### Post by bogdanb on 2007-01-12
Hi! I've been bumping into UUIDs a lot recently and it bugs me that I'm not very clear on how they work. I know what the point of a UUID is, in general, I'm just not very clear on the details of how they work on Linux. I've looked around for more info, but all I get is pieces of info from man pages of various utilities that use them, not a general idea.

The place where I did encounter them is mounting partitions. 

(That's another thing I don't know: are UUIDs used for anything else?)

I did find several utilities that can change a partition's UUID, so I deduce it's just one of those time+mac+maybe something "randomish" generated id, not something necessarily intrinsic to the disc. I never found something that (a) can set the UUID for any partition and (b) tell me the UUID for same partition, which is weird, because it seems to be something rather high-level.

(It seems logical that it is, but I'm not 100% sure: is a partition's UUID stored on that partition? Where? How does it work for things like FAT32?)

I'm sure there is an utility like this, it's just weird that I didn't find it yet.

(I did find a certain vol_id app, but I can't get it to work, it tells me things like "/dev/sdb1: error open volume" even when run as root. findfs seems to do the exact reverse thing that I need.)

Are there any other uses for these UUIDs? Other hardware things that might be identified by them? Is there a way of defining aliases of some sort, so I don't have to type 32 characters just to pick one of my 10 or so partitions (on all drives)?

The change appeared when upgrading from dapper to edgy, and I didn't find any explanation for what and how UUIDs are used wherever they are used. I'll welcome any pointers (just don't explain what a unique identifier is in general, I know that).

---

