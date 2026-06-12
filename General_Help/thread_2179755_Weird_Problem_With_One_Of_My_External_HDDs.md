---
title: "Weird Problem With One Of My External HDDs"
date: 2013-10-09
forum: General Help
---

### Post by Katniss Everdeen on 2013-10-09
I have two HDDs, same same (4TB) and the have all the same files on them. They are a duplicate backup, pretty much containing movies and TV shows.

One of them, if having really weird problems. I says the free space is 1.6GB less then the other one. I've checked all the files, and make sure they are all the same size, and they are.

ANother one, which is even weirder. One of my movie files is acting as a shortcut, to random files. First, when I found out that is was a different size, then the one on the other HDD, I've viewed the proeperties, and see which was was the better of the two, and replace it with that one. I couldn't delete it. I get this error:
[ATTACH=CONFIG]246845[/ATTACH]

I clicked on the file and it didn't play the movie, but another movie I had. I played the movie "The Egde" (1997). So Ideleted that movie, and hoping I can now delete said file. I get an input/output error.

I unmount and remount the HDD, I can now delete it. A short while later, and file with some letters and numbers apear with a . at the front of it. I've seen that happen beofre, but not on this HDD, it has been awhile.

The said file appears back, and when I click on it, it opens up a random photo on the HDD.

I've never seen this before. I am thinking of reformating the HDD with the problem. Everything that is on it, is also on another HDD, as I said before. The downside, is that it around 3TB, which would take a long time to copy over.

Is there anything else I can do, and avoid reformating the HDD? Also, why is it only one of the HDDs, not both?

---

### Post by erind on 2013-10-09
> **Katniss Everdeen said:**
> [...]

I clicked on the file and it didn't play the movie, but another movie I had. I played the movie "The Egde" (1997). So Ideleted that movie, and hoping I can now delete said file. I get an input/output error.

I unmount and remount the HDD, I can now delete it. A short while later, and file with some letters and numbers apear with a . at the front of it. I've seen that happen beofre, but not on this HDD, it has been awhile.

[...]
These signs seem to point to a failing disk and not a Ubuntu problem per se, good that you have a backup. To make sure try these steps first:

**1.** Perform a disk check. If it's NTFS formatted use Windows tools (*chkdsk* from Windows), similarly for Linux FS use linux tools (*fsck*). Try it a few times and see how the disk behaves.

**2.** Use a health/recovery disk software for a deeper analysis. There are many out there, but one that I've used is SpinRite (paid), which takes some time to complete, but it'll show and try to repair the bad sectors.

**3.** Depending on the results above, try a full format and keep a good eye on it, (it might happen again).

After these steps you'll have a better idea of what's going on and what to do.

---

