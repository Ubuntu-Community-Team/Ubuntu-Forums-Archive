---
title: "Encrypted Data"
date: 2007-11-12
forum: General Help
---

### Post by nickcoons on 2007-11-12
I've got sort of a complex situation that I need a little direction on.

I'm building a server that will house data on a partition for Samba, accessible to a Windows workstation.  This Windows user subscribes to an offsite backup service, whereby a client application is installed on the Windows workstation that periodically syncs the data with the server.  I would simply point the client app to the mapped server drive and tell it to keep all of that data backed up.

The information is fairly sensitive, so I want to keep it safe.  Ideally, we'd be able to back it up ourselves to an offsite location, but there are no other usable locations for us.  So even though we don't particularly want to, a third-party service is all we can come up with.

So here's the plan.  I'd like to have this data partition accessible in two ways, perhaps mounted in two directories, as such:

/var/data/normal
/var/data/encrypted

Now if I look at either of these directories, I would see the exact same file list and directory structure.  If I accessed a file under /var/data/normal, it would be an unencrypted version of that file that I could access without any problems.  If I accessed that same file under /var/data/encrypted, I would be accessing an encrypted version of that file.  So, for instance, double-clicking on a JPG file in /var/data/encrypted would not open that file, because it would be delivered to me encrypted.  But double-clicking on that same file in /var/data/normal would work just fine.

I would setup two Samba shares, one to point to each directory, such that the person on the Windows workstation would access the data on /var/data/normal, but the backup service's client app would access /var/data/encrypted.  That way, all data sitting on the backup service would be encrypted and inaccessible to anyone that, say, works for the backup service company.

I've thought of setting up a cronjob to copy /var/data/normal to /var/data/encrypted, encrypting each file on the way, but that would mean that I'd have to have no less than twice as much hard drive space as the total amount of data I had.

I'm looking for someone that might know how to accomplish this, or perhaps suggestions on other ways to accomplish the same end goal.  Thanks!

---

