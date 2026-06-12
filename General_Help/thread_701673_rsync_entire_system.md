---
title: "rsync entire system"
date: 2008-02-19
forum: General Help
---

### Post by Spitphire on 2008-02-19
I've been using rsync for awhile and I had a thought.. but i'm not sure how it will work before i try it.

I would like to keep an up-to-date backup of my ENTIRE system "/" ... that would sync every 24 hours or so and only update the files that need to be changed..

if I 
```

rsync -avz -e ssh user@host:/backup/filesystem/ / 

```

what will it do with the sym links and /dev, etc...?

Is it possible to do this, and will it all restore in the case of a total system crash, to include all the sym links and /dev ??

---

### Post by Spitphire on 2008-02-20
bump

---

