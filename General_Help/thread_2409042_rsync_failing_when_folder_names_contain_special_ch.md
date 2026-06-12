---
title: "rsync failing when folder names contain special characters"
date: 2018-12-27
forum: General Help
---

### Post by Adam_Jacobs on 2018-12-27
I have recently upgraded my Mythtv box from Ubuntu 14.04 to 18.04

One consequence of this is that the rsync script that I use for backup no longer works. Specifically, it fails when the folder name contains special characters. At least I think that's the problem: the only files for which it fails are in a folder with a special character (ü) in the name, so I would be amazed if the problem were not related to the special characters.

The error messages from rsync look like this:

```
rsync: mkstemp "/media/synology/mythtv/music/Rachmaninoff/Konzerte fÃ¼r Klavier und Orchester Nr. 1 - /.01-Nr.3 d-moll op.30 Allegro ma non troppo.mp3.pGwOsK" failed: No such file or directory (2)
```

I'm trying to back up onto an external Synology NAS drive, and a little googling suggested that maybe I should add the isocharset=utf8 option to the fstab entry where I mount the NAS drive. So I did, but that didn't help. It now looks like this:

```
//synology.local/htpc	/media/synology	cifs	auto,guest,noperm,_netdev,vers=2.0,iocharset=utf8	0	0

```
Any ideas how I can get it to work? I don't think this is a problem with my Synology NAS drive, because it worked fine before I upgraded.

---

### Post by sudodus on 2018-12-27
You could check that you have the correct local version of the language for **ü** (and maybe other special characters) to be managed in file names. But it happens that a feature that works in one version of Ubuntu is broken in the next version.

Otherwise I have no solution, but a workaround:

Avoid the problematic special characters in file names. For example, you can rename the files by converting the characters

ü --> ue
Ü --> UE
å --> aa
Å --> AA
ä --> ae
Ä --> AE
ö --> oe
Ö --> OE

---

### Post by Adam_Jacobs on 2018-12-30
OK, I figured this out. The solution was to mount the NAS drive using NFS instead of CIFS. Then everything works just fine.

Maybe you'd consider that a workaround rather than a solution if you have some specific reason for using CIFS instead of NFS, but given that I don't really mind which protocol I use just so long as it works, I'm going to mark this thread as solved.

---

### Post by sudodus on 2018-12-30
Congratulations and thanks for sharing your solution :-)

---

