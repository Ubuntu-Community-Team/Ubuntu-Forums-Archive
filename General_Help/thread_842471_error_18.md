---
title: "error 18"
date: 2008-06-27
forum: General Help
---

### Post by sanvice on 2008-06-27
I recently bought a 200 gig harddrive and installed ubuntu on it.
When I restart i keep getting this error:

[B]Boot from cd:
Grub loading, please wait ...
Error 18[/B]

I didn't partition it, i used all 203.9gb of it and i have no idea whats wrong...
Any help?   

:confused:

---

### Post by phidia on 2008-06-27
Grub didn't install to the MBR and/or the partitioner didn't work correctly.
There is a sort of long explanation of that [here]("http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=7667&start=0&postdays=0&postorder=asc&highlight=") 
But mostly you may want to try reinstalling grub. At least try that first. There should be an option from the install cd to reinstall grub or you can get the [supergrub disk]("http://www.supergrubdisk.org/").

---

### Post by sanvice on 2008-06-27
Thanks, i got the grub cd and I'm going to try that. :)

---

