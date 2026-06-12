---
title: "What is the best free backup for Ubuntu?"
date: 2024-08-21
forum: General Help
---

### Post by Tom_Carr on 2024-08-21
What is the best free backup for Ubuntu?  I have been using drop box, but I am about to have to pay for it to get more space.  What are some other options?  I have only been using dropbox for one desktop that I do all my work on.

---

### Post by TheFu on 2024-08-22
I know of no free/paid internet storage options that I'd trust with backups at all.
We are linux people, so we can setup our own solutions.

Backups need to follow the 3-2-1 method.
[LIST]
[*]3 copies (1 on normal storage, 2 backup copies (1 local, 1 remote) )
[*]2 physical media types
[*]1 copy should be remote - outside the region so huge natural disasters don't impact your data.
[/LIST]

That's the minimal.  Taking it to the next level adds some other requirements, like efficiency of storage and networking, versioning, encryption, tested, and with the ability to have all the data shipped overnight to you in 1 day on a new HDD after a failure.

So, it sounds like you are seeking some remote storage to place your encrypted, versioned, backup data onto.  Amazon S3 is common.  There are others, but they all have paid plans.  As for the software to use, it depends on your skill and how access to the remote storage is provided.  Duplicity is the standard that handles everything that backups should provide, but it is also prone to corruption if the backups aren't managed using their best practices.  For example, duplicity (dejadup, duplicati, et al) all require a fresh "Full Backup" every month, so it isn't really all that efficient with storage or networking, though it does address the other things good backups need.

I hate linking to redit stujff ... but the SelfHosted subredit says this: [https://www.reddit.com/r/selfhosted/comments/113gxz3/cheapest_cloud_backup_solution_for_linux_ubuntu/](https://www.reddit.com/r/selfhosted/comments/113gxz3/cheapest_cloud_backup_solution_for_linux_ubuntu/)

---

### Post by werewulf75 on 2024-08-26
Dropbox, Mega, or any Big Tech cloud storage cannot be trusted with your data. If 500Gig are enough, have a look at  [https://proton.me/drive](https://proton.me/drive) - it's securely end-to-end encrypted and zero-access encrypted, i.e., no-one can access your data, not even Proton. Unbeatable for privacy and security, Swiss-based.

---

