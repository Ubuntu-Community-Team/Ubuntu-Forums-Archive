---
title: "[SOLVED] Trying to link a network file system"
date: 2008-04-08
forum: General Help
---

### Post by Peter09 on 2008-04-08
Most of my data is held on a network drive (nas1). I am trying to put a link so that evolution will use the network drive to store my emails as well.

I have linked the .evolution file to the 'real' file on the nas drive. Using a terminal I can see everything, I have write and read privileges and all seems ok.

When I run up evolution it can see the mailboxes and displays their contents but it errors with a permissions problem. -- Cannot append data to mailbox -- 

The fstab line looks like 
//192.168.0.8/nas1share	/media/nas1share	 smbfs defaults,rw,username=xxxx,password=xxxx,gid=sambausersgroup 0 0

Cannot figure why a terminal session works but evolution does not....

PC

---

### Post by dcstar on 2008-04-08
> **Peter09 said:**
> Most of my data is held on a network drive (nas1). I am trying to put a link so that evolution will use the network drive to store my emails as well.

I have linked the .evolution file to the 'real' file on the nas drive. Using a terminal I can see everything, I have write and read privileges and all seems ok.

When I run up evolution it can see the mailboxes and displays their contents but it errors with a permissions problem. -- Cannot append data to mailbox -- 

The fstab line looks like 
//192.168.0.8/nas1share	/media/nas1share	 smbfs defaults,rw,username=xxxx,password=xxxx,gid=sambausersgroup 0 0

Cannot figure why a terminal session works but evolution does not....

PC

Unless the fileshare provides the same functionality as a native Linux filesystem (which I doubt), then I seriously doubt something like Evolution will work over a share like that.

Evolution probably needs to open the file with an exclusive lock (for database integrity), and if the share doesn't support that then you may well get issues like you are experiencing.

Just because you can read and write "ordinary" files over a share does not mean that particular apps will work over them - this has been an issue since network file sharing was invented.

---

