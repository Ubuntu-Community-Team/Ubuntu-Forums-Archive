---
title: "Webserver and general understanding of rights"
date: 2008-06-23
forum: General Help
---

### Post by _godbout_ on 2008-06-23
Hi there!

I've got a quick question about the rights in a Linux system. I know how this owner/group/other rights work, or at least I thought.
Then I installed a webserver, and I had to give it access rights on a folder. I found a way to do it, by chgrp of the folders where I want the webserver to have access.
But, I don't really then understand something. The rights for the folder where dedicated to 1010/1010 for user/group. Now it's changed to 1010/www-data. So, I correctly changed the group restriction to allow apache to access it, but what about the owner?!

I mean, I thought that the group was the group where the user belongs to. Here, I was able to change the group to www-data, but the user is still 1010 (I don't know what is this number related to who, actually?). Does that mean that 1010 is also a member of group www-data, or does that mean that the rights now are related to a group which is not related to the user?

Anyway, it works, but I don't really understand how :D

Thanks in advance!
Guillaume

---

### Post by HalPomeranz on 2008-06-24
The owner and group owner of a directory are totally independent of one another-- it's merely coincidence that they happened to be set to the same numeric value on your original directory.  In fact, those two numbers describe values in completely different sets.

What's going on here is that the owner value is what's usually described as a "user ID" (aka UID) in Linux/Unix.  User IDs are associated with user names in the /etc/passwd file (the first column of this file is the user name, the third column is the user ID number).  Similarly the group owner value is a "group ID" (GID), which is associated with a group name via the /etc/group file.  User ID 1010 is a completely different animal from group ID 1010.

The fact that you were seeing the number "1010" in file listings means that there's no /etc/passwd entry associated with user ID 1010 and there's no /etc/group entry for group ID 1010 either.  I'm sort of curious how you ended up with these ownerships-- did you copy these files from some other machine?  In any event, it would probably be a good idea to make everything that's currently owned by user ID 1010 owned by some other user-- perhaps the root user (UID 0).

---

### Post by p_quarles on 2008-06-24
Just want to expand and clarify a couple things from HalPomeranz's reply. First of all, I would say that user owners and group owners are unrelated -- since normally there would be very little use for completely different settings for the two -- but they are basically independent. 

Anyway, think of it this way: a user owner is a single account that has a defined set of permissions. However you define this owner's permissions, they will only apply to a single account. Group ownership, on the other hand, sets permissions for every user in that group. In other words, if you wanted to give two users -- but not all users -- the same access to a file, you would make them both members of the group that owned that file. 

Basically, ownership and permissions together allow for very exacting control over who accesses what and how. 

For Apache, specifically, the current setting will work, but it's also kind of unnecessarily permissive. Only one user needs to operate the server, so setting user owner to www-data would make sense. That would be done with:
```
sudo chown -R www-data /var/www
```

---

