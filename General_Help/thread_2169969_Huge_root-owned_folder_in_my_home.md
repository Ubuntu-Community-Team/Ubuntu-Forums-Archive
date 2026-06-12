---
title: "Huge root-owned folder in my home"
date: 2013-08-24
forum: General Help
---

### Post by zer010 on 2013-08-24
I don't know where it came from or why it's there, it just kinda appeared.  I tried to look into it, but it just keeps loading.  So I go to get info and it says it's owned by root and over 1000MiB.  I tried to remove it using rm -frv and I fell asleep before it finished.  When I woke up, it still hadn't finished so I just stopped it and rebooted.  IT seems to have some random name and when the llist of files being deleted was going on, they looked like they were random names as well. Why would there be a root-owned folder in my home and does anyone have any idea what this is?

---

### Post by prodigy_ on 2013-08-24
> **zer010 said:**
> rm -frv
Verbosity only makes things slower. Simply use ```
rm -rf /path/to/folder &
``` and let rm work in background.

As for the origins of the folder, with a random name it's anyone's guess. What kind files does it (still) contain? Have you tried to open any of them in a text editor?

---

### Post by zer010 on 2013-08-25
Well, I'm not sure what those files were and I never was able to open anything.  Everytime I tried to list the contents of that folder, it would basically just sit there, either loading or stalling.  I'd think that even if it was 1000 files, it should have showed something after 20 minutes.  I guess I'll never know what that was about or what caused it because I opted to do a fresh reinstall.  I just couldn't take having something like that on my computer.  A folder filled with files that root owns in MY home directory that I had little to no control of?  No thanks!  

@prodigy I do appreciate the reply and your tip about using the verbocity option.  I'll keep that in mind.

---

