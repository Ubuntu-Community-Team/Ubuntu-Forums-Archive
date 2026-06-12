---
title: "Putting linux files back into windows"
date: 2007-09-04
forum: General Help
---

### Post by AKR on 2007-09-04
I mounted my windows drive so I could take some folders off of it, and organize some files. After i was done, i tried to put the folder back onto my windows drive, but it tells me I do not have permission to write on the drive. how can I move my folders from linux back into windows?

---

### Post by jorgesallum on 2007-09-04
How did u mount the windows partition? What type  did you choose? Did you do as root or sudoer? If it concerns only *nix folder permitions, try a simple "chmod 777 *" in it and check if you can move it back. A much more simple issue is... copying it to a pendrive or something and put it back on windows :).

---

### Post by merlinus on 2007-09-04
If your windows is ntfs, then this should work:

Open a terminal and enter:

```

sudo apt-get install ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

-merlin

---

