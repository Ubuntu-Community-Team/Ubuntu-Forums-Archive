---
title: "Samba help: Write and read users"
date: 2006-12-16
forum: General Help
---

### Post by RichGuk on 2006-12-16
Hello,

I'm sure this has been asked a million times before, and yep there is search but found a lot of how to setup samba, I pretty much know that.

All I want to know is how can share a folder and have one user login that only has **read** privileges and then a different user who has **read/write** privileges.

Thanks,

Rich

---

### Post by gaebriel on 2006-12-16
Can you clarify what exactly it is that you're trying to do? Is there more than one shared folder? Do you want to do this within a domain environment? Do you want users to be prompted for a username and password and then be granted access depending on the user they give? ...

---

### Post by RichGuk on 2006-12-16
Hello,

There will be 3 shared folders, not a domain environment, and yes prompted for login and given diffrent access depending on the user name and password they supply.

So

going to \\box\storage 

and using;
"Rich" and password for rich will get me read and write

or type

"reavers" and its password and it just gives you read permission..

Thanks,

Rich

---

### Post by gaebriel on 2006-12-16
The easiest thing I can think of is to update the smb.conf share definition with the read list and write list options. Check out [http://samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2615626]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2615626") for more details. 

A better solution though may be to install the 'acl' package (`apt-get install acl`or open synaptic and search for getfacl), create the users in Ubuntu, then define posix file acls on the objects using setfacl. 

Let me know how this goes because there are other options to try. :)

---

### Post by RichGuk on 2006-12-17
Hey,

don't look for 24 hours or so and it gets lost pages back, anyhow I tried this and it seemed to work... not tested 100% but I think its working.

[storage]
  comment = TV, Films, Games, Apps, Downloads
  path = /storage
  valid users = reavers, rich
  admin users = rich
  read list = rich, reavers
  write list = rich
  force group = rich
  force user = rich
  read only = No
  create mask = 0775
  directory mask = 0775
  browseable = yes

Thanks for the help :).

---

