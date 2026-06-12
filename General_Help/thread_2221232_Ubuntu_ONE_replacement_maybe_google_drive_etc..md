---
title: "Ubuntu ONE replacement maybe google drive etc."
date: 2014-05-01
forum: General Help
---

### Post by MikeCyber on 2014-05-01
HI
I need a place to share my uploads. So best a folder that I could simply give the download link and the users could download whatever content they want.
I've tried google drive, but it seems as if I can't download items in a shared folder? For ex. it opens zip files but not downloads. Am I doing something wrong or you have an alternative?
Many thanks

---

### Post by TheFu on 2014-05-01
If you intend to share the files with the entire world, any of the online storage services can be used - box, g-drive, whatever Microsoft uses, whatever Apple uses, plus there must be 20 others like dropbox.

Heck, you can get a web hosting service for $20/yr.

If you want to control access, then using something like owncloud behind a VPN would be smarter or even just setup an sftp folder that you can share with selected people. You can probably host this yourself on any broadband connection.

"Shared folders" are usually done via CIFS. CIFS is NOT secure and generally blocked by every ISP in the world due to that. They are protecting end-users from themselves.  **sftp** is a better alternative for similar capabilities.

So - which protocol do you want to use?  SFTP, HTTP, something else?  This will determine which client programs can access the storage.

---

### Post by dannyboy79 on 2014-05-01
dropbox is the easiest IMO and has a linux client. of course you could host something yourself but this is using existing hosting services.

---

### Post by MikeCyber on 2014-05-01
I have just looked at dropbox and they want me to download and install a app. I want to upload some *.zip or *.7z files and give the link of the parent folder to my users. So they could check for updates themselves, but I don't want everyone to find it. Google etc. any searchengines must stay away...
So should I install dropbox, will that do the job?
Thanks

---

### Post by TheFu on 2014-05-01
If you don't want a search engine to find it, then do not put it on the internet without requiring a login and strong password.

---

### Post by Paulgirardin on 2014-05-01
> **MikeCyber said:**
> I have just looked at dropbox and they want me to download and install a app. I want to upload some *.zip or *.7z files and give the link of the parent folder to my users. So they could check for updates themselves, but I don't want everyone to find it. Google etc. any searchengines must stay away...
So should I install dropbox, will that do the job?
Thanks

The dropbox client is in the repos.Get it using Software Center

---

### Post by MikeCyber on 2014-05-02
Thanks. Hmm I'll have a look at google drive today as it's possible to download zips etc. Anyone knows how their mailing list works. Do those contacts need to be google accounts or any emails? How to upload contacts? Could they get to me asking for permission? That would be the easiest for me.
Thanks

---

