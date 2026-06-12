---
title: "user &quot;backup&quot;"
date: 2007-08-01
forum: General Help
---

### Post by andrgoo on 2007-08-01
Hi All,

I'm setting up a machine in my home network as a file/backup server using LTS 6.06 server. I was going to create a new user called "backup" to own and administer  the backup folders and rsync, but apparently there is already a user "backup". What is the purpose of this user, and is it approriate to login as this user to administer backups? 

Thanks and regards,
mike

---

### Post by kidders on 2007-08-02
Hi there,

> **andrgoo said:**
> is it approriate to login as this user to administer backups?No. Imo such accounts should neither have passwords nor shells, making it impossible to log into them.

Predefined accounts like "backup" are primarily intended as a means of access control, for security purposes. Many common processes & applications (eg web servers) run using dedicated accounts, so that the potential impact of a glitch, configuration error or security violation is vastly reduced. They are not intended to be used by real people.

There's no reason not to create an account for precisely the purpose you described though ... just call it something else.

---

