---
title: "Folder inaccessible in Windows but works in Ubuntu?"
date: 2007-09-08
forum: General Help
---

### Post by blade22 on 2007-09-08
I currently have 3 HDDs in my PC. 1 ide on which I have ubuntu and windows installed and two sata drives one of which I use to store videos on. One of the folders which I have on my drive is inaccessible in windws. Wehn I click on it in windows I get an error message saying that the folder is refering to source which is unavailable. However I can fully acess the folder in Ubuntu. Is this because the folder it i in was created using linux?

---

### Post by merlinus on 2007-09-08
How is the partition formatted?

-merlin

---

### Post by blade22 on 2007-09-08
the two SATA drives are formatted in NTFS format. I can access all of the other video files on the same drive in windows, just this one folder does'nt seem to be working.

---

### Post by merlinus on 2007-09-08
You might check its permissions.

-merlin

---

### Post by blade22 on 2007-09-08
It says root access, when i'm in ubuntu. However I've checked it up against all the other folders which do work and they are the same. Do you think that it could be just because I made the folder in Ubuntu?

---

### Post by merlinus on 2007-09-08
Entirely possible.  I have had permissions problems when I thought there should be none.

You can change the permissions from ubuntu by running nautilus as root:

```

gksudo nautilus

```

-merlin

---

