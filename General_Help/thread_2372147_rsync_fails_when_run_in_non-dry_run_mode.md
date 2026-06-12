---
title: "rsync fails when run in non-dry run mode"
date: 2017-09-22
forum: General Help
---

### Post by accounts0 on 2017-09-22
So this works:
```

rsync -vrlpEtgohXtn --progress -cD --stats --exclude-from='/foo/bar/Snafu/rsync_excludes.txt' /mnt/foo/bar/ /media/foo/ExternalHDD/bar

```

But not this:
```

rsync -vrlpEtgohXt --progress -cD --stats --exclude-from='/foo/bar/Snafu/rsync_excludes.txt' /mnt/foo/bar/ /media/foo/ExternalHDD/bar

```

When I run it without the -n flag, it hangs while scanning paths defined in rsync_excludes.txt, whose contents is as follows:
```

/mnt/foo/bar/Blockchain/
/mnt/foo/bar/VirtualMachine/Virtualbox/VMs/


```

---

### Post by SeijiSensei on 2017-09-22
> /mnt/foo/bar/VirtualMachine/Virtualbox/VMs/
I don't know if this applies to you, but the default location for VMs is ".../VirtualBox VMs/".  Notice the capitalization of "Box" and the space before VMs.  There is no separate "VMs" subdirectory in a normal VB installation.

---

### Post by accounts0 on 2017-09-25
> **SeijiSensei said:**
> I don't know if this applies to you, but the default location for VMs is ".../VirtualBox VMs/".  Notice the capitalization of "Box" and the space before VMs.  There is no separate "VMs" subdirectory in a normal VB installation.

Yea, I just change that in the VirtualBox main window's Preferences, to point that location away from the SSD to the larger HDD. Unless someone can prove me wrong, I don't believe this has anything to do with the rsync command failing.

---

### Post by dragonfly41 on 2017-09-26
Try installing grsync (the gui for rsync) to see if any errors are reported in grsync for your dry run.

---

### Post by HermanAB on 2017-09-26
Also note that rsync can fail due to packet loss when an interface gets overloaded.  You can fix that by limiting it with the bandwidth parameter.

---

### Post by accounts0 on 2017-09-27
Thanks, will try with that GUI package.

Regarding packet loss, that doesn't explain why when it does fail it's while scanning paths defined in the --exclude-from .txt file. When it does the dry-run it appears to exclude those paths, which is confusing to me since basically nothing's changing except removing the -n flag.

---

