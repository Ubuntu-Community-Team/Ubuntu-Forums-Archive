---
title: "Permissions/User Issue Writing to a Mounted NFS Share"
date: 2018-05-16
forum: General Help
---

### Post by nasha on 2018-05-16
Hi All,

I'm not sure when or how this problem became introduced, but after updating the OS (Server 16.04.4 LTS) packages, not version, and updating SABnzbd, Transmission and migrating from Sickbeard to SickRage, this problem arose and permissions have always been the weakest link in my arsenal.

- I have a Slackware server on bare metal w/ the storage array, hosting the Ubuntu Server VM via KVM which has an NFS share mounted to /mnt/NAS which connects to the Slackware export. This is a public NFS share, Slackware's permissions on the target dir are 775.
- Both Transmission and SABnzbd run as non privileged users, and are configured to write to the target dir as 755 which they do, and have done seamlessly and i was able to clean up any files that post-processing missed from Explorer on my Windows laptop as i was authenticated as a local user on the Slax machine.
- Today, i was unable to do so - Permission denied. Upon inspection, the user attributed to the files is "99". I thought it was a hiccup, so i chowned the mount point recursively to the local user, happy days...
- All new files being created are done so by "99", this is also true from touching a file or directory in the mount directory from the console.
- Ok, check the exports on Slax and anonuid=99, makes logical sense for it to show what it's showing.

However, prior to aforementioned updates, i was able to write these files/folders as the Ubuntu local user ('paradox' for reference sake) as well as the Slax user ('nasha' for ref.). I can say with certainty that a "user" (not 99) was the owner of the files getting written previously.
For the time being I've altered the daemons to write 777 as i'm catching up on a backlog and the traffic flow is heavy, but ideally i don't want to leave it like this.

What is the missing permission, user, group, setting or whatever else that needs to be implemented in order for Ubuntu to write to the mounted NFS share as a known user?

I'm sure it's something utterly stupid and simple, but it's not something that i've encountered before, and searches didn't highlight a solution for me.

Thanks in advance!
Nasha

---

