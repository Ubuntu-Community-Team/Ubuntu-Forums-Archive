---
title: "128GB SSD and 5GB VAR Partition is low on space"
date: 2020-10-01
forum: General Help
---

### Post by bpazolli on 2020-10-01
Pretty much a novice on Linux. I set up a laptop to only use Ubuntu 18.04.2 LTS, a while back. The laptop quickly started complaining that the VAR partition was filled up. I followed something similar as [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) and made the following:
100GB /home
15GB /root
4GB /tmp
5.1GB /var
4GB Swap
250MB /boot

I investigated this when I first noticed the issue and I think I came to the realisation that most advice was that /var could be a lot smaller (but possibly outdated advice), and I tracked down that there was some issue with snaps not automatically purging themselves of old version. I think I tried the auto-clean up command I found, but it didn't work, and in one moment I just started deleting some of the files. 

This issue has significantly impeded my enjoyment (updating and installing new software became a hassle) of the system and I generally stopped using the laptop. In retrospect I think I was too clever trying to create multiple partitions for such a small drive, and I've since been trying to work out how to recombine the partitions but haven't found a straightforward guide. Any assistance would be appreciated.

---

### Post by CelticWarrior on 2020-10-01
> [COLOR=#000000]Pretty much a novice on Linux.[/COLOR]

If so then I would recommend using the standard partitioning that will automatically avoid those issues. There's no point in having separated /var and /boot unless in specific SERVER settings. For a single user laptop it makes no sense. Also now you don't even need a swap partition because Ubuntu uses a swapfile by default.

If you had let the installer do it automatically it would have created just a small EFI partition (where applicable: UEFI systems in UEFI mode) and / (root). That's it, no more mucking about.

Unfortunately there's no way to "recombine". Do your backups and reinstall with the recommended settings.

---

### Post by oldfred on 2020-10-01
Its a lot easier to reinstall & restore from your backups.
Your user settings are all in /home, only if you manually edited system files in /etc would you possibly need those (but do not auto restore /etc), and list of installed apps.

You can copy each partition back into /'s folder for that partition and remove mount in /etc/fstab. 
Reverse of this:
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) & 
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

And if you have to do that for every partition, then you can see new install is easier.

---

### Post by ActionParsnip on 2020-10-01
What is the output of:
```

cd /var; du -sh *

```
Thanks

---

### Post by bpazolli on 2020-10-02
> **ActionParsnip said:**
> What is the output of:
```

cd /var; du -sh *

```
Thanks

I don't think that command works unless you're super user or whatever. See below were the biggest items. So mostly snapd stuff. I've decided to take the others advice and start from again. I have very little on this laptop but a couple of documents, so no big loss. I'm going to upgrade Ubuntu 20.04.1 LTS. So hopefully that works out better.

```

88M	./crash
183M	./cache/oracle-jdk8-installer
234M	./cache/apt/archives
260M	./lib/apt
260M	./lib/apt/lists
296M	./lib/snapd/seed
296M	./lib/snapd/seed/snaps
351M	./cache/apt
489M	./log/journal
489M	./log/journal/ed2afca4d6734287a7a3b7a355b1e52c
495M	./log
563M	./cache
720M	./lib/snapd/cache
1.8G	./lib/snapd/snaps
2.8G	./lib/snapd
3.2G	./lib
4.3G	.

```

---

### Post by oldfred on 2020-10-02
I do not have any snaps, but did not realize they were that large.
```
2.8G	./lib/snapd
```

---

### Post by bpazolli on 2020-10-02
Would it be worthwhile avoiding snaps due to the space constraint on this laptop?

---

### Post by ajgreeny on 2020-10-03
> **bpazolli said:**
> Would it be worthwhile avoiding snaps due to the space constraint on this laptop?
Yes, definitely!

Snaps do use a lot of disk space as they share no library files with the rest of the system even if those library files are already present on disk.
Search for PPA repos for all the snap applications you have and you may be lucky.

---

