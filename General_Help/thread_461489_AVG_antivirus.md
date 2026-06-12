---
title: "AVG antivirus"
date: 2007-06-01
forum: General Help
---

### Post by merlinus on 2007-06-01
After endless errors when trying to update this program via a terminal (it worked before the -16 kernel upgrade), and some problems with owner, I tried to get rid of it via Synaptic.

This failed, so I manually deleted all of the files associated with the program.

But....  is there some apt-get --purge command (or something similar) that will ensure it is completely gone?

As you might imagine, if Synaptic can't kill it, I do not want it on my system.

Thanks!

-merlin

---

### Post by madmetal on 2007-06-01
> **merlinus said:**
> After endless errors when trying to update this program via a terminal (it worked before the -16 kernel upgrade), and some problems with owner, I tried to get rid of it via Synaptic.

This failed, so I manually deleted all of the files associated with the program.

But....  is there some apt-get --purge command (or something similar) that will ensure it is completely gone?

As you might imagine, if Synaptic can't kill it, I do not want it on my system.

Thanks!

-merlin

is AVG at synaptic? :-k
how have you installed it?

---

### Post by merlinus on 2007-06-01
I installed it via Synaptic, but could not remove it that way.  Error message to the effect that the process could not be completed.

So I wonder if they threw some proprietary garbage into the app to make it non-removable.

:(

-merlin

---

### Post by mikewhatever on 2007-06-02
Use this guide to install AVG [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)
To remove it, try this [http://ubuntuforums.org/showthread.php?t=426070](http://ubuntuforums.org/showthread.php?t=426070)

---

### Post by merlinus on 2007-06-02
Thanks for the tip.  Looks like I got rid of all of it manually, though.

But mainly I am wondering why, after the kernel -16 upgrade, it refused to update via

sudo avgupdate -o

which worked perfectly previously.

Anyway, I can feel better about reinstalling with your handy guide about how to get rid of it, if need be.

One more question -- since it is available via Synaptic, why not go that route rather than apt-get?

Many thanks!

-merlin

---

### Post by mikewhatever on 2007-06-02
I did not know AVG was available via Synaptic. Do you know since when is it in the repositories?

---

### Post by merlinus on 2007-06-02
I am mistaken.  It showed up in Synaptic because it was installed on my computer.

I must have downloaded the .deb from their website.....

Thanks for your help!  Much appreciated.....

-merlin

---

