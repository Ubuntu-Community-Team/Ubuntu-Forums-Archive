---
title: "tracker.log keeps increasing in size"
date: 2008-01-30
forum: General Help
---

### Post by banda on 2008-01-30
the file /home/name/.local/share/tracker/tracker.log keeps increasing in size and becomes in excess of 100MBs within a few minutes!!,...

i think i have messed permissions a bit..

this is what gets filled up in the file 


> 29 Jan 2008, 11:47:19:913 - ERROR: failed to prepare query GetServiceID with sql SELECT ID, IndexTime, IsDirectory, ServiceTypeID FROM Services WHERE Path = ? AND Name = ?;
 due to code 26 and file is encrypted or is not a database
29 Jan 2008, 11:47:19:913 - ERROR: incorrect no of parameters 2 supplied to GetServiceID
29 Jan 2008, 11:47:19:914 - ERROR: parameter 0 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:914 - ERROR: parameter 1 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:914 - ERROR: execution of prepared query GetServiceID failed due to file is encrypted or is not a database with return code 21
29 Jan 2008, 11:47:19:914 - ERROR: unknown service Applications
29 Jan 2008, 11:47:19:914 - ERROR: failed to prepare query GetServiceID with sql SELECT ID, IndexTime, IsDirectory, ServiceTypeID FROM Services WHERE Path = ? AND Name = ?;
 due to code 26 and file is encrypted or is not a database
29 Jan 2008, 11:47:19:914 - ERROR: incorrect no of parameters 2 supplied to GetServiceID
29 Jan 2008, 11:47:19:914 - ERROR: parameter 0 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:914 - ERROR: parameter 1 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:914 - ERROR: execution of prepared query GetServiceID failed due to file is encrypted or is not a database with return code 21
29 Jan 2008, 11:47:19:914 - ERROR: unknown service Applications
29 Jan 2008, 11:47:19:915 - ERROR: failed to prepare query GetServiceID with sql SELECT ID, IndexTime, IsDirectory, ServiceTypeID FROM Services WHERE Path = ? AND Name = ?;
 due to code 26 and file is encrypted or is not a database
29 Jan 2008, 11:47:19:915 - ERROR: incorrect no of parameters 2 supplied to GetServiceID
29 Jan 2008, 11:47:19:915 - ERROR: parameter 0 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:915 - ERROR: parameter 1 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:916 - ERROR: execution of prepared query GetServiceID failed due to file is encrypted or is not a database with return code 21
29 Jan 2008, 11:47:19:916 - ERROR: unknown service Applications
29 Jan 2008, 11:47:19:916 - ERROR: failed to prepare query GetServiceID with sql SELECT ID, IndexTime, IsDirectory, ServiceTypeID FROM Services WHERE Path = ? AND Name = ?;
 due to code 26 and file is encrypted or is not a database
29 Jan 2008, 11:47:19:916 - ERROR: incorrect no of parameters 2 supplied to GetServiceID
29 Jan 2008, 11:47:19:916 - ERROR: parameter 0 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:916 - ERROR: parameter 1 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:916 - ERROR: execution of prepared query GetServiceID failed due to file is encrypted or is not a database with return code 21
29 Jan 2008, 11:47:19:917 - ERROR: unknown service Applications
29 Jan 2008, 11:47:19:917 - ERROR: failed to prepare query GetServiceID with sql SELECT ID, IndexTime, IsDirectory, ServiceTypeID FROM Services WHERE Path = ? AND Name = ?;
 due to code 26 and file is encrypted or is not a database
29 Jan 2008, 11:47:19:917 - ERROR: incorrect no of parameters 2 supplied to GetServiceID
29 Jan 2008, 11:47:19:917 - ERROR: parameter 0 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:917 - ERROR: parameter 1 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:917 - ERROR: execution of prepared query GetServiceID failed due to file is encrypted or is not a database with return code 21
29 Jan 2008, 11:47:19:917 - ERROR: unknown service Applications
29 Jan 2008, 11:47:19:917 - ERROR: failed to prepare query GetServiceID with sql SELECT ID, IndexTime, IsDirectory, ServiceTypeID FROM Services WHERE Path = ? AND Name = ?;
 due to code 26 and file is encrypted or is not a database
29 Jan 2008, 11:47:19:917 - ERROR: incorrect no of parameters 2 supplied to GetServiceID
29 Jan 2008, 11:47:19:917 - ERROR: parameter 0 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:917 - ERROR: parameter 1 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:917 - ERROR: execution of prepared query GetServiceID failed due to file is encrypted or is not a database with return code 21
29 Jan 2008, 11:47:19:918 - ERROR: unknown service Applications
29 Jan 2008, 11:47:19:918 - ERROR: failed to prepare query GetServiceID with sql SELECT ID, IndexTime, IsDirectory, ServiceTypeID FROM Services WHERE Path = ? AND Name = ?;
 due to code 26 and file is encrypted or is not a database
29 Jan 2008, 11:47:19:918 - ERROR: incorrect no of parameters 2 supplied to GetServiceID
29 Jan 2008, 11:47:19:918 - ERROR: parameter 0 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:918 - ERROR: parameter 1 could not be bound to GetServiceID
29 Jan 2008, 11:47:19:918 - ERROR: execution of prepared query GetServiceID failed due to file is encrypted or is not a database with return code 21
29 Jan 2008, 11:47:19:918 - ERROR: unknown service Applications

how do i fix this?

---

### Post by jeffus_il on 2008-01-30
If you don't use the search features of tracker, go to preferences>sessions and cancel it, and save your session, also remove the applet if its on your panel.
You could reinstall and say a little prayer.
You can go into the tracker preferences in the Preferences menu, and find any setting to do with a database and encryption.

---

### Post by banda on 2008-01-30
jeffus_il
thanks, i unchecked it in session and that seems to have worked

also found the bug report here [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/146243/](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/146243/)

---

