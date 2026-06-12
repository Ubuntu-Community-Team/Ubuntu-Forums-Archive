---
title: "Songbird"
date: 2008-03-06
forum: General Help
---

### Post by sefs on 2008-03-06
Hi is it true that songbird is based on the mozilla thing?

When we install firefox it installs with files that are under the control of root i believe, as it's installed in /opt or some other root controlled directory

I have heard it said that you should never run firefox if the files are owned by "user"

For instance when we have to update firefox for those of us who download it from mozilla we have to run a chown command to set the files to current user and then immediately after chown back to root.  I've read somwhere that this is important

Songbird on the other hand is installed to a path in the users home dir and the files are under the control of that user.  Since songbird seems to be based on the mozilla codebase thing, and you can browse the web somewhat in it...is this a security risk and a vector for an attach.  Should song bird files really be chowed to root  and installed into /opt like any other mozilla application?

Thanks.

---

