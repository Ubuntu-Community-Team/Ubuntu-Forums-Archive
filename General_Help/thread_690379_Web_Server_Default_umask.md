---
title: "Web Server Default umask"
date: 2008-02-07
forum: General Help
---

### Post by mahousaru on 2008-02-07
Hiya all

I just want to check to make sure I am not going to make a huge security boo boo.

I'm setting up a web server with multiple users, they will be accessing their files and the web pages in various ways such as ftpes, samba and scp.

Now currently I have set the default mask to 027 and to control access to the various web pages I am using multiple groups with g+s on the folders so their inherit the group.  One issue that keeps cropping up is that the lazy... I mean more efficient users don't want to keep adding write rights to files.

After auditing the files on the server I have concluded that any member of a group should be allowed to modify or delete the contents of a folder associated to the group.  So if I set the default umask to 007 will I open up any additional security holes?

The contents of the server should be for the web, but users do keep files in their home directories which are considered private.

Many thanks

---

