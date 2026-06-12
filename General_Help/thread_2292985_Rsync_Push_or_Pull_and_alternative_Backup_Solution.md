---
title: "Rsync Push or Pull and alternative Backup Solution that does Compressed Incrementals?"
date: 2015-09-01
forum: General Help
---

### Post by jeff140 on 2015-09-01
[COLOR=#333333][FONT=Arial]Trying to device a backup solution for an Ubuntu machine.  I'm doing a file backup using rsync but the rsync is run on the destination device and pulls the files over.  I'm wondering if this creates and issues with copying over files that are open and if so, does running the rsync on the source device and pushing the data resolve that?[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Second issue is I'd like to create a block level incremental backup of the whole server and prefer and open source or low-cost solution (not one of these $1K-$2K products.)  It's widely know that most open source solutions can't do incremental AND compressed. So that rules out rsync and other software based on it like FWBACKUPS.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]However I did discover that ZIP has a -FS options which essentially pulls it off!  However using zip isn't going to product a file that you can use to re-image the whole server. I also don't know how ZIP is going to handle open files (as good as rsync?) You would have to re-install the O/S and then restore the zip file.  Interestingly, while in the past, permissions and ownership were not saved in the zip but I've read reports that more recent versions do on Linux zip files. Can anyone confirm this?[/FONT][/COLOR]

---

### Post by papibe on 2015-09-01
Hi jeff140. Welcome to the forum ):P
> **jeff140 said:**
> does running the rsync on the source device and pushing the data resolve that?
Not really.

For system files, it is better to rsync over on offline system. For databases, it is better to rsync dumps not live databases.
> **jeff140 said:**
> However using zip isn't going to product a file that you can use to re-image the whole server.
This make me think your main concern is to recover a system, not data.

I would suggest looking into file systems that are able to do snapshots. Once you have the snapshots, you can rsync them wherever you want without concerns about integrity.

I know both BTRS, and ZFS support snapshots.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by lukeiamyourfather on 2015-09-02
> **papibe said:**
> I know both BTRS, and ZFS support snapshots.

It looks like ZFS hits all the points the original poster is looking for. If the server is running ZFS on the root then snapshots could be backed up to another host running ZFS. With ZFS entire file systems bit for bit can be sent between hosts (anywhere in the world) including all metadata and snapshots. It's also incremental and compressed.

---

