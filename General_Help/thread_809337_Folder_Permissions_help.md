---
title: "Folder Permissions help"
date: 2008-05-27
forum: General Help
---

### Post by jwf0020 on 2008-05-27
I did a search for this but no luck. 

I want to change a folder's permissions so that (for example) any user can access the contents of the folder. 

I have already changed the permissions so that a specific folder is read/write/executable for all users. However, when a new file is created within the folder, it does not inherit the permissions that I had set for the folder it is in.

How can I set the folder contents to inherit the same permissions as the folder itself?

Thank you in advance.

---

### Post by drs305 on 2008-05-27
Disregard - I'll post it shortly. Do you want them to just be able to read the files?

---

### Post by mattress on 2008-05-27
I've never really toyed much with this, but perhaps this article will help:

    [http://www.linuxjournal.com/article/7727](http://www.linuxjournal.com/article/7727)

By default I don't think what you want is possible without running chmod/chown/chgrp after the fact...

Please correct me if I'm wrong...

m

---

### Post by jwf0020 on 2008-05-27
> **drs305 said:**
> Disregard - I'll post it shortly. Do you want them to just be able to read the files?

I want them to read and execute all of the contents of the folder. However, when a new file is created in the folder by the owner, I want the permissions of that file to default to read/executable without me having to run a command line.

---

### Post by jwf0020 on 2008-05-27
> **mattress said:**
> I've never really toyed much with this, but perhaps this article will help:

    [http://www.linuxjournal.com/article/7727](http://www.linuxjournal.com/article/7727)

By default I don't think what you want is possible without running chmod/chown/chgrp after the fact...

Please correct me if I'm wrong...

m

I'm reading it now. Thanks for the link. There's got to be a way to have folders default to a set of permissions...

---

### Post by jwf0020 on 2008-05-27
I did some quick research on the web and found out about Access Control Lists (ACLs). Does anyone know if this would enable me to do what I want?

Still researching....

---

### Post by lswest on 2008-05-27
I'd suggest setting up a bash script chowning the folders (or chmodding it) regularly using a Cron Job (I'd post a link, but I hardly use them, so a quick google search might yield more information) to run the script at set intervals.  This is a basic fix, but it should work.

---

### Post by drs305 on 2008-05-27
umask can be used to set permissions on future creations but I am not sure how to set it up to run all the time on only one folder.  umask can be invoked inside the ~/.bashrc file or fstab or in a script. 

If using umask is a possibility I'm sure someone will post.

---

### Post by jwf0020 on 2008-05-27
> **lswest said:**
> I'd suggest setting up a bash script chowning the folders (or chmodding it) regularly using a Cron Job (I'd post a link, but I hardly use them, so a quick google search might yield more information) to run the script at set intervals.  This is a basic fix, but it should work.

I think it's called crontab. I have thought of using crontab to set up a scheduled task but I would need to run it every few seconds of every hour of every day. I really would hate to do this. Just thinking of doing that makes me want to take a shower.

---

