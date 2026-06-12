---
title: "Copy emails from mailbox from local server to remote"
date: 2006-11-13
forum: General Help
---

### Post by chrisdee on 2006-11-13
Hello. I wonder how I can copy emails from mailbox for a user from local server to remote server. I just installed Ubuntu 6.06 on a new machine, and want all the emails (for a spesific user) from the old server (ubuntu 5.10) over to the new one.

Any Idea how I do this ?

---

### Post by chrisdee on 2006-11-13
Is the nobody who knows this ?

---

### Post by chrisdee on 2006-11-13
I try again. Help would be apreciated

---

### Post by koenn on 2006-11-13
I'll have a try:

both machines need to be on a network so they can talk to each other. 

I don't know where your mailboxes are, byt i guess they're just files or folders, maybe in /home/*username*

On the new server, you need the same user accounts as on the old server, otherwise your users(s) wont be able to access the mailbox on the new server.
You can to this by copying the user accounts form /etc/passwd and /etc/shadow

Then, you need to copy over a network and make sure the 'modes' (ownership, user access rights, ...) of the directories and files are preserved. 

so, you can use (in a terminal) rcp, and check/change the permissions afterwards, or use rsync. 
you may have to install rsync first, then run it, eg like so:

```

sudo su
password:

apt-get install rsync
rsync -av /path/to/oldmailbox/ new_server_name/path/to/newmailfolder

exit

```

rcp is similar, but I'm not sure it preserves file permissions. 
also : do "man rsync" to see if you need any additional options and mind the use of a trailing / in /path/to/oldmailbox/ to make sure you get the ***contents*** of that directory

good luck.

---

### Post by chrisdee on 2006-11-14
Thanks:) I'll try this.

---

### Post by koenn on 2006-11-14
correction: 

rsync -av /path/to/oldmailbox/ new_server_name**:**/path/to/newmailfolder

---

### Post by hashimoto on 2006-11-14
If I recall correctly I did this in Thunderbird simply by draggin the emails from the one folder to another. In my case i dragged all email from an old pop-mail account into my new imap-inbox. Not sure if this is what you are looking for...

---

