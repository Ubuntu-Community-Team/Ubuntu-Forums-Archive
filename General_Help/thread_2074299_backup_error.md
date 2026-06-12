---
title: "backup error"
date: 2012-10-21
forum: General Help
---

### Post by unibroker on 2012-10-21
I backup a financial program every time I exit.  I had no error message whenever my target was an ntfs partition.  I recently changed it to an ext4 partition.  Now when I try to backup it gives me an error both when I check the box to "mount" the location or when I leave the box unchecked.

Side note:  I know most of my questions posted to this forum had to have been asked before but I am having no luck in searching.  I use the advanced search and still the results are unusable.  Any suggestions in this regard would be appreciated.

Update:  Solved it myself with ```
sudo chown -R username:username /partition/mount-point
```

---

