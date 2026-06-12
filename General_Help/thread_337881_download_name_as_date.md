---
title: "download name as date"
date: 2007-01-13
forum: General Help
---

### Post by dest581 on 2007-01-13
I can't find out how to name a downloaded file through wget as the current date.  For example, I want to download [http://blah.com/blah.zip](http://blah.com/blah.zip) every day, and I want a directory which has a file labeled for each day.  Each of those files would be that day's blah.zip.  

I'm trying to download sql backups from cpanel's automatic backup script.  I know how to do that part, but I don't know how to do the renaming.  

Thanks for the help.

---

### Post by Hossie on 2007-01-13
```
!#/bin/bash
cd /my/dir
mkdir `date +%y%m%d`
cd `date +%y%m%d`
wget myfile.zip
```

---

### Post by dest581 on 2007-01-13
Thanks!

Followup question: Would putting this into crontab work as a daily download?

```

0 0 * * * user cd /home/user/folder/;mkdir `date +%y%m%d`;cd `date +%y%m%d`;wget "address";
```

---

### Post by Hossie on 2007-01-13
Im not sure if the command gets executed with a shell (you would need a real shell for the backticks and so on), its much better to write it in a file and execute that.

---

### Post by dest581 on 2007-01-13
Thanks for the help!

---

### Post by Hossie on 2007-01-13
No problem.

Dont forget to make it executable and always give absolute paths (because $PATH is limited in Cronjobs).

---

