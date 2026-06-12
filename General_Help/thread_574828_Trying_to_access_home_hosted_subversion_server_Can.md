---
title: "Trying to access home hosted subversion server: Can't Create Directory..."
date: 2007-10-13
forum: General Help
---

### Post by xelapond on 2007-10-13
So, I just set up a home hosted subversion server on my old iMac G3.  I finaly got it all set up.  On my windoze xp computer running tortoise svn I was able to check out the directory, but on attempt to commit the changes I get:

Error: Commit failed(details follow)
Error: Can't create diectory 'svn/db/transactions/0-1.txn': Permission Denied

Any Idea what this means and how I can fix it?  

I used this guide to set it up:

[http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/)

Though I am running Ubuntu server, not Desktop. 

Any help would be appreciated.

Alex

---

### Post by azza85 on 2008-05-27
Did you manage to fix this?  I am having exactly the same problem ...

UPDATE: I fixed this by changing the permission on the directory of the subversion server.  For some reason, when I created a new project, the permissions were not correct for the subversion user...

---

### Post by snovak on 2008-06-20
You all have to set ownership of your svn root dir.  Like so...

```

sudo chown -R www-data:www-data /path/to/svn/root

```

Then I do my import and check out through the apache module.  

```

svn import http://localhost/svn

or 

svn co http://localhost/svn projectName

```
That did it for me.

---

