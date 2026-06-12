---
title: "Sharing files to Windows computers from Ubuntu, question about Samba permissions"
date: 2016-06-25
forum: General Help
---

### Post by Cursed Lemon on 2016-06-25
Alright, so I'm trying to create a little makeshift "media server" here at home and I'm trying to configure the Samba permissions correctly. 

I have one system/Samba account on the server. What I would like is to log onto the server from Windows explorer as the admin account and be able to add/delete files from the Samba share, but have other users log on as a guest (preferably with no needed credentials) with read-only access.

What would I have to do to make this work? I've read up on some of the documentation but it's not working out too well for me at this point.

---

### Post by TheFu on 2016-06-26
1st, you don't need to allow "admin" access over samba to let 1 userid control the files and all others use only guest.
2nd, the way I'd do it is to setup 2 different samba "shares" - just to the same storage.  a) for the userid which controls the files and b) for all guest users. Give them different share names.  Make the userid which controls the files own all the files on the native Linux side. Use Linux storage for the files. One last tip - put the shared storage outside the /home directory structure. Using /home causes some things to happen which could complicate this configuration. Best to avoid it.

To get started, please post what you've done already and post the output from **testparm**.

When I read a post like this, I think ... why doesn't he just use Windows?  He wants to only access it from Windows. He wants it to behave like Windows. He doesn't say way Linux is being used at all ... why not just use Windows?

OTOH, if the OP really wants a media server, why not deploy a media server - something like Plex. It would be easier than dealing with samba and only he would need to know anything more useful, like sftp to manage files.  Use WinSCP from windows to manage the files. Everyone else would use a DLNA client or web interface to access the media on the "media server." It is sorta like majic. Plex isn't F/LOSS, but it is free. No need to get a plex account or sign up with the Plex people in any way for this to work on the same subnet.  In fact, with a little knowledge, you don't need their account to stream anywhere in the world either - just use a vpn into your home network.

---

### Post by HermanAB on 2016-06-26
Also note that the easiest file server to set up is always anonymous FTP.  You can do that with filezilla server and client on Windows.

The most difficult server to set up is SAMBA.  There are many others, e.g. http, webdav, nfs, nc, tftp...

---

