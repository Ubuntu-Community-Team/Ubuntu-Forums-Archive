---
title: "Symlinks followed on  Vorta backup?"
date: 2021-08-01
forum: General Help
---

### Post by timgood on 2021-08-01
I'm using Vorta to backup my home directory. Since moving /home to a SSD I've kept Music and Video files on the original HDD and symlinked the Music and Video directories to the old location. My question is - will Vorta backup these files by following the symbolic links or do I have to create a separate backup routine to do so? The drives are mounted at boot in fstab - the SSD to /home and the Music and Video directories on /shared. Would be grateful for advice.

---

### Post by Holger_Gehrke on 2021-08-01
Vorta is a frontend for Borg. The documentation for Borg states "Besides regular file and directory structures, Borg can preserve symlinks (stored as symlink, the symlink is not followed)" (see [here]("https://borgbackup.readthedocs.io/en/stable/usage/general.html#support-for-file-metadata")). So no, Vorta will not backup symlinked directories, you'll have to add the target directories of the symlinks to the backup yourself.

Holger

---

### Post by timgood on 2021-08-01
Thanks Holger. Have added as you suggested.

---

