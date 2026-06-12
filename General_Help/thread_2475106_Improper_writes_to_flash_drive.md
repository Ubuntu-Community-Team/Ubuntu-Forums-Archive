---
title: "Improper writes to flash drive"
date: 2022-05-16
forum: General Help
---

### Post by allen2 on 2022-05-16
Edit: Despite running chkdsk and rebuilding the mbr, something wasn't right with the flash drive.  Deleting all partitions and formatting to XFAT seemed to solve the issue.

Yesterday, I ran apt update on Ubuntu 21.10 (not sure if related).  

When I try to write files to a flash drive, it's only writing partial files.  I tried both ext4 and ntfs and it is experiencing the same issue in both.  As far as I'm aware, there is nothing wrong with the flash drive.  It completes as done / stops blocking on cp -r command.  The files are about 60 to 150 mb. Ubuntu might write some completely, others it will only write either 4 MB or 8 MB and it leaves a lot as 0 byte files.  I do safely remove through Dolphin.  I don't think it's the flash drive itself.

I suspect it is either an issue with write cache or the latest update.  Previously, I had tried to enable write caching through windows for better performance, but I undid the changes that I made.  

I'm not sure where to check or even the search terms I should use to research further.  I tried searching various things, but none of the search engine results are related.

---

