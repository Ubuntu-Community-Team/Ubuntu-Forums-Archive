---
title: "[SOLVED] Kmail - Exporting emails from one pc to another!"
date: 2007-07-30
forum: General Help
---

### Post by daller on 2007-07-30
Hi there,

I'm setting up a new computer for a friend!

His old computer is running feisty (like the new one)

How can I export all kmail emails, from the old computer, onto the new computer?

---

### Post by TBerben on 2007-07-30
Open Kmail, go to File, then Export Mail.. Kmail will automatically compress all folders to a gzipped tarball. On my computer it creates /home/***/Desktop/kmail_exported_mail/ and stores the archive there. Since I didn't alter any settings in Kmail I assume that this is the default behaviour. Hope it helps :)

---

### Post by dreadlord_chris on 2007-07-30
> **daller said:**
> Hi there,

I'm setting up a new computer for a friend!

His old computer is running feisty (like the new one)

How can I export all kmail emails, from the old computer, onto the new computer?

Basically, it's pretty simple - just copy the accounts mail folder (either ~/Mail or ~/.kde/share/apps/kmail/mail) to a temporary folder on the new computer - then run KMail's Import Messages (File > Import Messages) utility on the temp folder.

This will work fine as long as the original mail folder was **not** configured in **mbox** mode. You can check what format his are in through: Settings > Configure Kmail > Misc > By default, message folders on disk are:      <<== if this says **Directories ("maildir" format)** then you are fine.

If it says **mbox** then you will need to create another folder: in the **Folders** box - right-click **Local Folders** > New Folder > give it a new name > Type=maildir
Then _copy_ all the mail to the new folder, copy that folder to the new machine & import it.

---

### Post by daller on 2007-07-31
Thanks! - It worked well!

---

