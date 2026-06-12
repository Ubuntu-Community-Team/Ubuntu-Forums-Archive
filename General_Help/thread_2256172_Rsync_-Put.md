---
title: "Rsync -Put ?"
date: 2014-12-10
forum: General Help
---

### Post by danrichnc2 on 2014-12-10
I have a script that rsyncs two hard drives on a local network. It is important to me to continue partial transfers, use the most currently modified file, and to preserve the modification times across both drives. For this I used the "rsync -Put" options.

The problem I am finding is that on a partial transfer the mod time is newer than the source file, so that the -u parameter causes the partial to never be completed.

Can anyone think of a good solution to this problem?

---

### Post by nerdtron on 2014-12-10
-u for update right?
I have been using -arvh and it always update the destination files. Have no problems so far. Try other options from the man page of rsync.
```
man rsync
```

---

### Post by danrichnc2 on 2014-12-10
Thanks for your quick reply! If I use your options, it does not keep the partial transfers.  I have also noticed that rsync will overwrite the destination file if it is different, even if it is the most currently modified file, so be careful.

---

### Post by papibe on 2014-12-10
Hi danrichnc2.

The --partial option does not work well with the --update option (-u).

A partial transferred file would have a local modified time instead of the source's time. Only when 100% is completed, the original source's time is set.

If you are syncing to a server as a backup, I'd would use only --partial. For instance:
```
rsync -avP source/ server:path/to/backtup/source/
```
(-P is --partial and --progress)

In case you're syncing two workstations (both can modify the data). I would use two rsync commands. One for small/medium sized files with the --update option, and another for large files using the partial option. For example:
```
rsync -av --update --exclude=relative/path/to/big_file.data  /path/to/dir/ machineB:/path/to/dir/

rsync -avP /path/to/big_file.data machineB:/path/to/big_file.data
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by danrichnc2 on 2014-12-10
I like your thinking papibe, it was my first thought too; however, I found a solution that works with with one rsync pass.

#changes the mod times for the partial files
touch -t 197001010000 /destination_path/.temp/*
#keeps partials isolated in a temporary folder
rsync -avPuH --partial-dir=.temp /source_path/ /destination_path/

The solution is not really elegant, but it works.  The setup is two workstations and I'm fairly surprised that it hasn't been a problem for more folks. I kinda learned the hard way that without the --update option, changes made by the destination workstation are erased.  Hopefully this will help someone else.  Thanks, you guys rock!

---

