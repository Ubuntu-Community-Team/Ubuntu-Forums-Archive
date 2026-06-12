---
title: "mirror folder on another computer"
date: 2007-10-14
forum: General Help
---

### Post by DiGiTY on 2007-10-14
I would like to have my iTunes Music folder on my Windows computer mirrored and synced to my Ubuntu home server. How do I accomplish this?

TIA

---

### Post by tarpon_bill on 2007-10-14
The program you want to use is called rsync. I suggest you read the man pages and if it's still not clear visit the rsync site. It will do the job, I use it, but it can be complicated and takes some thought to produce exactly what you may want. Just set up a dummy directory, throw in some files and practice transfers with those files --- delete when done and set up the real thing. It's easy really.

You may need to trigger a 'crontab' event to fire it off.

---

### Post by DiGiTY on 2007-10-15
okay, so run a rsync server on the winbox and rsync client on the linux box?

I got SMB/Windows sharing already set up on both boxes, how could I sync 'em up using cp or something?

---

