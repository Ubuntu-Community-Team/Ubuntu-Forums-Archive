---
title: "Website backup"
date: 2007-11-14
forum: General Help
---

### Post by mellowd on 2007-11-14
Hi there.

I'm currently running Gutsy as my home server so no X on there. I've got 3 websites online. I'd like to know if there is a way I can get my server to automatically connect to these three websites via ftp and download them for backup. It would also be nice if it automatically compressed them. It would be even better if it could check for new files only and download them to prevent myself downloading the same large files over and over again. 

Is there a way to do this?

Thanks!

---

### Post by mellowd on 2007-11-15
No-one has any ideas?

---

### Post by fsmithred on 2007-11-15
You can use wget to download the websites. Look at man wget to see what options are available.
 If you want to automate the whole procedure, you could write a bash script to do it, and make it a cron job.



.

---

### Post by Seti on 2007-11-15
I used to do precisely this with a script scheduled to run from cron. The server had NFS and was configured to only share with my backup server.

---

### Post by mellowd on 2007-11-15
I'll be using cron thanks. 

Let's see how I progress with it :)

---

