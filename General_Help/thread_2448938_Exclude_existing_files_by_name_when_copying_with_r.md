---
title: "Exclude existing files by name when copying with rsync"
date: 2020-08-16
forum: General Help
---

### Post by Helveticus on 2020-08-16
Hello

I'm executing the following two `rsync` commands. In the first command, I'm copying files from source to destination and in the second command I'm then checking the files and delete the files in source.
```

    rsync --info=progress2 -r /local/data/ /import/myNAS/data
    rsync --info=progress2 -r --checksum --remove-source-files /local/data/ /import/myNAS/data
```

I would like to only copy and remove files from source to destination which do not exists already in destination. I could do this using the `--ignore-existing` flag but with this flag files are copied when they are newer. I would like to have a check only on name and not timestamp. That means when a file with the same name exists in destination, the file should not be copied from source and should also not be deleted from source.

Is this possible?

---

### Post by Dennis N on 2020-08-16
> That means when a file with the same name exists in destination, the file should not be copied from source and should also not be deleted from source.
No rsync, but the **cp -n** command will do that. It copies only files with names not at the destination. It doesn't delete anything anywhere.

---

### Post by HermanAB on 2020-08-17
Remove the --checksum option and use --ignore-existing instead.

Other options that may be useful:
--ignore-times          don't skip files that match size and time
--size-only             skip files that match in size
--modify-window=NUM     compare mod-times with reduced accuracy

---

### Post by Helveticus on 2020-08-17
But --ignore-existing does not only check for file name but also for timestamp. So, if a file is newer it is replace. I would like to have a check only on name. So for example, if already a file name "test.jpg" exists, it should not be replaced independent of it is older or newer.

---

### Post by HermanAB on 2020-08-17
Hmm, how about "touch -m -r *" on the archive first, before doing the rsync?

For good measure you could use -t and set the whole archive to the year 2525 in the future.

Alternatively, consider running your own time server, so that time stamps actually work the way they are supposed to.

---

