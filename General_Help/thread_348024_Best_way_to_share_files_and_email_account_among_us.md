---
title: "Best way to share files and email account among users on same machine"
date: 2007-01-28
forum: General Help
---

### Post by flayspray on 2007-01-28
Hi All,

I would like to know if anybody has some suggestions on the best way to share files and maybe an email account between two users on the same machine. 

I have two users on the same machine, each with their own account and own home directory. How could I best make the same files available to both? Would you suggest setting up a /common directory under home and giving ownership of it to a group and then making both users part of that group? Or something else?

Also, how about sharing an email account? Say for example I'm using Thunderbird. Is there a way to set it up so that emails and settings for a common email account are also saved in this /common directory?

What have you all tried?

Thanks much in advance for your help!

---

### Post by andreas64 on 2007-01-28
Hi,

I've created an extra partition to share common data. I Think this is the most secure way.

And yes - you can copy the Thunderbird-profile-directory (~/.thunderbird) to that common directory and point Thunderbird to the new profile for both accounts.

Andreas

---

### Post by flayspray on 2007-01-28
Thanks for the info. I think I'm going to try that now.

As far as setting permissions for all users so that they'll have full access to the files on that partition, I found a thread that explains how to set it up quite easily using ACL:

[http://www.ubuntuforums.org/showthread.php?t=145741&highlight=acl](http://www.ubuntuforums.org/showthread.php?t=145741&highlight=acl)

Thanks again.

---

