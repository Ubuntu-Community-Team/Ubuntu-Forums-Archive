---
title: "Deja-Dup Backup - Restore-Test fails: Invalid Argument"
date: 2013-10-10
forum: General Help
---

### Post by gu4rdi4n on 2013-10-10
Hello,

I am using the ubuntu internal backup system (Deja Dup) to backup all my work to an SMB share in the local network. The backup runs every week, takes about 15-20 minutes and seems to run fine. I started backing up my data when i set up this box about a year ago, the backups now are about 20GB in total, but there are still terabytes free. It is fully encrypted because it is a shared fileserver and there are also some files that should not go public.

Now to the problematic part: Once in a while, the backup program asks me for the password to test if the backups can still be recovered. I have the password (more than 30 chars) in my keepass storage. But whenever i try to run the test, it immediately stops and gives me the error-message "invalid argument" and nothing more. I dont know if i can restore my data or not. Are there any protocol files i can analyse?

Another problem is that i dont know if there is any way to trigger that test, currently i just have to wait a few weeks to get it again. So i cannot analyse what is happening.

I am running Ubuntu 12.10 i386, Deja-Dup 24.0.

---

### Post by asalapi on 2014-02-06
The same happens to me (you might wish to file a bug and link here) under Ubuntu 13.10. It's also with an SMB share, which might be "important" for troubleshooting.
Anyway, the backup and password seem to be all right because if you initiate deja-dup (backup) and ask for a restore (restoring NOT to the original location, of course, to avoid messing things up) the restore is carried out correctly... well, ehem, unexpectedly, without asking for the password (in my case, it is stored for the periodic backups and, it seems, for restoring, too).

---

