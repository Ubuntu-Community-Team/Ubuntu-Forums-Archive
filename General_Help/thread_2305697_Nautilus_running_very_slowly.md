---
title: "Nautilus running very slowly"
date: 2015-12-08
forum: General Help
---

### Post by mystmaiden on 2015-12-08
I'm running 12.04 LTS and have noticed of late that opening files has slowed down significantly. I updated everything today (one of the cures listed online) but no joy there. When I open Documents I get the loading icon, but even after it disappears it takes some time to actually use the files. I'm wondering if that could be caused by having too much stuff in the folder? Documents is about 25G snd Music in 16G. Other folders are very slow to open as well, but those two are the most noticeable.

I'd love some help solving this.

thanks,
mystmaiden

---

### Post by Ricardo_Velasco on 2015-12-08
Greeting:

Sorry for the wrong answer before.

I have a possible solution

Try running without GUI :

> [FONT=arial]sudo killall nautilus
sudo apt-get install --reinstall nautilus[/FONT]

With these commands these reinstalling Nautilus

---

### Post by mystmaiden on 2015-12-08
Thank you for the reply. Ricardo. I did reinstall nautilus per your suggestion - it didn't help unfortunately.

---

### Post by Ricardo_Velasco on 2015-12-08
Greetings

Hope you serve , investigate a temporary solution to your problem . He says it is due to a corrupt file you sent the information page :

[https://wiki.debian.org/Nautilus/FAQ/SlowNautilus](https://wiki.debian.org/Nautilus/FAQ/SlowNautilus)

Here run these commands as root:

> sudo su

[B]rm -rf /home/YOUR-USERNAME-HERE/.local/share/gvfs-metadata

**pkill gvfsd-metadata**[/B]

---

