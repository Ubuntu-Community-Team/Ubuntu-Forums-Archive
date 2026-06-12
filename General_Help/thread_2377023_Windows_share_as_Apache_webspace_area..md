---
title: "Windows share as Apache webspace area."
date: 2017-11-08
forum: General Help
---

### Post by grungeman2 on 2017-11-08
I'm trying to setup a websolution where IIS and Apache can share the same webspace user storage area and using the same AD-users.

Today i got most of it running fine, but there is atleast one last thing i need to crack or figure out if it is possible to do.  

On the Ubuntu 16.04 server running Apache using mpm-itk to run each vhost with a uniq isolated user, this works fine if i point the site to a mounted hard drive.  By the way im using the Active directory user there, I do not want to create any local user on the ubuntu server itself.  

**Main problem:** I added the windows share to fstab to be auto mounted using a windows admin account for the share. So far so good, but this makes the share only readable for the apache server, I need it to be writeable as well. The only solution for that so far is to mount the same share again but with the user of each specific website.  Which isnt a acceptable solution.  I'm looking for better solutions :) 

By the way, all of the above is working right out of the box running IIS and same share. 

/Peter

---

