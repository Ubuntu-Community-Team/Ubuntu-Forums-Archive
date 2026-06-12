---
title: "How delete folder with hard links (from rsnapshot)"
date: 2019-07-08
forum: General Help
---

### Post by WhiteTigerIT on 2019-07-08
Into a server 18.04 I've created some folders with rsnapshot, from this server and other remote servers.
Now I wish to remove the rsnapshot folders because they take up too much space.
In these there are hard links.

Can I simply remove the backup folder with all its contents or do I have to do any other procedure?
I do not want to delete the original files of this server and especially of the remote ones.

Thanks in advance for the help

---

### Post by HermanAB on 2019-07-08
A hard link is just another name for the same file.  You can simply delete the backup folder with something like rm -rf backup, but please triple check your syntax before you press enter.

---

### Post by Impavidus on 2019-07-08
Just another name for the same file. The file gets deleted when its last name is removed. No matter how many names the file has, it takes the space of one file.

---

### Post by The Cog on 2019-07-08
> **Impavidus said:**
> Just another name for the same file. The file gets deleted when its last name is removed. No matter how many names the file has, it takes the space of one file.
Exactly. 
But beware, if the filename in the backup folder is the last link to the file, then the file goes when you delete it.

---

### Post by WhiteTigerIT on 2019-07-09
I'm sorry, but I don't understand and I would like to be sure of what I'm doing.

There is a folder **/Backup/** with sub-folders
* hour.0
* hour.1
* hour.2
* day.0
* day.1


Each of these has two additional folders: **server1** and **server2**


With **rm -rf /Backup/hour.0**, do I only delete **only** the files in this folder or the original files on the two servers?

---

### Post by kpatz on 2019-07-09
You're only deleting the backups in hour.0.  The original files will still be on the servers/original locations (if you haven't deleted them from there separately).

The purpose of the hard links in rsnapshot backups is so that once a file is backed up, it just creates links to it instead of making multiple copies taking additional space.  So if a file is backed up on Monday, then the file is still on the server, unchanged, when Tuesday's backup runs, a hard link is created so that the backup of that file in day.0 and day.1 occupy the same space.  If the file is changed in between, a new copy is backed up rather than a hard link created.

If you delete hour.0, the links within that particular backup are deleted.  Any hard links in other locations (such as hour.1) will remain and the space will still be taken up by the files that still have links.  If there are files in hour.0 that aren't linked elsewhere, those files will disappear (from the backup, not the original location).

Hard links can only exist across files in the same file system (partition, mount point).  Every file in a file system has at least one link, the original one.  Additional links are just additional file names pointing to the same inode.  Deleting a link decreases the link count in the inode, and when the last link is removed, the file is deleted "for real".

---

### Post by WhiteTigerIT on 2019-07-09
Thank you all for the clarifications.

---

