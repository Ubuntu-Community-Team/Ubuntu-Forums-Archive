---
title: "[SOLVED] chmod directory and its sub-directory, but not the files"
date: 2008-03-02
forum: General Help
---

### Post by Rick Z on 2008-03-02
Hi,
How do I chmod 777 to a directory (i.e /var/www/test/template) and its sub-directories to all the same permission, but not the files?

if I run the following command "chmod 777 -R /var/www/test/template" or "chmod -R /var/www/test/template" , this will also change its files permission right?  I just need to change the directories permission not the files.  Is this possible?

:)

---

### Post by Oldsoldier2003 on 2008-03-02
> **Rick Z said:**
> Hi,
How do I chmod 777 to a directory (i.e /var/www/test/template) and its sub-directories to all the same permission, but not the files?

if I run the following command "chmod 777 -R /var/www/test/template" or "chmod -R /var/www/test/template" , this will also change its files permission right?  I just need to change the directories permission not the files.  Is this possible?

:)
use the gui, or alternatively write a quick bash script to loop through the directories and chmod 777 them

---

### Post by Rick Z on 2008-03-02
Thank you very much for the suggestion.  I am not sure how to write a shell script.  I knew this can be done in GUI, but it's little time consuming.  Could you show me how to write a shell script in this situation?

Thanks.

---

### Post by ghostdog74 on 2008-03-02
```

find /yourpath -type d -exec chmod 777 "{}" \;

```

---

### Post by Rick Z on 2008-03-03
This is GREAT.  Thank you so much.

---

