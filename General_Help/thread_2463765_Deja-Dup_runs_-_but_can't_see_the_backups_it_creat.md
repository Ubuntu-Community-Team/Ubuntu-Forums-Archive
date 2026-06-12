---
title: "Deja-Dup runs - but can't see the backups it creates?"
date: 2021-06-17
forum: General Help
---

### Post by astronomertom on 2021-06-17
I've been using deja-dup for my backups and it *seems* to run fine.  Starts with a full backup, then appears to run incrementals normally.  I see the files out on the destination volume with appropriate dates and reasonable sizes.

Yet if I run

```
duplicity collection-status file://media/UbuntuBacku4TB/Wheeler/<user>
```

I get:

```
Last full backup date: none
Collection Status
-----------------
Connecting with backend: BackendWrapper
Archive dir: /home/<user>/.cache/duplicity/bc716aaecc8efc569f7a72751d49e55d

Found 0 secondary backup chains.
No backup chains with active signatures found
No orphaned or incomplete backup sets found.
```

Apparently duplicity is unable to find the backups, so I doubt I can restore anything from the files.

The other 'fixes' for this I've found don't seem to work - most were just bad paths, etc.  I even tried deleting the old backups, re-entering the backup parameters, and starting fresh, yet it still does this.  If I run deja-dup in one of my other user accounts on the same machine, it works fine and sees the backups.

Is there a way to fix this so it sees my backups?

Barring that, is there a way to reset deja-dup so it will return to proper functionality.  I suspect there might be a bad parameter floating around in deja-dup that is confusing it.

Thanks,
Tom

---

### Post by deadflowr on 2021-06-18
You're missing the extra / after file.
Should be three.

---

### Post by astronomertom on 2021-06-19
I was doing /// for quite some time, but then it's even worse.  I get:

```
Giving up after 1 attempts. FileNotFoundError: No such file or directory
```

Then I found a thread which suggested I needed to do only // and thought it was progress as it at least generated some output.

So I guess I'm still stuck... 

Thanks for the clarification.

---

### Post by deadflowr on 2021-06-19
3 /// is at least giving an error or that there is an issue.
2 // will respond with what was outputted from post #1 regardless
(note that with just 2 // you can even misspell things and it will still show as it does)

For possible recovery to try and sort things out check out deja-dup's worst case page here: [https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase]("https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase")

Another small thing I see is unless you manually mount the location, using tools outside of how Ubuntu usually mounts to /media, it's in the wrong directory.
Normally drives mounted in /media are located in a user-named sub-directory of the /media directory like /media/username replacing username with the current user's name.
But I don't know how you've set things up, so for all I know you set the mountpoints manually...

> is there a way to reset deja-dup so it will return to proper functionality
probably using dconf-editor. (would need to be installed)
deja-dup settngs are in org > gnome > deja-dup.

---

### Post by astronomertom on 2021-06-20
Yes, I do have a defined mount point in /media.  Part of my attempt to get the external USB disk to behave more like Mac OSX so all users would have full access to the mounted disk.  It sort of works.  But other accounts on the same machine have no problems with their backups so I suspect my hacked mount point is not the root problem.

Already looked that the settings in dconf-editor and nothing obvious there.

Thanks for troubleshooting link.  I don't think I encountered that in my searches.  Looks like it might be a way to use my backups if all else fails.

Tom

---

