---
title: "rsync over ssh hangs with vmdk file"
date: 2015-11-30
forum: General Help
---

### Post by gobo7 on 2015-11-30
i've got a new install of kubuntu 14.04 on a workstation.  it does rsync's to
two nas servers.  the command for one of the nas servers is:

/usr/bin/rsync -avPz --delete-after -e ssh /home/user/ nas4:/home/user-copy2

the problem is when writing out to nas4, rsync hangs on a vmware vmdk file.
it always hangs on the second of several <2gb files at around the 50 ~ 65% 
point.  there is no error, ssh shows the connection is still up and both rsync 
processes are still running.  no activity.

the ugly details.
- the 14.04 box is replacing an opensuse 12.3 box.  the directories from the 
opensuse box were copied to the 14.04 box.  the opensuse box had no issues with
rsync.
- nas4 uses rsync over ssh as it has no exported filesystems.  the other nas 
has an nfs share mounted on the 14.04 box (ssh not needed.)
- rsync of the same file set in question to the other nas completes without issue.

i'm at a complete loss to find any details of why rsync hangs.  is there possibly
a difference with ssh that needs to be adjusted?  compatibility issues with rsync?

any suggestions appreciated.

edit-- new detail.
the rsync process runs in pairs on each end.  when the host process hangs, the 
two rsync processes on the nas close.  no messages. 
sshd writes a disconnect message on the nas when i ctl-c on the host.

---

### Post by BCW142 on 2015-12-24
I'm getting a like problem with Ubuntu 14.04.3 LTS after updates this week (12/22/2015). I've been using a script to copy videos to the main server (and mythtv setup). Both sides have the same versions of everything and are AMD 64 bit systems. It's now hanging like yours on some files, random as far as I see, any format any type. I'll have to check the server, likely working the same as yours and dropping rsync. Now the thing is what do we do to figure out why it hangs? The one the sending end it just hangs, I'll check the receiving server and setup vncviewer for it so I can check it when it happens. Both of mine also have samba and upnp setup on them. I have noticed when It hangs and I kill the tasks, I can scp the file and that works fine. Of course it may have nothing to do with updates, it could be other causes like ntfs-3g running on the sending end disk and ext4 running on the receiving side. Hang just now (NOVA is the script input; script, then rsync's output till hang):
#!/bin/bash
# 25t - To bbc's /5T/Videos/name*.mp4
rsync -aPrvz "$1"*.mp4 bcw@bbc:/5T/Videos/"$1"

NOVA - Manhunt Boston Bombers.mp4
2,811,184,015 100% 19.28MB/s 0:02:19 (xfr#6, to-chk=28/61)
NOVA - Meteor Strike (SD).mp4
2,260,992 0% 5.74kB/s 31:51:10
(Hung and just sits there. Kill it and restart, same thing happens on the same file; it's trying to copy from /3T/Videos/NOVA to remote /5T/Videos/NOVA directory.)

---

### Post by BCW142 on 2015-12-24
Was editing the last entry and it made a new entry instead. So I Deleted the old one put the new one in place and then dropped it from here.
Kicked off copy using scp:
bcw@leno:/3T/Videos/NOVA$ scp "NOVA - Meteor Strike (SD).mp4" bcw@bbc:/5T/Videos/NOVA
bcw@bbc's password: 
NOVA - Meteor Strike (SD).mp4                 100%  630MB  10.2MB/s   01:02 #Finished fine.
I didn't fix the hang on either end, just Ctrl-C'd out on the sending end and kicked off the scp.
Kicked off script again and:
bcw@leno:/3T/Videos/NOVA$ 25t NOVA
bcw@bbc's password: 
sending incremental file list
rsync: chgrp "/5T/Videos/NOVA/NOVA - Invisible Universe Revealed.mp4" failed: Operation not permitted (1)
So it made it through "NOVA - Meteor Strike (SD).mp4" then hung due to former hang, I need to kill the tasks.
The point here is that it made it through the original file now and hung on another. I'm guessing buffering problems (like buffer/cache not big enough).

---

