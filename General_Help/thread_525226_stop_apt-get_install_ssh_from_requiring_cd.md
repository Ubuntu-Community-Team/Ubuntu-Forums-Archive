---
title: "stop apt-get install ssh from requiring cd"
date: 2007-08-14
forum: General Help
---

### Post by Dudsmacka2 on 2007-08-14
On a fresh install of ubuntu server edition, if I were to run **apt-get install shh** it prompts me for the ubuntu cd to be mounted so it can copy files.  Is there any way I could set it up to avoid needing the cd in the cd-rom drive - preferably by downloading all dependencies from the internet?

---

### Post by merlinus on 2007-08-14
System/Administration/Software Sources.  Make sure cd is unticked.

-merlin

---

### Post by Bachstelze on 2007-08-14
> **merlinus said:**
> System/Administration/Software Sources.  Make sure cd is unticked.

On a server ??


@Dudsmacka2, open /etc/apt/sources.list in your favourite text editor and comment out or delete the cdrom line.

---

### Post by Dudsmacka2 on 2007-08-14
> **HymnToLife said:**
> Dudsmacka2, open /etc/apt/sources.list in your favourite text editor and comment out or delete the cdrom line.

ty!

---

### Post by Dudsmacka2 on 2007-08-14
On a somewhat similar note, If I have **apt-get install ssh >> /home/prep.log;** in a BASH script, how can I get it to automatically choose "yes"?

---

