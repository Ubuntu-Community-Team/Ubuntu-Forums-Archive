---
title: "Rsync - deleting files when using --files-from"
date: 2007-11-27
forum: General Help
---

### Post by feenster on 2007-11-27
Hi,
Struggling with something in Rsync at the moment. I'm issuing the following command:

```
rsync -avz --delete --files-from=includes.txt --exclude-from=excludes.txt / /backup
```

Includes.txt contains:
```
/home/folder1
/home/folder2
/home/folder3
```

So that will happily backup the above three folders to **/backup**, and will delete any files in the destination that don't exist in the source anymore. However, if I remove **/home/folder3** from the *includes.txt* list, the folder isn't deleted from **/backup** (note: **/home/folder3** isn't added to the *excludes.txt* list, as it would be too cumbersome to maintain a big list).

Is there anyway round this - can i force Rsync to delete folders on the destination that don't exist on the source, when the data is being fed in with *--files-from*?

Cheers,
  Matt

---

