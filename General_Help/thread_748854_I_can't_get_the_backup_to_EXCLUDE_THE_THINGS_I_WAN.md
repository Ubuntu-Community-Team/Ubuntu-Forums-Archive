---
title: "I can't get the backup to EXCLUDE THE THINGS I WANT"
date: 2008-04-07
forum: General Help
---

### Post by adn258 on 2008-04-07
When I use the below backup command in my terminal i see it DELAY on backup.tgz as if it IS BACKING THAT UP TOO.  Why?  Any ideas even though it is supposed to be excluded.  


tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

---

### Post by dcstar on 2008-04-08
> **adn258 said:**
> When I use the below backup command in my terminal i see it DELAY on backup.tgz as if it IS BACKING THAT UP TOO.  Why?  Any ideas even though it is supposed to be excluded.  


tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

GNU tar has an "**--exclude-from=**FILE"  (or "-X") option which uses a single file containing the list of exclusions, so your command will never work.

Refer to the man page.

---

