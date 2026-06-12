---
title: "File Retrieval for Restoring Evolution"
date: 2015-01-02
forum: General Help
---

### Post by ozark_hillbilly on 2015-01-02
OK, I have had to re-install Evolution email handler after going from 12.04 LTS to 14.04 LTS. I want to extract the archives files related to Evolution to bring it up to date.
When the Evolution installer asks me to point to the backup file(s) to use to restore Evolution how do I know which ones to use? The .dgp files of my backup archive are considered an invalid selection by the installer.

Or, can I go into the .config evolution area and find the needed files there? If so, which ones to grab?

Ed

---

### Post by buzzingrobot on 2015-01-04
Restoring from a backup created within Evolution?  Last time I did that Evolution was looking for a ????.tar.gz archive.

---

### Post by ozark_hillbilly on 2015-01-04
Would the backup of my /HOME folder contain the Evolution data? I have archived files like this saved:

/media/ed/Backupdrive/Backup Archives/duplicity-full-signatures.20141222T023626Z.sigtar.gpg

---

### Post by buzzingrobot on 2015-01-04
> **ozark_hillbilly said:**
> Would the backup of my /HOME folder contain the Evolution data? I have archived files like this saved:

/media/ed/Backupdrive/Backup Archives/duplicity-full-signatures.20141222T023626Z.sigtar.gpg

Those files appear to be backups created by Deja Dup.

Within Evolution itself there is a function to create an archive of your current settings: servers, ports, username, password, etc. There is also an option in the Evolution setup panel. -- the one you see on first use -- to use that archive to quickly complete the 
setup of a new Evolution install.

If you created that archive, I expect it's in one of the Evolution folders in your home folder.  If you backed up home with Deja Dup, it ought to be restorable with Deja Dup. As mentioned, it's a ".tar.gz" file.

---

### Post by buzzingrobot on 2015-01-04
> **ozark_hillbilly said:**
> Would the backup of my /HOME folder contain the Evolution data? I have archived files like this saved:

/media/ed/Backupdrive/Backup Archives/duplicity-full-signatures.20141222T023626Z.sigtar.gpg

Those files appear to be backups created by Deja Dup.

Within Evolution itself there is a function to create an archive of your current settings: servers, ports, username, password, etc. There is also an option in the Evolution setup panel. -- the one you see on first use -- to use that archive to quickly complete the setup of a new Evolution install.

If you created that archive, I expect it's in one of the Evolution folders in you home folder.

---

