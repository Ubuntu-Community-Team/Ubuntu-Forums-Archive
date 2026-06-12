---
title: "Backing up my /home"
date: 2014-12-04
forum: General Help
---

### Post by seabird22 on 2014-12-04
Hello to all.


   I am looking to be able to back up /home in the most efficient way possible in an effort to; save time, minimize hard drive wear and tear, not  forget any items. For example; I work on several different documents daily, however, some are not worked on everyday. I update entries on my password file almost on a daily bases. I add new files to Downloads and Documents. I am looking for a way to be able to automatically copy only what has changed in /home, including existing files that I have worked on for that day (e.g. documents, password file). Is it possible to this with one string in the command line? 


Any help would be appreciated.

---

### Post by nerdtron on 2014-12-04
HHmmmm.. a lot of options can be used on  backing up.

For starters we can use the following command:

```
 rsync -avrh --progress /home/username/ /path/to/destination/
```

It won't compress anything. It will just copy the contents of the /home/username/ folder to the /path/to/destination folder.
At first this will copy everything (except hidden files). Next time your run the rsync command, it will check only the files that are updated and those will be ones that will be transferred.
Rsync can have lots of options and tweaks to maybe fit your needs and this example is only a simple "copy and update" command.

I think it also have a GUI tool for this, (grsync ??) but I haven't used it.

---

### Post by seabird22 on 2014-12-04
> **nerdtron said:**
> HHmmmm.. a lot of options can be used on  backing up.

For starters we can use the following command:

```
 rsync -avrh --progress /home/username/ /path/to/destination/
```

It won't compress anything. It will just copy the contents of the /home/username/ folder to the /path/to/destination folder.
At first this will copy everything (except hidden files). Next time your run the rsync command, it will check only the files that are updated and those will be ones that will be transferred.
Rsync can have lots of options and tweaks to maybe fit your needs and this example is only a simple "copy and update" command.

I think it also have a GUI tool for this, (grsync ??) but I haven't used it.

Thank you very much for your reply. I will read the man pages.   ):P

---

