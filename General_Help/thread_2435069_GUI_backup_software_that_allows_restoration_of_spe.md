---
title: "GUI backup software that allows restoration of specific user specified files"
date: 2020-01-15
forum: General Help
---

### Post by bingbong6 on 2020-01-15
I recently had to use Timeshift to restore a backup, because I accidentally deleted /bin....not going to get into that here...


I run Ubuntu 18.04 with system root and home on separate partitions. When trying to restore via timeshift ( I selected to backup system root (/) and home (/home) in it's entirety), **I did not see an option to select just 1 of the partitions to restore, or any way to restore just select files from 1 partition.** Here, I just wanted to restore /bin, but being able to just choose the entire system root only would have sufficed. 

**Is there a better backup program with a GUI that will allow this functionality?** I do not like Deja Dup that comes with ubuntu.

---

### Post by dragonfly41 on 2020-01-16
I have been copying subsets of the file system from source to destination using two tools:

grsync (setting up sessions for each workflow)
and
krusader (a dual pane file manager). This is not a common backup option probably because it comes with a lot of KDE baggage.
But I find dual pane managers to be useful and the operations are more visible.

In krusader to show other mounted partitions (e.g. another drive) you need to click on the button "Open the available media list".
Under Krusader > Settings > Toolbars tick all three options. The job progress toolbar is useful for batch runs.

In grsync make sure you study the implications of using a closing slash (or not). You get different results.
And the "dry run" feature is useful.

In your example you can selectively backup/sync /bin using either tool.

There will be other such tools around to support "selective backup/sync".

---

### Post by bingbong6 on 2020-01-16
One that I had been considering was Backintime, but I'm not sure if it still has the same capability to restore the root system in it's entirety from a snapshot, like Timeshift does. Just in case I would need it. If the two are different, maybe I'll run both. But it seems to me that Backintime would do everything I'd need.

Not too interested in KDE applications bc as you said, they come with a lot of bloat and baggage.

---

### Post by deadflowr on 2020-01-16
>  I do not like Deja Dup that comes with ubuntu.
That's unfortunate because deja-dup does exactly what you ask. Perfectly.

But backintime probably does it too.
Not sure.
But it's fairly popular.


You can check the Ubuntu help page for more alternatives here:
[https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by bingbong6 on 2020-01-16
I have had issues with Deja dup in the past, not running when it should, and it's gui is lacking. Might as well use rsync on cli at that point.

---

### Post by ra7411 on 2020-01-16
[COLOR=#000000]I use qt5-fsarchiver for o/s backup. Fsarchiver is easy to install for terminal use, but getting the qt5- gui set up can be a hassle. Also, most of the gui versions around have poor english wording. "Stored partition" button is actually to store the partition you're backing up. It backs up and restores quickly, and is a good choice to preserve your o/s before updates or any big changes you're going to try. I've used it for a number of restores and it worked. You can backup the o/s "live" - that is, while you're using the computer for work. You can install fsarchiver through Synaptic package mgr, and sometimes synaptic shows qt5-fsarchiver, but how well it actually installs the gui is mixed.[/COLOR]

[COLOR=#000000]In my opinion, Ubuntu/Conical (whatever) should get the gui and language syntax problems solved and make this a main backup program in the software center.[/COLOR]

[COLOR=#000000]I use Grsync for incremental backup of user files (/Home). You can get this out of the regular software center. This also does your backup "live" while you do other work.[/COLOR]

---

### Post by Ralph L on 2020-01-16
I have used LuckyBackup for about 10 years and like it fairly well.  It is a gui front end to rsync, but adds some features of its own.  The only bug I have found is that it won't restore permissions, when the backup is done using an older snapshot.  It will restore permissions if the restore is done from the latest backup snapshot.  It is a little complex to use, because it will let you set rsync parameters as well as LuckyBackup parameters, and I found that I needed to set rsync parameters.  It keeps a complete image of the latest backup, so to restore a one or more files (that you may have accidentally purged), you just bring up the file browser on the backup file.  It looks just like your current system.  Then, just using your normal file browser, copy the files back to your running system.  No need to look through different backups to get the latest one.

I have put all my data (including Thunderbird, Flirefox, and other app configuration data) on a separate partition with symbolic links connecting to them from the OS partition.  I backup only the data partition (not the OS partition) as I can always reinstall the OS from scratch.  I have never had to reinstall the OS (except for new releases).  Whenever, I install a new release, I do that on a separate partition, keeping the old OS until I am satisfied the new one works correctly.  With my data all on a separate partition, I can run either the newly installed OS or the old one just by restarting the computer and selecting the OS i want at boot time.

---

### Post by GhX6GZMB on 2020-01-16
@bingbong6, this is no problem with Timeshift. Go to "Settings" and "Filters". Then take it from there.

---

### Post by Tadaen_Sylvermane on 2020-01-17
[COLOR=#000000]> I have had issues with Deja dup in the past, not running when it should, and it's gui is lacking. Might as well use rsync on cli at that point.

The problem with DejaDup is that it only runs when you are logged in. As it is gui and gui login as root is not advisable it isn't exactly designed for backing up system files. But you can get around this with a crontab to force it to backup on a schedule, regardless of login.

```
deja-dup --backup
```

To be honest you would be better served with the cli than a gui for this. Greatly limited by GUI requirement. Duplicity which is the backend for Deja-Dup works great. Here is a script I use. You can probably adjust it as needed.

[/COLOR]```
    backup_workhorse() {        if [[ ! -d "$TARGETDIR" ]] ; then
            mkdir -p "$TARGETDIR"
            chown -R "$BACKUPUSER":"$BACKUPUSER" "$TARGETDIR"
        fi
        su -c "duplicity \
        --exclude-if-present .nobackup \
        --no-encryption \
        --full-if-older-than 1M \
        /home/${BACKUPUSER} file://${TARGETDIR}" "$BACKUPUSER"
        su -c \
        "duplicity remove-all-but-n-full 4 --force file://${TARGETDIR}" \
        "$BACKUPUSER"
    }
```

---

### Post by bingbong6 on 2020-01-17
Thanks! I will consider this. Agreed, I need to learn to use the cli for more things, but I'm still learning and have to prioritize. Right now, so I have SOME backups, I'm probably going to stick with a GUI because it's faster for me at this point in time. Also, and most importantly, I recently learned a lesson regarding permissions and proper security of executable scripts. The lesson I learned was that I'm not educated on it. So I need to get more familiar with basic security practices and permissions, and then maybe I'll try incorporating more custom scripts into my machine. 

I appreciate you sharing that though, I'm definitely saving it for future use/reference.

---

### Post by TheFu on 2020-01-17
> **bingbong6 said:**
> Thanks! I will consider this. Agreed, I need to learn to use the cli for more things, but I'm still learning and have to prioritize. Right now, so I have SOME backups, I'm probably going to stick with a GUI because it's faster for me at this point in time. Also, and most importantly, I recently learned a lesson regarding permissions and proper security of executable scripts. The lesson I learned was that I'm not educated on it. So I need to get more familiar with basic security practices and permissions, and then maybe I'll try incorporating more custom scripts into my machine. 

I appreciate you sharing that though, I'm definitely saving it for future use/reference.

CLI/Shell is better than a GUI for a few things.
* automation
* backups
* moving files, data, around
* renaming lots and lots of files
* system admin work, configurations.

Since backups generally should be 100% automatic, daily, overnight, the first time most people need to learn a little scripting is when they try to create backups.

As for the best tool for backups, it really comes down to the tool that works for your restore needs.  Try about 5 different tools out.  Backup /etc/ as your test area.  This specific area is good for testing backups because there are system files, owned by different users, with a few different groups and special files which can break some backup tools in that directory area.  /etc/ is also relatively tiny, so that doing the backup should be just a few seconds total.  Then restore the files somewhere else and verify they are all exactly the same. Same data, same owner, group, permissions, ACLs.  All those things must be the same.    
When you test, be certain to change the permissions (in a harmless way) of some files for at least 1 version of the backups.  Modify some files enough to change them, but not break anything - add an extra line to the bottom of /etc/hosts ... you get the idea.  Create at least 3 different versions of the backup-set of files.  How much added storage does each "version" require?   This 2nd set of tests is where many rsync solutions fail.

IMHO.

---

### Post by bingbong6 on 2020-01-17
I'll definitely give this a shot. Probably going to test it on my raspberry pi though in case I botch something again....like deleting my /bin lol (by the way, Timeshift successfully restored my root partition, and my home partition which I didn't want to do, which is what prompted this post). 

> [COLOR=#000000]This 2nd set of tests is where many rsync solutions fail.[/COLOR]

Which tests? Everything here?:

> [COLOR=#000000]When you test, be certain to change the permissions (in a harmless way) of some files for at least 1 version of the backups. Modify some files enough to change them, but not break anything - add an extra line to the bottom of /etc/hosts ... you get the idea. Create at least 3 different versions of the backup-set of files. How much added storage does each "version" require?[/COLOR]

---

### Post by Tadaen_Sylvermane on 2020-01-17
Vms are good for this sort of thing. Snapshot and just restore if you botch it.

---

### Post by bingbong6 on 2020-01-17
I ways worry with VMs that I will still somehow manage to somehow mess up my bare metal system

---

### Post by TheFu on 2020-01-17
> **bingbong6 said:**
> I ways worry with VMs that I will still somehow manage to somehow mess up my bare metal system

That is next to impossible, unlike attempting to dual boot, which is 1000x more dangerous than using a hypervisor and VMs.  VMs running inside the virtual hardware setup for them. They cannot* break out of that and touch the hostOS unless you go out of your way to allow it. 

* **cannot** is a strong term.  There have been attacks against hypervisors which use flaws to break out of the VM. These are deliberate attacks, not accidental. I've read about them, never saw any in the wild. Patches usually fix the issue before it is announced, at least for the hypervisor I use, qemu-kvm.

---

### Post by speartip on 2020-01-18
Timeshift or fsarchiver for your root partition. Backintime or Areca for your home partition.

---

### Post by cmcanulty on 2020-01-20
I have been using grsync for years and never an issue. It is really fast. I backup around 300GB in a few minutes (after first run of course). You can save permissions and many other options. I backup home and another backup of / excluding some folders like opt, mnt, etc

---

### Post by sgage on 2020-01-20
Another vote for grsync. By setting up different backup profiles, and with careful use of exclusion files, you can control things to a fare-thee-well. E.g., I have a grsync profile for my config, separate from my data. This is very useful if you enjoy, as I do, exploring different distros. 

As someone mentioned above, do note the difference between somedirectory and somedirectory/ in specifying your backups. A small amount of experimentation will make it clear.

---

