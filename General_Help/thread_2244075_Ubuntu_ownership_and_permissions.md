---
title: "Ubuntu ownership and permissions"
date: 2014-09-13
forum: General Help
---

### Post by gopukrishnan on 2014-09-13
I have two users testuser2 and testuser1 with homedirectories /home/testuser2 and /home/testuser1 respectively. I want to share the directory /home/testuser1/Videos/ and its contents across these two users. I did the following :
1. Created a group named ggg and added both users testuser2 and testuser1 to it
2. Changed the ownsership of /home/testuser1/Videos to testuser1:ggg from testuser1:testuser1
3. Set acl to group ggg having permission rwx on /home/testuser1/Videos
4. Set sgid to the directory /home/testuser1/Videos

Now I created a soflink to /home/testuser1/Videos inside the directory /home/testuser2/Desktop/testuser1 so that both testuser1 and testuser2 would be able to add/edit/remove directories. While testing I came across the following scenarios which I would like to get clarification you guys.

A) Copying files by testuser1 :

I have copied a file from /home/testuser1 (say examplefile1 testuser1:testuser1 644 ) to /home/testuser1/Videos and I could see that the ownership of the file changed to testuser1:ggg successfully. 

1.How can I change the permission also automatically to the one I need (group permision to rwx) if someone is copying files to my destination? 

2. If I am copying a file with 444 permission, then testuser2 wont be able to write to it. Thats normal since it is 444, but he is able to delete it. How ?

B) Moving files by testuser1 :

Comparing with the copying, while moving the files, ownership is not changing to testuser1:ggg. It keeps testuser1:testuser1 and keeps what the actual permission is.

1. How can I change the permission AND ownership to the one I required automatically ?
2. Same case as copying, testuser2 is able to delete the file but not able to write if the file is having permission read only.Why ?

I have tried to explain as much as possible. Please let me know the answers for A and B sections. Thanks guys

---

### Post by Lars Noodén on 2014-09-13
Have you tried setting the set-group-ID bit for the shared directory?

---

### Post by Impavidus on 2014-09-13
A2 and B2: Modifying files is controlled by the write permission on the file. Deleting files is controlled by the write permission on the directory.

---

### Post by bab1 on 2014-09-13
> **gopukrishnan said:**
> I have two users testuser2 and testuser1 with homedirectories /home/testuser2 and /home/testuser1 respectively. I want to share the directory /home/testuser1/Videos/ and its contents across these two users. I did the following :
1. Created a group named ggg and added both users testuser2 and testuser1 to it
2. Changed the ownsership of /home/testuser1/Videos to testuser1:ggg from testuser1:testuser1
3. Set acl to group ggg having permission rwx on /home/testuser1/Videos
4. Set sgid to the directory /home/testuser1/Videos

Now I created a soflink to /home/testuser1/Videos inside the directory /home/testuser2/Desktop/testuser1 so that both testuser1 and testuser2 would be able to add/edit/remove directories. While testing I came across the following scenarios which I would like to get clarification you guys.

A) Copying files by testuser1 :

I have copied a file from /home/testuser1 (say examplefile1 testuser1:testuser1 644 ) to /home/testuser1/Videos and I could see that the ownership of the file changed to testuser1:ggg successfully. 

1.How can I change the permission also automatically to the one I need (group permision to rwx) if someone is copying files to my destination? 

2. If I am copying a file with 444 permission, then testuser2 wont be able to write to it. Thats normal since it is 444, but he is able to delete it. How ?

B) Moving files by testuser1 :

Comparing with the copying, while moving the files, ownership is not changing to testuser1:ggg. It keeps testuser1:testuser1 and keeps what the actual permission is.

1. How can I change the permission AND ownership to the one I required automatically ?
2. Same case as copying, testuser2 is able to delete the file but not able to write if the file is having permission read only.Why ?

I have tried to explain as much as possible. Please let me know the answers for A and B sections. Thanks guys

I'll answer this from a different point of view.  You should not do any of the above **except** using **sgid** to set the group ownership.  If you have data you want shared you should store that data in a different file system.  You can use /data or /srv or even (heaven forbid)  /home/data.  In this manner no specific user will need be the owner of the files that are created (saved) in the directory and no need for sym-links.  The system umask sets the permissions upon **creation ** of the object.  This should be 0775 for subdirectories and 0664 for files.  If you move or copy a file you will not be creating the file so you will have to change the permissions with the tool *chmod*.  See ```
man chmod
```... you can script this.

If you need to change the ownership you can use the tool *chown*. See ```
man chown
```... you can script this also.

The problem you are having is due to the objects carrying their ownership and permissions from their original creation.  The method I outlined assumes that all files that are shared are created in the shared directory and therefore have the correct user and user group and that umask sets the correct permissions.

Methods of creating a file can be "saving" a file or "cut and paste" a file.  Moving or coping a file will always be problematic for this type of setup.

---

