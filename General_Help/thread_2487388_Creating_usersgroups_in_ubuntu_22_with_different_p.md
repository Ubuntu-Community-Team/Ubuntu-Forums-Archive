---
title: "Creating usersgroups in ubuntu 22 with different permissions"
date: 2023-06-02
forum: General Help
---

### Post by sjbasu on 2023-06-02
Hello Veterans,

I have installed ubuntu 22 in my server. Now I need to create 3 users [Bio1, exec and intern] apart from root. Now I am having two main queries:

1. how do I create these users so that all **gets to see** the entire directory structure ?
2. But **user: intern** gets read/execute access to **only two folders** ? [they should be able to SSH using that username]

I have used adduser command but I can't SSH using it.

How do I go about ? Please advice.

Much appreciation in advance.

Regards,
Sangram

---

### Post by MAFoElffen on 2023-06-02
You can only set folder ownership to one use and group... But your can set permissions of that same folder in a granular manner via using 'acl', so that you can give same or differing access and permission to (multiple) Users or Groups:
RE: [https://manpages.ubuntu.com/manpages/jammy/en/man5/acl.5.html](https://manpages.ubuntu.com/manpages/jammy/en/man5/acl.5.html)

Basically, you implement it in this manner.
- user1
- user2
- user3

...and
- /data/Folder1
- /data/Folder2
- /data/Folder3

Create security groups. 
- managers
- interns

Use 'setfacl' to set permission of those folders to groups
```

sudo setfacl -m g:managers:rwx /data/Folder1/
sudo setfacl -m g:interns:rwx /data/Folder1/
sudo setfacl -m g:managers:rwx /data/Folder2/
sudo setfacl -m g:interns:rwx /data/Folder2/
sudo setfacl -m g:managers:rwx /data/Folder3/

```
Check the access control list of the folders, to ensure access and permissions are set
```

getfacl -p /data/Folder1/  
getfacl -p /data/Folder2/
getfacl -p /data/Folder3/

```
Folder1 & Folder2 should be accessible with read, write and execute by both security groups. Folder3 in this example is set for only managers... You can see how you can modify that to very granular differences, right?

Then- Set the User's memberships to their security groups
```

sudo usermod -aG managers user1
sudo usermod -aG managers user2
sudo usermod -aG interns user3

```
Understand the logic of doing it that way? Easier for management & administration to do it logically that way.

EDIT: As an Admin, you can test this by *'being'* that user, either via logging in as them, or *being them* via 'sudo su -l <username>. Do I need to explain more on that?

---

