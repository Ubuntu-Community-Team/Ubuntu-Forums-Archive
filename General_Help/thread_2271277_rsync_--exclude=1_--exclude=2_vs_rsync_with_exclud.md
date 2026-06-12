---
title: "rsync --exclude=1 --exclude=2 vs rsync with exclude list. Seeing different results..."
date: 2015-03-28
forum: General Help
---

### Post by Roasted on 2015-03-28
Hello friends. I utilize an rsync script as part of my backups with my systems. It's a simple bash script that is tagged as a startup application. That way each time a system boots up + logs in (which is frequent for me since I power off my systems when I am done with them), a backup kicks in. I started messing with some exclude lists but I'm not getting the results I expected. I'd like to explain what the script does first. Upon login, I have sleep 1m set, which means the script will wait 1 minute before going to the next step. The only reason I do this is for the laptops to give them plenty of time to connect to wifi if they do not connect immediately on startup. Assuming I ever have to wait for a wifi hook, it's a matter of 3 seconds, but I figured a minute was an "accepted overkill" level of padding so I ran with it. Next, it sends a Unity-looking notification to tell me the backup started. Then it rsyncs the data, then writes a date stamp to a log file (txt file) on my server. This way I can track which systems backed up. I use set -e at the beginning because it's my understanding that if I use set -e and the script fails, it will *not* complete the rest of the steps. (in other words, if the rsync fails, it won't write a date stamp in the log file). Then it sends a backup complete notification and... that's it. Here's the first script.

```
#!/bin/bash
set -e
sleep 1m
notify-send "Backup Started"
rsync -a --delete --exclude-from 'exclude-list.txt' /home/jason/ jason@192.168.1.20:/media/2f730da3-263d-473f-af11-cc955e3158ef/backups/jason/desktop_ubuntu
ssh jason@192.168.1.20 'date >> /media/2f730da3-263d-473f-af11-cc955e3158ef/backups/backup_logs/jason_desktop_ubuntu.txt'
notify-send "Backup Complete"
exit
```

Let's break it down in steps. Notify-send is step 1, rsync is step 2, the 'date >>' section is step 3, and notify-send for backup complete is step 4. In the above script, only step 1 takes place. I do NOT get new files on the source rsynced, a date stamp in the log nor do I get a notification that the backup is done. So it says a backup started, but a backup never takes place, nor anything beyond that. Let's take a look at the next script.


```
#!/bin/bash
set -e
sleep 1m
notify-send "Backup Started"
rsync -a --delete --exclude='.gvfs' --exclude='.gnupg' --exclude='Desktop' --exclude='Misc' --exclude='Music' --exclude='Music Videos' --exclude='ownCloud' --exclude='Software' --exclude='System Images' --exclude='Videos' --exclude='VirtualBox VMs' /home/jason/ jason@192.168.1.20:/media/2f730da3-263d-473f-af11-cc955e3158ef/backups/jason/desktop_ubuntu
ssh jason@192.168.1.20 'date >> /media/2f730da3-263d-473f-af11-cc955e3158ef/backups/backup_logs/jason_desktop_ubuntu.txt'
notify-send "Backup Complete"
exit

```

As you can see, I have a bunch of individual excludes in the rsync command. These excludes are the same things notated in the exclude-list.txt file in the first script. The difference is, this second script completes ALL four steps. I cannot make sense as to why that is. Is there something I missed?

---

### Post by papibe on 2015-03-28
Hi Roasted.

Could you post the content of 'exclude-list.txt' ?

A few thoughts:

[LIST]
[*]Although it should work as it is right now, the proper syntax should be ```
--exclude-from**[COLOR="#FF0000"]=[/COLOR]**'exclude-list.txt'
```
[*]When executed on a non interactive bash scrtipt, I would include the absolute path to the exclude file:```
 --exclude-from='/path/to/exclude-list.txt'
```
[*]Both --exclude and --include are simplified versions of the --filter rules, so --exclude assumes a '-' preceding the pattern, and --include a '+'. So you just may be missing a default include rule at the end: --include '*' (it would means include anything else).


[*]The option --exclude-from it is a little different. You need to explicitly use the pluses and minuses. Something like:
```
- .gvfs/
- .gnupg/
- Desktop/
- Misc/
- Music/
- Music Videos/
- ownCloud/
- Software/
- System Images/
- Videos/
- VirtualBox VMs/
+ *

```
(I assumed most of them are directories so I added the trailing '/').
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

