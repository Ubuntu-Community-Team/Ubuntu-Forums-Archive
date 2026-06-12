---
title: "Samba shared directory and permissions"
date: 2008-06-02
forum: General Help
---

### Post by hymerman on 2008-06-02
Hi all,

I've got a file server set up with a big shared directory which contains files I want anyone with permission (via Samba) to be able to read and write to. Currently I only have one user, myself, on a remote machine. This has been fine, but now I'm doing things like automatically moving torrents downloaded by the server into this shared directory for a remote user to sort, and that user is unable to modify the files because they are owned by whichever other user put the files there. I can see this happening when one remote user puts a file in the share and another tries to modify it, too.

Is there some simple way besides setting up some combination of cron and chmod/chown to allow what I want?

Just to clarify, I don't want to set the storage directory to be readable and writeable by all (I don't want for example Apache to be able to delete my files), I want the set of users that can access it by Samba or otherwise to have read and write access.

Perhaps I just need to set up some 'sharers' group and hook that into Samba? Is that a common way to do this?

Thanks in advance!

---

### Post by Prospero2006 on 2008-06-02
Would a general samba username work?

Just one account that the people who log in know to use?

I am in charge of a middle school ubuntu classroom and all of my students log into the samba shares I have set up using the username: student.

?

---

### Post by hymerman on 2008-06-03
That would allow people to modify each others' files, which is halfway there, but it wouldn't allow  users to modify files of other things running on the server (say, cron dumping backups to storage or bittorrent moving completed files there) since the usernames wouldn't match.

Thanks for the reply :)

---

