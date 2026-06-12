---
title: "Accidentally Deleted File in Nemo - HELP?"
date: 2019-10-07
forum: General Help
---

### Post by rebeltaz on 2019-10-07
I have a folder that is network connected to my laptop and mounted. In Neo, I right-clicked on the file (an AVI) and accidentally clicked move to trash. I immediately hit CTRL-Z. The file didn't reappear. The [Undo] menu is greyed out. The file is not in the trash. Is there any way I can find this file?

---

### Post by oldrocker99 on 2019-10-07
Here's what Google found.[https://www.tecmint.com/photorec-recover-deleted-lost-files-in-linux/](https://www.tecmint.com/photorec-recover-deleted-lost-files-in-linux/)

---

### Post by rebeltaz on 2019-10-07
Well... I don't use g@@gle. I did, however, duckduckgo it and what I found was that every link pointed to testdisk. testdisk is a program with which I am familiar and have used on many occasions to recover lost files for customers. In this instance, however, for some reason, the [undelete] command was not a provided option. I don't know if it's because I was trying to run the program against a mounted drive or not, but there it is. 

Since an internet search had failed me, I had hoped that someone with more knowledge than g@@gle might be able to help. Thank you, though.

---

### Post by Impavidus on 2019-10-07
Testdisk recovers files from the raw data present on the hard drive. For network drives, your laptop has no access to these raw bytes (only the server has), so it won't work.

There's a separate trash can for every partition and user. Did you look in the right trash can? It may be a hidden directory on the network connected filesystem.

---

