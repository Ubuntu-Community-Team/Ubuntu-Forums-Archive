---
title: "Software problem after power-brake"
date: 2006-10-26
forum: General Help
---

### Post by rejser on 2006-10-26
My neighbur who is a farmer dug through the power cable to our house, when power came back I was going to start ktorrent, which was active when the brake came.
The message I get is:

> ScimInputContextPlugin()
terminate called after throwing an instance of 'std::bad_alloc'
  what():  St9bad_alloc


I tried purging ktorrent and reinstalling, but didn't work.

My first thought was hardware error, but scanned ram and harddrive and it cam up with nothing.

Anyone have any idea, never run across this before.

Ed: found the problem, cache in one of torrent-files was damaged which caused ktorrent to crash.

---

