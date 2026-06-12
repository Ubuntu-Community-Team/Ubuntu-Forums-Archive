---
title: "Restoring files from NTFS to Ext4?"
date: 2015-08-04
forum: General Help
---

### Post by Mark_in_Hollywood on 2015-08-04
I am helping a neighbor with Xubuntu. His 2009 era Dell laptop's hdd died. I installed a new drive. Installed Xubuntu (I use Ubuntu, but his Core 2 Duo lappy has but 1.5 gig of RAM, so I thought lighter on resources, better).

Before his Vista disk crashed, I set the Windows Vista Backup & Restore Center to backup his pix, resume, etc. (c:/User/*.*) I would like to bring those files from the external backup drive over to Xubuntu. The backup set is all *.zip. Can I restore these NTSF files onto EXT4?

---

### Post by Vladlenin5000 on 2015-08-04
The file system where the files reside is irrelevant, provided it is recognized by the OS, both origin and destination. Copy/paste whatever you want.

---

### Post by howefield on 2015-08-04
> **Mark_in_Hollywood said:**
> The backup set is all *.zip. Can I restore these NTSF files onto EXT4?

If you are asking simply can they be copied to the ext4 file system, then yes they can. A zipped picture can be stored, accessed and opened just as well as they did on Vista. The only caveat being that the file format will determine if they can be opened in Xubuntu, you need an application capable of opening them, eg a publisher file won't open but word and excel files will.

---

