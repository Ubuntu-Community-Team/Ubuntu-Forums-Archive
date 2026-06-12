---
title: "Best Way to Share Files Among Users on a Single Machine"
date: 2008-05-27
forum: General Help
---

### Post by Roger Mudd on 2008-05-27
What's the best way to share files between two user accounts on a single machine? My machine has two users -- my wife and I. I'd like to make certain directories within my home directory available to her with read and write permissions.
I've looked into ACLs but haven't found a good guide which I can grasp. This looks like the most sophisticated/granular approach. Are Samba and NFS options? My initial impression is that both are designed for networked machines and not for this purpose specifically. Please correct me if I'm wrong.
Simply changing owner/group permissions on these directories hasn't been an option because those permissions seemingly effect only existing files. Any new files revert back to old permissions.
Coming from Windows and Mac, I'm looking for a solution similar to "Shared Documents" from Windows or "Shared" from OSX. 
Any help is greatly appreciated!

---

### Post by tact on 2008-05-27
I have a similar requirement on my machine.  What I did is create a folder "common" (as opposed to "shared") in /home.

That folder (/home) is owned by root so you have to use sudo to create another folder inside it.  Then you need to make that folder read/write to all users.
```
sudo mkdir /home/common
sudo chmod 777 /home/common
```

You can leave root as the owner so others cannot change permissions on the "common" folder.

This does not change the permissions on files placed in the "common" folder.  Anything your wife places there will be owned by her and have the permissions as set by here..  Files you put there have you as owner and permissions you set.

That works for me.  Might not suit you though.

BTW you are right - samba and nfs are not really useful for this purpose.

Cheers

---

### Post by Nepherte on 2008-05-27
Another possibility is to create a new group, for example 'share' and add you and your wife's user name to the group (system > manage > users and groups). Change the ownership of the map to a user of the group share and use the normal settings:
```
sudo chown -R yourusername:share /home/common
sudo chmod 0755 /home/common
```
This way only the persons that need to access the map, can actually do something with it.

---

