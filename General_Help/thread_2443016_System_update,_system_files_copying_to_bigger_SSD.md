---
title: "System update, system files copying to bigger SSD ?"
date: 2020-05-10
forum: General Help
---

### Post by michalbo on 2020-05-10
Hi,
I got Ubuntu 18.4 server which I would like to latest 20 version with putting it on 512SB SSD (it is on 128GB now).
As it seems easy, the thing is bit complicated because the server consist of few RAID1,5 drives.
But I only care about my boot drive which is RAID1 with other one. But it has some things like /var kept on different RAID.
To cut the story short, I'm thinking that the easiest meted would be:

1. Make the backup of the existing system
2. Remove existing boot drives.
3. Insert new 512GB SSD and setup clean Ubuntu 18.4
4. Restore the files from the backup
5. Update to 20.
6. create the RAID1 if all works ok

I suppose I need to exclude some stuff while making the backup (RAID conf. files or cramfs info for the starter)
At the same time I would like to keep my network, firewall, mail, openvpn and so on running as they are now :)

I read a bit about rsync and I believe it is way to go. Can anyone with bigger Linux experience suggest please what to exclude to make it the painless process please. Maybe a better approach?
Oh I made the image of the one of the existing disks so there is a way to put it on the new SSD but I'm not sure how to deal with the RAID elimination in that case.
PS, I preferer to work on the new SSD rather than existing ones to not to damage anything as all works fine for now.
Thanks

---

