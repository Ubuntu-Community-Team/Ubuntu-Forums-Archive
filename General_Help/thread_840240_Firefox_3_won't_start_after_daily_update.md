---
title: "Firefox 3 won't start after daily update"
date: 2008-06-25
forum: General Help
---

### Post by rturner on 2008-06-25
Update Manager upgraded firefox today and now I can't get it to start.  I tried starting it from the command line and got the following error:

error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory

I'm not sure what to try next.

---

### Post by foadumf on 2008-06-25
I had the same problem and this worked for me:

sudo cp /usr/lib/xulrunner-1.9/libjemalloc.so /lib

i am using hardy 64bit

---

### Post by graemej236 on 2008-06-25
Thanks for this Foadumf it got my Firefox back working too on Hardy.

---

### Post by rturner on 2008-06-25
> **foadumf said:**
> I had the same problem and this worked for me:

sudo cp /usr/lib/xulrunner-1.9/libjemalloc.so /lib

i am using hardy 64bit

It worked fine in my 32bit install.  Thanks!

---

### Post by chronniff on 2008-06-25
I thank you as well foadumf that worked for me as well, any clue as to why this happened?

---

### Post by Double D on 2008-06-25
> **foadumf said:**
> I had the same problem and this worked for me:

sudo cp /usr/lib/xulrunner-1.9/libjemalloc.so /lib

i am using hardy 64bit


Thank you, this worked for me as well

something is wrong with the newest firefox update i suppose

---

### Post by Harpoon on 2008-06-26
Thanks, foadumf.  For the benefit of others, this does not seem to be an Ubuntu problem.  All distributions are suffering from the same "broken after upgrade" problem.

I'd suggest to the mods that this fix be made a sticky.  We have not heard the last of this, I am sure.

---

