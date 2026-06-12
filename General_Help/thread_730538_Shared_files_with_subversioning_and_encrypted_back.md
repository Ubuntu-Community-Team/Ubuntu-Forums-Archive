---
title: "Shared files with subversioning and encrypted backup"
date: 2008-03-21
forum: General Help
---

### Post by michaelzap on 2008-03-21
I'm hoping that some folks here can give me some ideas for how they'd approach this situation:

A local NGO currently has a Windows 2003 server. They really only use it as a file server, although all of the 25 or so computers on their network log into a domain on it when booting up. User/Group privileges are managed on the server, and all users have access to one or more shared folders on the server. They would like to get rid of the Windows 2003 server and set up a FOSS alternative, and at the same time we will be switching most (but not all) of their client machines to (X)Ubuntu.

So obviously a Samba server would probably be a part of the new system. I've considered just using a network hard drive for this purpose, since they're simple and robust. There is no one at this NGO who will be able to administer a server properly, so simple is better and potentially more secure.

Now comes the interesting part: Security is a major concern here (some of this information could potentially mean life or death for affected persons), and we'd like to add some new features to the system. For one thing, we'd like to keep all files in an encrypted volume (probably TrueCrypt, since that way it could be accessed on a Windows machine if necessary). We'd like to have regular encrypted backups that can safely be stored off-site (TrueCrypt on external hard drives?).

There's some concern that files have disappeared or been moved inexplicably in the current system (there are volunteers and short-term employees here). So ideally we'd like to implement a system that logs every action by each individual user so that we can figure out why some of these things have occurred, and we'd also like to have a versioning system (Subversion?) that would allow them to recover previous versions of files if necessary. Alternatively we could just make sure that our nightly backups are versioned if the extra complexity of checking out files and whatnot seems to be more trouble than it's worth.

Is there a particular system that people would recommend in this situation? Or would Samba with TrueCrypt volumes and rsync for backups be the best way to go? If there were something like WebDAV that would centralize all of their needs into one system that was easy to administer I think that would be perfect.

Thanks in advance for your suggestions!

---

### Post by michaelzap on 2008-03-25
No one has any ideas or suggestions?

---

