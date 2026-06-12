---
title: "System memory"
date: 2007-10-30
forum: General Help
---

### Post by bks on 2007-10-30
I have 512 MB of RAM installed in my Gateway, but the system info says I only have 503.2 MB. Is that just in the way it is calculated? I have a dedicated graphics card so I don't think it is a shared memory issue. Any ideas?

---

### Post by Warren Watts on 2007-10-30
Does your PC have onboard graphics that might be using some of the RAM?

---

### Post by rfruth on 2007-10-30
lshw reports 503 on my P4 512 MB integrated video system ...

---

### Post by nowshining on 2007-10-31
about 8mb of that is dedicated to holding the kernel in memory :) so it's most likely fine, it's only reporting that 503mb is available to apps and also in advance just so u know linux uses RAM for cache so if u notice less it's not, because like I said it uses RAM to the gill and loads it with cache which can be used if needed by any program..


edit: before anyone asks yes I also have an Integrated card but not used as I use an external Nvidia one. :) also yes I also have 512mb RAM...

---

### Post by Warren Watts on 2007-10-31
Can't say in your case, but in my BIOS, unless I specifically disable the shared memory, it shares memory even with the onboard video disabled...

---

### Post by nowshining on 2007-10-31
i can only take down about 7mb as I can't in the bios disable shared memory all I can change from is 8 or 1mb and if I enable 8mb i guess it's the equiv of disabling it as it takes it off of  503 - 49x megs and such. I think XP or Windows just shows the total NO MATTER what.

---

### Post by santiagoward2000 on 2007-10-31
> **nowshining said:**
> about 8mb of that is dedicated to holding the kernel in memory :) so it's most likely fine, it's only reporting that 503mb is available to apps and also in advance just so u know linux uses RAM for cache so if u notice less it's not, because like I said it uses RAM to the gill and loads it with cache which can be used if needed by any program..


edit: before anyone asks yes I also have an Integrated card but not used as I use an external Nvidia one. :) also yes I also have 512mb RAM...

Mmmm, so that's why it said I have 185mb!!

---

### Post by bks on 2007-11-03
> **nowshining said:**
> about 8mb of that is dedicated to holding the kernel in memory :) so it's most likely fine, it's only reporting that 503mb is available to apps and also in advance just so u know linux uses RAM for cache so if u notice less it's not, because like I said it uses RAM to the gill and loads it with cache which can be used if needed by any program..

That make sense. I didn't know the RAM was used for that, thanks.

---

