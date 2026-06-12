---
title: "backup all the mails fetched by evolution"
date: 2008-06-19
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-06-19
how to backup all the mails fetched by evolution? can i save them all as text files or something that could be read by a text editor? or any other way that could make a back up for it so that i could store them in a usb flash drive? many thanks

---

### Post by cariboo on 2008-06-20
Here is a link that should help you:

[http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/](http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/)

Jim

---

### Post by tbraun on 2008-06-20
Hello!

There are several options. Personally, I just make a 1:1 copy of the ~/.evolution folder. I figure that if my disk gets corrupted, I would install Ubuntu again on any new disk I'd get, and I would also continue to use Evolution. Thus, I don't need to change the format.

Incidentally, I had described a while back how I secure my data (using truecrypt) and at the same time get a very simple backup solution. The post is here: [http://ubuntuforums.org/showthread.php?t=376822]("http://ubuntuforums.org/showthread.php?t=376822"). This also talks specifically about Evolution. (Note that the latest version of truecrypt has different command line switches now and a GUI as well, so that part changes a little bit).

Note also that Evolution has a backup mechanism built in (look under the File menu for "Backup Settings..."). I never tried that, though.

Finally, the format in which the e-mails are stored is pretty much standard MBOX, so you should easily be able to import them in other e-mail programs or in a text editor.

---

### Post by afeasfaerw23231233 on 2008-06-20
thanks for help!
here are the files and folders inside /.evolution.
> addressbook  calendar       categories.xml  key3.db  memos      tasks
cache        camel-cert.db  cert8.db        mail     secmod.db

 which of them should i put back in case my harddisk is corrupted? And which software can i use to view their contents before i can get my box recovered?

---

### Post by afeasfaerw23231233 on 2008-06-22
bumP

---

