---
title: "How to prevent accidental delete of files?"
date: 2024-08-18
forum: General Help
---

### Post by u4634456 on 2024-08-18
Hi!

Is chattr +i command the only way to prevent deleting files? I want to make file server for backups so I want to be able to create files but not delete them. My first thought was to write python script that would run as root and use file watchers to get information about new files and then run chattr +i command for every new file. But the problem with that idea is that if it runs chattr +i while file is still uploading it prevents file upload from being finished. Is there any better ways to get this done?

---

### Post by TheFu on 2024-08-18
Unix/Linux file permissions can prevent file deletion. Learn them.

There are also ACLs.  That's the **setfacl** and **getfacl** commands, but those are seldom used. Judicious use if standard Unix permissions has served my needs all but twice in 30 yrs.

And there's always backups, so if an important file is deleted, you can restore it easily.  Backups solve 1001 issues, so why not use them?

If you more clearly explain the full need you have, perhaps someone could provide the "standard solution" for that instead?  

For example, if you need to allow file uploads from random people over the internet, use an HTTP server for that and have a separate upload directory that only has wx permissions for the userid running the web server. No read.  Then, periodically, move the files from that upload directory, process the file(s) to ensure they don't contain unwanted items like malware or steganography and place them into another directory either for the rest of your processing or for sharing with the world.  In general, it is a bad idea to allow uploaded files to be read or accessible by anyone without checking.  In the processing, you can ensure unique filenames.

Of course, you probably have a different thing planned.

---

### Post by u4634456 on 2024-08-19
> If you more clearly explain the full need you have, perhaps  someone could provide the "standard solution" for that instead?   

I want to create local fileserver/NAS to use at home intranet so that I  could backup files from my computer there. So nothing is exposed to  public internet. I planned both ftp and smb. And I wanted to secure it  against scenario where one of my computers get compromised by virus that  tries to delete or overwrite files in my server (ip/username/password  falls in the hands of virus). To combat that I want to create  environment where it is possible. Its possible to create new files but  not possible to overwrite or or delete files. 

Sofar I have come up with non-standard solution:
```
import os
import sys
from inotify_simple import INotify, flags

# Directory to monitor
WATCH_DIR = '/path/to/dir'

# Create an instance of INotify
inotify = INotify()

# Add a watch on the directory for IN_CLOSE_WRITE events
watch_flags = flags.CLOSE_WRITE
wd = inotify.add_watch(WATCH_DIR, watch_flags)

print(f"Watching for file changes in {WATCH_DIR}")

try:
    while True:
        # Read events from inotify
        for event in inotify.read():
            # Check if the event is for a file and the event type is IN_CLOSE_WRITE
            if event.mask & flags.CLOSE_WRITE:
                # Construct the full path of the file
                file_path = os.path.join(WATCH_DIR, event.name)
                # Apply the immutable attribute
                os.system(f'chattr +i "{file_path}"')
                print(f"Applied chattr +i to {file_path}")
except KeyboardInterrupt:
    print("Stopped by user")
finally:
    inotify.rm_watch(wd)


```


I read about setfacl  but it doesn't seem to give better control than chattr unless I  missed something.

---

### Post by TheFu on 2024-08-19
Ok. The  "standard solution" for this is to have a backup server (perhaps the NAS can do this) which "pulls" backups over the network.  Anytime you "push" backups, that means the client system has to be allowed to write to the NAS.  That is unacceptable, since any client can become compromised.

With the "pull" backups, you will still get malware in the backups, but hopefully, you'll see the huge changes to the backup size and do some research on what may have caused it.  The -1 version will still have the good backups from the day prior.  Versioned backups solve lots of other issues too.  Once had a system that was used once a month for some accounting stuff.  Nobody noticed that the DB had become corrupted for over a month. When I learned about it, it had been 37 days since the initial corruption happened.  I did some trial and error restores, going a week at a time until one of the restored DBs worked. Then I tried each of the DBs for that week until I found the first one that worked.  We didn't lose anything and the team was a little late for their monthly report, but that wasn't a big deal.

Daily, versioned, "pulled", backups are what you need.

BTW, never use SMB or FTP for backups.  At least use secure protocols, which SMB and plain FTP are definitely not.

---

### Post by currentshaft on 2024-08-19
Thank you

---

### Post by werewulf75 on 2024-08-20
> **currentshaft said:**
> It is not feasible to create an environment where it is guaranteed to not be possible for malicious software to mutate files.

Not any different than trying to build a house which is immune to all damage and trespass attempts. That's why we use backups and insurance as a compensating control instead.
Indeed, backups, backups, and more backups. I even keep backups of my backups, i.e., copies. On another drive of course, encrypted of course.

Another problem can be that we accidentally delete a file of a bunch of files ourselves. Has certainly happened to me, more than once. Even deleted a then current backup once - luckily had the dupe. :cool:

---

