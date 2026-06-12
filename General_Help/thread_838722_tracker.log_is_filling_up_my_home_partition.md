---
title: "tracker.log is filling up my /home partition"
date: 2008-06-23
forum: General Help
---

### Post by komputes on 2008-06-23
On my eeepc, I usually have 1GB of space dedicated to my /home directory. After taking that /home partition and using it on an 8.04 installation, it seems that the following file starts taking up too much space:

/home/komputes/.local/share/tracker/tracker.log 

This file alone fills up my /home partition at 800MB. I have ended up taking "Tracker" out of my sessions, deleting the trackerd process and changing the permission to tracker .log to that bobody has write permissions to it. Whew!

What is it?
I'm guessing it's the tracker for searching files and words within files 

Why is it so big?
Iuuno?

How do I limit it?
Iunno?

Help! I need somebody. :)


Excerpt from tracker.log:
23 Jun 2008, 19:13:55:265 - ERROR: incorrect no of parameters 11 supplied to CreateService
23 Jun 2008, 19:13:55:266 - ERROR: parameter 0 could not be bound to CreateService
23 Jun 2008, 19:13:55:267 - ERROR: parameter 1 could not be bound to CreateService
23 Jun 2008, 19:13:55:267 - ERROR: parameter 2 could not be bound to CreateService
23 Jun 2008, 19:13:55:268 - ERROR: parameter 3 could not be bound to CreateService
23 Jun 2008, 19:13:55:268 - ERROR: parameter 4 could not be bound to CreateService
23 Jun 2008, 19:13:55:268 - ERROR: parameter 5 could not be bound to CreateService
23 Jun 2008, 19:13:55:269 - ERROR: parameter 6 could not be bound to CreateService
23 Jun 2008, 19:13:55:269 - ERROR: parameter 7 could not be bound to CreateService
23 Jun 2008, 19:13:55:270 - ERROR: parameter 8 could not be bound to CreateService
23 Jun 2008, 19:13:55:270 - ERROR: parameter 9 could not be bound to CreateService
23 Jun 2008, 19:13:55:270 - ERROR: parameter 10 could not be bound to CreateService
23 Jun 2008, 19:13:55:271 - ERROR: execution of prepared query CreateService failed due to no such table: Services with return code 21
23 Jun 2008, 19:13:55:271 - ERROR: CreateService uri is /usr/share//applications/screensavers/blinkbox.desktop
23 Jun 2008, 19:13:55:272 - ERROR: could not get file id for /usr/share//applications/screensavers/blinkbox.desktop - unable to continue indexing this file
23 Jun 2008, 19:13:55:273 - ERROR: failed to prepare query GetServiceID with sql SELECT ID, IndexTime, IsDirectory, ServiceTypeID FROM Services WHERE Path = ? AND Name = ?;
 due to code 1 and no such table: Services
23 Jun 2008, 19:13:55:273 - ERROR: incorrect no of parameters 2 supplied to GetServiceID
23 Jun 2008, 19:13:55:273 - ERROR: parameter 0 could not be bound to GetServiceID
23 Jun 2008, 19:13:55:274 - ERROR: parameter 1 could not be bound to GetServiceID
23 Jun 2008, 19:13:55:274 - ERROR: execution of prepared query GetServiceID failed due to no such table: Services with return code 21
23 Jun 2008, 19:13:55:276 - ERROR: failed to prepare query CreateService with sql INSERT INTO Services (ID, Path, Name, ServiceTypeID, Mime, Size, IsDirectory, IsLink, Offset, IndexTime, AuxilaryID) VALUES (?,?,?,?,?,?,?,?,?,?,?); 
 due to code 1 and no such table: Services
23 Jun 2008, 19:13:55:277 - ERROR: incorrect no of parameters 11 supplied to CreateService

---

### Post by sdennie on 2008-06-23
If you don't use tracker then go to System->Preferences->Searching and Indexing and disable indexing and watching.  It should be safe to then delete the log file.  Though, before deleting it, you may want to look in it and see what kind of messages it was spewing out that caused the file to get so big.

---

### Post by chrisccoulson on 2008-06-23
What is in the log? My tracker.log is 64 bytes...

---

### Post by komputes on 2008-06-25
@vor - I'm in Gutsy, System->Preferences->Searching is not an option in Gutsy (AFAIK)

I have posted my solution for this although I'm wondering why it happened only after I took a /home partition and mounted it from 7.10 to 8.04 and back to 7.10 again.


--

@chrisccoulson - I have posted what is in the log, it's that large paragraph that stars with:

"23 Jun 2008, 19:13:55:265 - ERROR: incorrect no of parameters 11 supplied to CreateService"

It simply keeps repeating itself.

---

