---
title: "Samba shares with mutiple users"
date: 2014-02-05
forum: General Help
---

### Post by SchnappiJedi on 2014-02-05
Samba shares are very difficult to configure correctly...especially for multiple users!

Sharing home folders works great/fine...for a single user.

It gets tricky when setting up a samba share outside of the home directory with multiple users. I assume that all files in a samba share need to have default owner of no-one (optional) and more importantly read/write access to everyone and defaulting to this for new files and folders in the samba share folder.

Once this is set does anything else need to be done? 

Also an admin user on ubuntu is automatically added to a group called sambashare. Do all users accessing the share need to be added to this group?

---

### Post by bab1 on 2014-02-05
> **schnappi2 said:**
> Samba shares are very difficult to configure correctly...especially for multiple users!

Sharing home folders works great/fine...for a single user.

It gets tricky when setting up a samba share outside of the home directory with multiple users. I assume that all files in a samba share need to have default owner of no-one (optional) and more importantly read/write access to everyone and defaulting to this for new files and folders in the samba share folder.

Once this is set does anything else need to be done? 

There is no need to set any specific user as owner when creating a share for multiple users.  There is no reason to add world (others) read/write permissions either.  What you do need is a path to the share that always has others with r-x permissions (read and eXecute).  This allows any user to traverse the path and read the contents of all the folders.  The group permissions are used to manage the access for multiple users. 
> 

Also an admin user on ubuntu is automatically added to a group called sambashare. Do all users accessing the share need to be added to this group?
No.  I have only users in my sambashare group.

I use the group *users* and set group inheritance of the file system I wish to share with multiple users.  For instance I have a Samba share at /srv/public.  The ownership and permisssions look like this```

drwxrwsr-x 9 root users 4096 Feb  2 14:26 /srv/public

```
The share definition looks like this```

[public]
        comment = Shared Data
        path = /srv/public
        browseable = yes
        guest ok = yes

        force group = users
        writeable = yes

        create mask = 0664
        force directory mode = 2775

```

---

### Post by SchnappiJedi on 2014-02-13
Thanks.

---

### Post by Roasted on 2014-02-13
Not sure if this will help or only cloud the situation more, but here's what I do...

I have one "samba" share, located at /media/storage. All users have access to this share. From there, the samba bit is pretty much over. At this point only rwx permissions control who can go where. 

Within /media/storage, I have a series of what I call top tier folders. These top folders include things like, backups, documents, music, pictures, public, videos, etc. I create a group identically named to each one of these top folders, and that group gets assigned to the corresponding folder. Then I add the users to the group that should have access to that folder. For example, to edit files in /media/storage/documents the system requires you to be in the documents group. Why? Because 770 permissions. 770 = Owner, Group, Others. With 7 being read/write/execute, and others having a 0 (no access), 'others' cannot do anything. Of course, I can lessen the restriction to 775 if I wish, giving 'others' read/execute access, but I choose not to for my own reasons.

Same goes for the other top folders as well that I mentioned above, backups, pictures, etc. 

So in short, I have 1 samba share everyone has access to, and several "top" folders with corresponding groups for each, then I adjust rwx permissions accordingly to who can go where.

drwsr-sr-x   7 jason backups    4096 Oct 26 23:48 backups
drwsrws---   6 jason documents  4096 Feb  5 00:04 documents
drwx------   2 root  root      16384 Jan 31  2013 lost+found
drwxrwx---   7 jason motion     4096 Nov  3 01:50 motion_feeds
drwsrws--- 148 jason music      4096 Feb  5 14:06 music
drwxr-xr-x   3 root  root       4096 Jan 26 15:41 owncloud
drwsrws---  31 jason pictures   4096 Feb  4 22:45 pictures
drwsrwsr-x   6 jason public     4096 Feb 13 23:25 public
drwsrws---   8 jason videos     4096 Nov  3 01:38 videos

As you can see I am a believer in only giving users access to what they need. I don't really like having anything else open to 'others' for security (and personal) reasons. I'd rather have to add the users I need to see the data as opposed to letting everybody in to a certain degree via the others category. As you can see, public is an exception as public has read/execute. This folder is mostly a spare dumping zone with lesser restrictions that I play with. If it helps, I also create a generic 'guest' user, mostly because I haven't had consistent luck using 'guest' access in samba. This of course stems back to my early (2005) days with samba, so it may be better now, but I like having that generic user account for that purpose. AKA - "user" with a generic password that I give out willingly.

Fun fact - If you add the hide unreadable flag into the smb.conf, it'll make everything that the user doesn't have access to disappear from their sight. This, in my opinion, makes a lot of sense as it takes out any sort of frustrating trial-and-error a user might be dealing with to see what they have access to. What you see is what you get. Need more? Talk to me. :P

hide unreadable = yes


Hope that helps.

---

