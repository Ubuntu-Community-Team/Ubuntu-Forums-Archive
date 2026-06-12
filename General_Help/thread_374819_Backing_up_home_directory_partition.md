---
title: "Backing up home directory partition"
date: 2007-03-03
forum: General Help
---

### Post by DarkDancer on 2007-03-03
Hi!

I just bought myself a brand new computer (well, the parts for it) and I wanted to back up the home directory partition, for 2 reasons. 

1. there is never a guarantee that your old drives will work on a new controller without repartitioning.  

2. I kind of wanted to redo the drives anyway (I want more space in my home Directory)

So, I pop into gnomebaker, pick the home directory, and it gives me this message:

mkisofs: Directories too deep for 'home/var/cache/setup-tool-backends/backup/time/First/etc' (7) max is 6.
:-( write failed: Input/output error


How can I back up the home partition?

---

### Post by taurus on 2007-03-03
See if you can do that, copying $HOME, using k3b.  I don't have any problem copying my $HOME to a DVD using k3b.

---

### Post by DarkDancer on 2007-03-03
Thanks! That seems to be doing the trick.... ;)

---

