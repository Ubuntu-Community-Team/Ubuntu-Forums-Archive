---
title: "BackInTime doesn't restore the correct file owner and group"
date: 2015-09-09
forum: General Help
---

### Post by Sacha_Kozma on 2015-09-09
Hi everybody ! ;)

Here is the situation : I made a full backup of my ubuntu system (folder /, with BackInTime (version 1.0.34) with root privileges), and then I tried to restore it so I booted from a Ubuntu Live CD,formatted my partition, installed BackInTime (version 1.1.6), and used the fonction "Restore / to" to restore to my freshly formatted partition. Everything worked without any error, but when i boot in my ubuntu i couldn't login (boot loop, and so on). After some research I found that BackInTime didn't restore the files owner and group correctly : everything is owned by root:root. 

So i checked in the file where BackInTime save the permissions and saw that it seems correct (for exemple here for the .Xauthority file, which need to be owned by the user) :

[IMG]http://i.imgur.com/RozttzQl.png?1[/IMG]

But when I checked the restore logs, I found that BackInTime only used the chown command on the files owned by root, and not on the files owned by me (sacha), resulting in a situation where all the files are owned by root:root. For example for the same file (.xAuthority) :

[IMG]http://i.imgur.com/VXCosg2l.png?1[/IMG]

We can see that the files that I should own is only "chomped", unlike the root file which are "chmoded" and "chowned"

Why is this situation happening ? I looked on different threads and forums but I can't find any solution.. In the changelog of BackInTime, they fix a bug like mine :

[LIST]
[*]Fix bug: failed to restore file owner and group
[/LIST]

But this was in the version 1.1.4, and I used the version 1.1.6 to restore the backup (but I used the version 1.0.34 to do the backup, maybe this is the problem but it seems strange..). Maybe because I restore with the root privileges ? But if I restore as a standard user I don't have enough privileges to restore all the files...

Thank you for your help !

---

### Post by TheFu on 2015-09-09
When you did the restore - did you use root? Ah - yes you did.

You should open a bug with the BackInTime team. Canonical won't do anything about it. The back-in-time folks will want you to use the latest version and test again.

Back-in-time doesn't actually store the user/permissions separately from the files, does it? The NAS storage needs to support the file permissions and hardlinking for it to work at all. Is your NAS doing NFS support?

Also, since different versions of files may not change but the permissions did, only the last permissions for the last backup will be stored.

I found that back-in-time was useful for end-user backups only. Stopped using it in 2012 for these reasons. For system backups, a different tool is needed - duplicity or rdiff-backup is where we looked. Been relatively happy with rdiff-backup the last 8-ish years.  No GUI, sorry.

One of the cool things about back-in-time is that you can use rsync to restore everything.  Did you try that, avoidig the GUI completely?  Be certain to run as root for the rsync restore.

---

### Post by Sacha_Kozma on 2015-09-10
> You should open a bug with the BackInTime team. Canonical won't do anything about it. The back-in-time folks will want you to use the latest version and test again.

Ok, I opened one and one of the developper answered me he will looked at this bug tomorrow !
> Back-in-time doesn't actually store the user/permissions separately from the files, does it? The NAS storage needs to support the file permissions and hardlinking for it to work at all.

Yes BackInTime does this, actually it is the file we see in the first screenshot.
> Also, since different versions of files may not change but the permissions did, only the last permissions for the last backup will be stored.

You're right but the permissions for these files never changed (in the example it is my home folder, and we can see that backintime has stored these permissions correctly, the problem is that he cannot restore them :/)
> I found that back-in-time was useful for end-user backups only. Stopped using it in 2012 for these reasons. For system backups, a different tool is needed - duplicity or rdiff-backup is where we looked. Been relatively happy with rdiff-backup the last 8-ish years.  No GUI, sorry.

I will check these tools ! Thank you very much for these propositions !
> One of the cool things about back-in-time is that you can use rsync to restore everything.  Did you try that, avoidig the GUI completely?  Be certain to run as root for the rsync restore.
No i didn't try it because i don't know the exact command that is needed.. Plus the fact that backintime store the permissions in a separate file and I don't know how to use this file to apply the permissions on the newly restored file..

Thank you very much for your answer, I will wait the answer of the backintime developper and update this thread if necessary ! ;)

---

### Post by TheFu on 2015-09-10
If backintime stores owner/group/permissions in separate files now, they've completely overhauled the system from the last time I used it. In the old days, 2 yrs ago, that wasn't the case and rsync (run as root to maintain permissions) could easily be used to restore files.

From the docs:
> Keep in mind that Back In Time is just a GUI. The real magic is done by rsync (take snapshots and restore), diff (check if somethind changed) and cp (make hardlinks).
and
> Starting from version 0.9.24 permissions and user/group are stored in a special file. This way you can even save/restore files from a NTFS/FAT drive without losing this informations (NOTE: FAT don&#8217;t support hard-links).

Guess I was running pre-0.9.24.
If you know the format of the permissions file, you can do the restore with rsync, then apply the permissions manually.
OTOH, this seems like a bunch of effort that any good backup tool should just handle.

BTW, unrelated, using /mnt for anything other than temporary mounts isn't following standards. 
[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure) There is an official standard, but the wikipedia is easier to read.

---

### Post by Sacha_Kozma on 2015-09-10
> Guess I was running pre-0.9.24.


Yes that's a new feature and this is why I think that this is a bug in his tools. (the permissions are correctly stored but not correctly restored)
I think that I'll wait for the developper to fix the tool !

> you can do the restore with rsync, then apply the permissions manually.


All my files are now correctly restored, I just have to apply the permissions.. Do you know how I could do this ? The file where the permissions are stored is well structured but I don't I there is a command to take a column of the file as an argument... I have a basic shell scripting knowledge..


> BTW, unrelated, using /mnt for anything other than temporary mounts isn't following standards. 
 The screenshots are taken from the Live CD, where I mounted my partition (/dev/sdb4) and my NFS+ storage (the backup location, a Synology) in the /mtn folder, but on my Ubuntu I used to only mount my backup location (the Sinology) in the /mtn folder using /etc/fstab.. Is this bad ?

Thank you for your help, it's very appreciated !

---

### Post by TheFu on 2015-09-10
> **Sacha_Kozma said:**
> Yes that's a new feature and this is why I think that this is a bug in his tools. (the permissions are correctly stored but not correctly restored)
I think that I'll wait for the developper to fix the tool !
Don't hold your breath. I suspect it was fixed already and using the newest version for BACKUPS will handle it.  However, since you are trying to restore from a backup, that probably will not work.  Using the same version for the backup AND the restore is very important, unless the tool specifically says different versions can work.

It is also common for 2nd level version changes to break file compatibility.
a.b.c --- if "a" changes, don't expect anything to be compatible. If may be, just don't expect it.
--- if "b" changes, file formats may have changed.
--- if "c" changes, expect the newer versions to work with files created by older versions.
This is general and I didn't look up what B-i-T does. Every project team can have a different versioning strategy.

> **Sacha_Kozma said:**
> All my files are now correctly restored, I just have to apply the permissions.. Do you know how I could do this ? The file where the permissions are stored is well structured but I don't I there is a command to take a column of the file as an argument... I have a basic shell scripting knowledge..
Couldn't say without seeing the file. Can you post a small except that shows the important parts? Oh - NO SCREEN SHOTS!!! That isn't nice to low bandwidth readers.

> **Sacha_Kozma said:**
>  The screenshots are taken from the Live CD, where I mounted my partition (/dev/sdb4) and my NFS+ storage (the backup location, a Synology) in the /mtn folder, but on my Ubuntu I used to only mount my backup location (the Sinology) in the /mtn folder using /etc/fstab.. Is this bad?

Bad? I don't know.  Definitely against standards. Using /media is also against standards, but nobody seems to care.  If we ignore history, we are doomed to repeat it.  These standards exist for good reasons that are not always clear to newer admins.

> **Sacha_Kozma said:**
> Thank you for your help, it's very appreciated !

It is fun to help others and share my experience.

Anyway - I've shared MORE than I know-for-certain now. Thanks for the education.

---

### Post by Sacha_Kozma on 2015-09-10
> This is general and I didn't look up what B-i-T does. Every project team can have a different versioning strategy.

Mmh ok, it's worth knowing these tips ! I'll wait the answer of the BiT team to see if they fix my issue, if interested you can follow the development here : [https://answers.launchpad.net/backintime/+question/271252](https://answers.launchpad.net/backintime/+question/271252)
> Couldn't say without seeing the file. Can you post a small except that shows the important parts? Oh - NO SCREEN SHOTS!!! That isn't nice to low bandwidth readers.

Haha sorry, I had to switch from the Live CD to my Mac and it was faster to take screenshots of the importants configs. Here is it :

[I]```
[FONT=Monaco]33204 sacha sacha /home/sacha/pulseaudio/src/tests/thread-mainloop-test.c[/FONT]
[FONT=Monaco]33204 sacha sacha /home/sacha/pulseaudio/src/tests/volume-ui.py[/FONT]
[FONT=Monaco]33204 sacha sacha /home/sacha/pulseaudio/src/tests/flist-test.c[/FONT]
[FONT=Monaco]33204 sacha sacha /home/sacha/pulseaudio/src/tests/rtstutter.c[/FONT]
[FONT=Monaco]33204 sacha sacha /home/sacha/pulseaudio/src/tests/thread-test.c[/FONT]
[FONT=Monaco]33204 sacha sacha /home/sacha/pulseaudio/src/tests/runtime-test-util.h[/FONT]
[FONT=Monaco]33204 sacha sacha /home/sacha/pulseaudio/src/tests/ladspa-dbus.py[/FONT]
```
[/I]
So i guess the structure looks like : file permission/owner/group/file path, separated by a space..

> Bad? I don't know.  Definitely against standards. Using /media is also against standards, but nobody seems to care. 

So where should I mount my NFS+ storage ?

---

### Post by TheFu on 2015-09-10
> **Sacha_Kozma said:**
> 
Haha sorry, I had to switch from the Live CD to my Mac and it was faster to take screenshots of the importants configs. Here is it :

```

[FONT=Monaco]33204 sacha sacha /home/sacha/pulseaudio/src/tests/thread-mainloop-test.c[/FONT]
[FONT=Monaco]33204 sacha sacha /home/sacha/pulseaudio/src/tests/volume-ui.py[/FONT] 
So i guess the structure looks like : file permission/owner/group/file path, separated by a space..

```

So where should I mount my NFS+ storage ?

Please use "code tags" for stuff like this going forward, not font-work.

Those aren't file permissions that I recognize - wouldn't know what to do with them. Scripting something like that shouldn't be hard - provided the permissions bits mapped 1-for-1 to chmod. They do not - or these examples have permissions nothing at all like normally used. Should be 4 octal numbers.  Plus it doesn't appear that ACLs are captured. ACLs aren't widely used in home environments.

If you are developing code, using git would be more important than backups, but I'd have backups too. 

Where to mount?  Anywhere EXCEPT the existing directories. Make something up. Mount there.  I use /misc and /D and /Data. I also use autofs to mount storage dynamically, only when desired.  BTW, never heard of NFS+ -  normally NFSv3 or NFSv4 are specified. Sounds like a brand-name attempt.  I ignore brands and read standards. If they don't follow the standards I need, keep looking.  With OSX, had a real problem because Apple didn't want to call standard things by standard names. Drove me crazy for the 2 weeks I tried to use OSX, but that is just me.

I'm difficult some times. ;)

---

### Post by Sacha_Kozma on 2015-09-10
Yes sorry i meant NFS ! It's strange for the permissions.. In fact BiT doesn't store ACL permissions, unless it is specified.. 

Ok I'll correct that as soon as my Ubuntu is working again and mount it in another place !

Haha yes I understand the struggle ;) but i like the fact that on OS X everything work "out of the box" (Time Machine, and so).. Very nice OS for a standard use !

---

