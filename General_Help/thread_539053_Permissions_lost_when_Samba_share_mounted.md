---
title: "Permissions lost when Samba share mounted"
date: 2007-08-30
forum: General Help
---

### Post by mossblaser on 2007-08-30
When I connect to a samba share on my ubuntu server I am able to browse the files with all the permissions exactly as expected. When I mount the same share using cifs the permissions become messed up. What appears to be happening is that the User ID of the file's owner on the server is being looked up on my computer (where the User ID obviously corresponds to a different user) and that local user with the same user id as the remote one becomes the owner. This can lead to the problems because I cannot access files I should be able  to and that every file I create I am not allowed to change because I do not own it and it is only writable to its owner. Using the samba server using ubuntu's network browsing functionality is not good enough - its very slow and many applications do not fully support it (besides as a permanent solution it is too messy). Oh and it is also critical that user permissions display and work correctly when mounted (so making mount show all files as fully read/writable is not a useful solution).

Examples of what I am finding are:
A folder on the share when connected with ubuntu's connection utility
```
  Own Grp Oth Owner Group
d rwx rwx rwx jonathan shareAdmins
```

The same folder on the share when mounted using cifs
```
  Own Grp Oth Owner Group
d rwx rwx rwx jamesw vboxusers
```

In the examples above the user jamesw on my computer has the same User ID as the user jonathan on my server and I believe this is what is causing the problem.

If I have not been clear enough please tell me! Thanks in advance for all help!

p.s. I have been googling around for a solution to this problem for the past few hours - my guess is I am not searching for the correct things...

p.p.s. Mounting with smbmount (smbfs) does not help

---

