---
title: "geeqie recursive slideshow help"
date: 2021-05-24
forum: General Help
---

### Post by franklin1k on 2021-05-24
In geeqie I have a problem with making a slideshow recursive.  When right clicking on the folder my pics are in, to make the recursive of subfolders, the option is greyed out.  Help!

---

### Post by TheFu on 2021-05-24
I'm running Geeqie 1.5.1 and the Recursive slideshow is working.  Just tested it here. Worked fine with photos on NFS mounts.
As a first guess, I'd think it was the userid lacking read permissions.

---

### Post by franklin1k on 2021-05-25
I'll look into that.  First time I've ever seen this problem.  Geeqie has been my viewer for ten years.
thanks

---

### Post by MasterZ on 2021-07-26
Hi, 
Did you manage to solve the issue ? 
I'm running Geeqie 1.6 on Hirsute and I also have my slideshow options greyed out on the right-click menu. 

I do have read access to the files and it used to work before (so I suspect some update took place). 
I tried to delete my geeqie folder in .config and let it recreate a new one, but still the same behavior. 

I'm able to launch the recursive slideshow from the command line, just not from the context menu anymore. 
Is there any pre-requisite for this to work ? (file indexing service, ... )

---

