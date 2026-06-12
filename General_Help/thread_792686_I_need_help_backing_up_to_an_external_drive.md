---
title: "I need help backing up to an external drive"
date: 2008-05-13
forum: General Help
---

### Post by AhronZombi on 2008-05-13
Hello after spending weeks trying different things and searching all over i need to ask you all for help. i want a rsync or diff backup solution that will allow me to automatically backup to a 80 GB usb drive, and automatically delete old backups when its full. ive tried timevault, it failed to realize my drive was external and started writeing to /media/disk before mounting my disk and my disk ended up being mounted to disk1 and so on. So time vault was a fail. next i tried flyback, witch worked great until my usb drive was full, after the drive was full it failed to try and delete old backups even though i specified in the settings to do so once drive space got below 1 GB. please give me advice on howto get either of these to work or another solution you may know of. thanks allot guys

:confused:

---

### Post by rune0077 on 2008-05-13
I'm using Simple Backup myself. It doesn't automatically delete files once the drive is full (I think, though my backup-drive has never actually been full), but it does let you tell it to automatically delete backups that are X days old.

Not sure if it's what you're looking for, but give it a try, it's in the repos.

---

### Post by mankygitt on 2008-05-13
I also use simple backup/restore installed via Synaptic.
I'm using it on my media server to backup to a second drive installed,
and on my Laptop to backup to an ftp server.

Both work very well.
I dont know how to get it to purge older backups automatically, but every 28 days (configurable) it performs a full back up. So I manually purge everything prior to the last full backup. 

It's very easy and effective.

I've needed to restore from it several times where i did "silly things".. and happily now rely on it as a very solid backup mechanism.

---

### Post by rune0077 on 2008-05-13
> **mankygitt said:**
> I also use simple backup/restore installed via Synaptic.
I'm using it on my media server to backup to a second drive installed,
and on my Laptop to backup to an ftp server.

Both work very well.
I dont know how to get it to purge older backups automatically, but every 28 days (configurable) it performs a full back up. So I manually purge everything prior to the last full backup. 

It's very easy and effective.

I've needed to restore from it several times where i did "silly things".. and happily now rely on it as a very solid backup mechanism.

You can just run the simple backup config (in System > Administration), and there's a tab called purging (the last one, I think) - here you can set a specified number of days, and anything older than that will be automatically deleted.

---

### Post by housam on 2008-05-13
Read this [[COLOR="Red"]_guide_[/COLOR]]("https://help.ubuntu.com/community/Backupsolutionsforlinux") it 'll help you

---

### Post by AhronZombi on 2008-05-13
> **rune0077 said:**
> I'm using Simple Backup myself. It doesn't automatically delete files once the drive is full (I think, though my backup-drive has never actually been full), but it does let you tell it to automatically delete backups that are X days old.

Not sure if it's what you're looking for, but give it a try, it's in the repos.

no thanks i tried it in the past. i dont think it does rysnc or diff. plus its a little too simple for what im trying to do. im working with time vault again since the project still seems active

---

### Post by rune0077 on 2008-05-13
> **AhronZombi said:**
> no thanks i tried it in the past. i dont think it does rysnc or diff. plus its a little too simple for what im trying to do. im working with time vault again since the project still seems active

Well that's probably why it's called Simple Backup :) It's still the only backup software for Linux I have found to be at all useful, and it managed to restore my system very smoothly the one time I needed it.

---

### Post by HermanAB on 2008-05-13
Here you go:
[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

Also see this wizard for it called Keep:
[http://www.kde-apps.org/content/show.php?content=32984](http://www.kde-apps.org/content/show.php?content=32984)

---

### Post by AhronZombi on 2008-05-14
> **HermanAB said:**
> Here you go:
[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

Also see this wizard for it called Keep:
[http://www.kde-apps.org/content/show.php?content=32984](http://www.kde-apps.org/content/show.php?content=32984)


thank you for the recomendation, will try

---

