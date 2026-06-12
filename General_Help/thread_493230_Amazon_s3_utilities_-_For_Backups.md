---
title: "Amazon s3 utilities - For Backups"
date: 2007-07-05
forum: General Help
---

### Post by DugieHowsa on 2007-07-05
Does any one know of any good Amazon S3 utilities/packages that integrate nicely in Ubuntu?  I used to use S3 Backup ( [http://www.maluke.com/s3man/](http://www.maluke.com/s3man/)), but currently these is only a windows port.  I have tried using s3sync ( [http://s3sync.net/](http://s3sync.net/) ), but I am having problems with the ruby and openssl implementations.  I also tried using JetS3t Cockpit ( [http://jets3t.s3.amazonaws.com/index.html](http://jets3t.s3.amazonaws.com/index.html) ), but I am having java run-time issues.  Jungledisk ( [http://www.jungledisk.com/](http://www.jungledisk.com/) ) is the closest thing I have found, but I was wondering if anyone else is using something that they would recommend.

---

### Post by nzflew on 2007-08-07
Did you find a solution in the end?

---

### Post by DugieHowsa on 2007-08-13
I resolved the issues I was having with the JetS3t toolkit. I am using the synchronize utility to back  up and the cockpit utility to confirm the uploads.  I also found this Firefox plugin that works:

[http://www.rjonna.com/ext/s3fox.php](http://www.rjonna.com/ext/s3fox.php)

I found that JetS3t Cockpit and the Firefox S3 Organizer work best with small amounts of files.  I found that etS3t Synchronize works best with large amounts of files.

I also just finished a write up on using the JetS3t suite:

[http://ubuntuforums.org/showthread.php?t=524811](http://ubuntuforums.org/showthread.php?t=524811)

---

