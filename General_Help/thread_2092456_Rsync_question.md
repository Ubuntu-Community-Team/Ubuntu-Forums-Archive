---
title: "Rsync question"
date: 2012-12-07
forum: General Help
---

### Post by Herbon on 2012-12-07
I recently ran the following "Rsync" command to sync the entire content (subfolder) of a folder on a "NAS" to another folder on a "NAS".

> rsync -urp  --progress /home/Sillynubie/.gvfs/"mylibrary on 10.10.2.4"/Network_Media_Audio/   /home/Sillynubie/.gvfs/"music on 10.10.2.5"When I check the destination drive with "LS" the folders are present, but not the contents.

I used a "Find" command to located the file type (*.mp3) on the new drive, but can up with no hits.

Yet the terminal shows the file had been copied.  

Thanks!

---

### Post by jim_deadlock on 2012-12-07
Did you wait for the whole operation to complete? rsync tends to create the folders long before the files start appearing.

---

### Post by Herbon on 2012-12-08
> **jim_deadlock said:**
> Did you wait for the whole operation to complete? rsync tends to create the folders long before the files start appearing.

Ok, 

I guess I jumped the gun since the terminal was saying individual files were copied successfully.

---

### Post by Herbon on 2012-12-10
No go, the folders are there, but are empty.

---

### Post by SeijiSensei on 2012-12-10
Use the "a" switch, not "urp".  If you use "rsync -av" the program will list every file it transfers. And if you want simply to transfer the files append a "*" at the end of the first file specfication.

You could also try putting the entire file specification in single quotes like this:

```
rsync -av '/home/Sillynubie/.gvfs/mylibrary on 10.10.2.4/Network_Media_Audio/*' '/home/Sillynubie/.gvfs/music on 10.10.2.5'
```

What user is this running as?  Does the local user have the same user ID as "Sillynubie" on the remote?

---

### Post by Herbon on 2012-12-10
Same user and password on both NAS boxes

I will try this new command later today.

---

