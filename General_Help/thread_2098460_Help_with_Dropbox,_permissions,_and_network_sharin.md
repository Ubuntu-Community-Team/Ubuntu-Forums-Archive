---
title: "Help with Dropbox, permissions, and network sharing documents"
date: 2012-12-26
forum: General Help
---

### Post by Cclips on 2012-12-26
So, as is, the setup is a server comp running Ubuntu 11.04 that is running dropbox. It uploads a Samba share folder as a backup service, and to provide cloud access to files and such. 

The issue I have, is that dropbox won't upload files that the server doesn't own. So if computer A tries to create a document on and place it on the server, it is set to own the document. Dropbox then fails to upload it.

I thus went in and changed ownership to get them to upload (changed to server owned) which worked fine, but now, not having ownership of the files, computer A is not able to edit/control/replace the files with newer versions. 

My initial thought, was to run Dropbox as root, and leave the permissions as is, but seem to run into trouble with getting it to do as such.

My other thought was a script to change the owner at a set time period (say midnight) enough time for dropbox to upload, and then change it back in the morning, but that also seems sloppy and unneccesary. 

Any ideas or help is greatly greatly appreciated.

---

### Post by Cclips on 2012-12-27
Bump. Anyone have any ideas?

---

### Post by Cclips on 2012-12-31
Still none? I don't imagine the issue is that complex :\

---

### Post by Cclips on 2013-01-02
New year bump.

---

### Post by Calinou on 2013-01-02
Make a group where both the server and "computer A" are in, then set the files to "read + write" for owner and group (eg. chmod 664 file_name).

---

