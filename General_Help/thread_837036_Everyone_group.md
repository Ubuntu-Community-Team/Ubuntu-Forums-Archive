---
title: "Everyone group"
date: 2008-06-22
forum: General Help
---

### Post by anjanesh on 2008-06-22
Hi

I've created a partition called **/programs** so that I'll install other applications here for everyone to access - but not write.

In Windows, C:\Program Files is read-accessible Everyone group.
How do I mimic the same in Linux/Ubuntu ?

Thanks

---

### Post by ddales on 2008-06-22
You can use the "users" group or create a new group called "everyone" if it doesn't already exist.  The change the permissions on the /programs to allow the chosen group to read and execute.  Add users to the group and you're all set.

For example (as root or with root privileges):

* groupadd everyone
* vi /etc/group  (add your users to the group by placing their usernames seperated by commas at the end of the group line)
Like this:  everyone:x:1234:user1,user2,user3
* chmod 755 /programs

If you're using Samba to share the /programs directory you'll have to adjust your Samba settings as well.  Search for a Samba how-to on how to get that to work.

---

