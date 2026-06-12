---
title: "fakeraid a sucess case (ot maybe)"
date: 2006-12-30
forum: General Help
---

### Post by larini on 2006-12-30
Hi, I finally get my system work in my raid array (nvidia)
I do the folowing (resuming):
- I install ubuntu in a third drive
- I copy all partition do my raid using cp
- change grub things
- and works!

but..

my partition has 500GB, but in nautilus I'm getting only 37 GB free.
The same free space that I had in the third drive.

Any glues?

Thanks

---

### Post by WTF_Shelley on 2007-01-13
Have you changed Fstab to point at you new array? if you haven't its booting grub on your array then mounting the third drive as / , /home etc

---

