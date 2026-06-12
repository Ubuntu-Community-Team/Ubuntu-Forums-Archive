---
title: "Samba woes with one client (others ok)"
date: 2014-12-18
forum: General Help
---

### Post by keith30 on 2014-12-18
I'm by no means an IT expert but I look after a small network in our office comprising of a Linux Server now running 14.04 and a handful of workstations with either XP or Win7. 

Very recently (possibly related to upgrading to 14.04) one of the XP clients is unable to connect to the shared folders. We have no need for security settings and as such I have security=share in samb.conf but the XP client now keeps asking for a user name and password of which there is none (it has occasionally done this in the past but clicking cancel allowed access). Windows Explorer can see the server and all other clients work fine. 

I have found that creating an new user account on the XP machine resolves this problem although that is not a practical solution as I would have to transfer all user settings etc for what should be a simple fix. I tried renaming the existing user but that trick did not work and I have tried net use /delete which results in a message that there are no entries on the list. I am assuming there is a cache of users somewhere and some corruption is demanding the credentials to log in. I have googled for many hours and tried various suggestions but as yet to no avail. I cannot establish whether it is a server or client issue.

Thanks in advance for any help

---

### Post by TheFu on 2014-12-18
Can the same user access the files from the Win7 machines?
Are you using Active Directory?

Have you manually reset the smbpasswd for that userid?

Just thoughts ... I don't know what will work. We stopped using XP last , er ... March when support ended.  XP on any network is a danger.

---

### Post by keith30 on 2014-12-20
Thanks for your suggestions. AFAIK I do not have Active Directory. I have tried accessing files on other Win7 PC's but that also seems to be troublesome though I suspect that is more to do with the security settings on Win 7 not playing ball with XP. As I have not managed yet in getting it to work I have started to migrate my files to a spare PC which runs Win 7.

---

### Post by TheFu on 2014-12-20
Seems you misunderstood.

The AD question was to find out if there were multiple users. The way you have it setup, every userid on each different PC is different. Samba doesn't look at that, it looks purely at the username.

If you post the smb.conf file, someone can probably point out the issue, assuming ping works from every machine to every other machine. Sometimes trivial network problems prevent connections.

---

### Post by keith30 on 2014-12-27
I think I understand you now. Each client only has one user account on it and no requirement to 'log in'. Also, there are no users in Samba, everyone gets access as a guest. If it answers you question to me, I did set up a new user on a Win7 machine with the same username that was causing problems and it got access to the files just fine.

Thanks for your help though. I have now replaced the XP client with Win 7 and all is working again. In due course I will need to set up user accounts with passwords, but at the moment we do not have any sensitive data on this server.

---

### Post by TheFu on 2014-12-27
Glad it is working. Please mark the thread as "solved" so others  can benefit (or ignore it).

Just to clarify - Samba is very complicated and can be configured in thousands of different ways - with/without userids or with external or internal authentication.  With the way YOU are using it on standalone systems only the text username matters. It is possible to allow everyone access, restrict that by subnet or use full networked userids to manage the access of files.  That just isn't the way you need it now, so I simplified the answers to get it working, not necessarily explain the inter-workings of samba authentication (which I'm honestly NOT qualified to discuss at all).

Before saying there isn't any sensitive data ... what happens if someone from off the street grabs all the data and posts it online as "nude photos of ..." so there are 1M downloads in 30 min?  Is it sensitive now?   

Almost always best to follow the standard security practice of least access possible to perform duties, and no more.

---

