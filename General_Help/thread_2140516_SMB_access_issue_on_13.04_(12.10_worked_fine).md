---
title: "SMB access issue on 13.04 (12.10 worked fine)"
date: 2013-04-29
forum: General Help
---

### Post by fr33z0n3r on 2013-04-29
I just upgraded to 13.04.  I have found that SMB access (via Files "Connect to server" - previously Nautilis) is not working as in 12.10.  I use my Ubuntu desktop as a client to my Windows Server that I have.  I have lost the ability to browse files.  It does not prompt me to provide credentials anymore.  I will not modify my Windows server security to account for this apparent breaking change in Ubuntu.  Not even to troubleshoot.

I have a lot of files that are on that server.  It almost seems like it is refusing to allow for alternate credentials.  If I can control that then I could presumably connect in Files.  _Why did the Connect To Server dialog box get changed to remove this functionality?_

Does anyone know what happened?  Did they change library support or something?  Can I regain this functionality?

This is a showstopper for me.  If this is a "deal with it" kind of change, then I'm reverting to 12.10 and never coming back up.  I require a user-friendly way to enter alternate creds.  I'm not going cmd on this every time.  But let me know options so I can continue to access my files at least until I can block out a day to revert.

Thanks in advance!

---

### Post by fr33z0n3r on 2013-04-30
ok, wow.  I feel both stupid and shocked.  The functionality is there, but you MUST enter the URL like this:
smb://username@ipaddressOrName/Share

If you leave off the username, you are hosed on that "bookmark" forever - unless you edit it in Bookmarks.

It isn't smart enough to either prompt you for credentials, or prompt you AFTER it knows you've failed to connect.

Terrible usability change.  Absolutely horrible design change.

---

