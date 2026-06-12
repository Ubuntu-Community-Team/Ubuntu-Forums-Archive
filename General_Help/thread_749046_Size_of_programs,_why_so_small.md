---
title: "Size of programs, why so small?"
date: 2008-04-08
forum: General Help
---

### Post by homy06 on 2008-04-08
I was rummiging around and I noticed all my programs are really small compared to when I was using windows. like blender is 19 megabytes! why so small? is it just not as feature packed as windows programs?
 Shake 4 is 40 megabytes. a video compositor.

this is crazy small, just wondering.

does it have to do with the way it unpacks? or that they all use the same libraries so once those are downloaded then there's only the app itself to download?

---

### Post by kpkeerthi on 2008-04-08
Thats because linux uses **shared libraries** (common code used by many applications) unlike windows where everything is packaged into one setup file.

---

### Post by mcduck on 2008-04-08
Yeah, shared libraries not only reduce the size of programs, but also the memory usage, as the same library only needs to be loaded to RAM once, and all programs can then use it.

Windows actually is able to use shared libraries as well (all the .dll-files) but because Windows lacks any version management for them installing new programs could easily overwrite the previous library version with older/incompatible one. Because of this developers need to include the correct library versions with every program, and every program also has to load it's own libraries to memory..

---

