---
title: "chmod and permissions issue for admin"
date: 2008-03-19
forum: General Help
---

### Post by elbeano on 2008-03-19
On a system with multiple users, I want to give one user the ability to create/modify files in users' directories. I've done this by making the privileged user a member of each user (group).  This still doesn't accomplish what I want because new files they create end up being inaccessible to users, since the new file is owned by the privileged user. When users create new files, they default to read-only access for their group.

I want users and the privileged user to be able to create and modify files in users /Documents folder... How do I go about this?

---

### Post by elbeano on 2008-03-19
I am looking at utilizing ACLs for this, so unless forum users want to give me a heads up about issues with those... standby... I will report my results.

---

### Post by scramasax on 2008-03-19
> **elbeano said:**
> When users create new files, they default to read-only access for their group.

The group needs read-write access.  You have to change the umask.  A a umask of 002 permits write to user *and* group on newly created files.

What you have on Ubuntu is a system where there are "private groups" -- that is to say, each user has his own group.

[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-users-groups-private-groups.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-users-groups-private-groups.html)

That system was devised in order to make sharing easy but personal files not writable -- because the umask can be set, so that files are created rw-rw-r-- *but* personal files can still stay non-writable if they are created with the group set to the individual owner rather than to the group set up to allow sharing.

Note what's said in the linked document:

> If you set the setgid bit on a directory (with chmod g+s  directory), files created in that directory will have their group set to the directory's group. 

You need to make a group for sharing -- call it "staff", say.  Each person has a directory for sharing that has the group set to that.  But their personal files in other directories can still stay non-writable.

---

### Post by elbeano on 2008-03-22
Adding ACL capability has turned out to be the only satisfactory option. I needed to keep the limited users from reading each others' files, so creating a sharing group and making the users members of that was not an option. I'm happy with ACLs. Just to add basic instructions for getting them:
(remember that the following is an example, depending on your setup the details will likely be different)

sudo apt-get install acl

then modify /etc/fstab, adding acl functionality to whatever partitions needed:

# /dev/hda3
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  /     ext3    defaults,acl,errors=remount-ro     0     1

remount:
sudo mount / -o remount

To add GUI support for ACLs:

sudo apt-get install eiciel

---

