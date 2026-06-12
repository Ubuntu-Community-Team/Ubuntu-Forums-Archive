---
title: "rsync / grsync doesn't perform 2-way sync?"
date: 2016-06-13
forum: General Help
---

### Post by jub2 on 2016-06-13
I need to sync a few folders on Ubuntu my laptop with a few folders on my Windows desktop. 

I thought grsync would work for this, but it seems grsync is a one-way sync. If I add files to the destination folder, they are not being synced to the source folder. So I assume any changes to destination folder files would also not be synced back to the source folder (and probably overwritten by the older source folder file if this isn't optioned out).

Am I doing something wrong or does grsync (a GUI for rsync) not have a bidirectional sync capability?

OK, it looks like Unison GTK performs a two-way sync, so I installed that, but I'm running into a permissioning issue in writing to the Windows shared folder.

I installed cifs-utils, then
> sudo mount.cifs //winPC/documents/synced_files /mnt/winPC/synced_files -o user=jub2

Then I set up a sync in Unison to sync "/mnt/winPC/synced_files" and "/home/jub2/Documents/synced files". It syncs, but any changes in the latter folder do not get synced back to the Windows shared folder because permission is denied. I'm guessing it's because root is the owner of the Windows shared folder. And I cannot take ownership by executing
> sudo chown -R jub2: /mnt/winPC - this gives me ownership of "/mnt/winPC", but not "/mnt/winPC/synced_files" as long as the Windows shared folder is mounted there. Once I umount "/mnt/winPC/synced_files", then I can take ownership of this folder.

How can I get permission to write to the Windows shared folder?

Separately, when I set up the folder pair in Unison (what Unison refers to as a profile), I selected Synchronization Kind "Local" since the Windows shared folder was mounted. The other options are "Using SSH", "Using RSH", "Through a plain TCP connection". Not sure if I should be using one of these options instead.

Edit: rsync, and by extension, grsync are indeed unidirectional sync apps.

---

### Post by TheFu on 2016-06-14
rsync is 1-way, but you can swap the source around.  Run in 1 direction first, then in the other. That will get the ¨latest¨ version of any files onto both boxes. Of course, the time needs to be correct enough on both systems involved or you might end up with an older file over-writing.  It is best to have 1 ¨system of record¨ and make all changes on it, if you are using rsync.  

Sorry. Don´t know anything about unisom.

When using non-Linux file systems, the easiest way to allow write is to set the owner and group permissions at mount time.  If the storage is not directly accessed (HW connected) to a Windows PC, then it is best to use Linux file systems. Windows can connect to those over the network using samba and other Unix systems should use NFS .... IMHO.  

If unison supports ssh, I´d use that. It would be secure over the internet. Just be certain to use key-based authentication. rsh shouldn´t be used, er, anywhere since around 1994-ish (like telnet and plain ftp).  rsync works over ssh by default, so be certain to setup key-based ssh connections.

Please use ¨code tags¨ not ¨quote tags¨ when displaying code.  The spacing is hard to see. It doesn´t appear to be correct above, but I cannot be sure due to the font.

---

