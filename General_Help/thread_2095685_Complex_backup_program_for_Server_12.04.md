---
title: "Complex backup program for Server 12.04?"
date: 2012-12-17
forum: General Help
---

### Post by runrun395 on 2012-12-17
I'm looking for a program that will automatically make hourly backups of certain folders into designated locations, but that's not the difficult part. It simultaneously needs to be deleting every backup except the 24th that reaches over 48 hours old (you see where I'm getting at?) AND every one of those backups except the 7th that reaches over two weeks old AND every one of THOSE backups except the 4th which reaches over two months old.

So this is the end result:
Hourlies for the past two days
Dailies for the past two weeks
Weeklies for the past two months
Monthlies (quater-weeklies) forever.

If anybody knows of a program that can perform this end result or how I can script one myself, that'd be awesome.

---

### Post by Cheesemill on 2012-12-17
[Rsnapshot]("http://www.rsnapshot.org/") will do what you need, this is exactly the type of situation it was written for.

```
sudo apt-get install rsnapshot
man rsnapshot
```

---

