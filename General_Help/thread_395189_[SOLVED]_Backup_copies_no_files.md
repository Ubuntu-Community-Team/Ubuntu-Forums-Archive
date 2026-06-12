---
title: "[SOLVED] Backup copies no files"
date: 2007-03-27
forum: General Help
---

### Post by dcroxton on 2007-03-27
Can some kind soul help me get a backup working?

I tried the "simple backup config" program, but nothing happened when I ran the backup.  Well, the process started, then terminated almost immediately, and no files got copied.

So I've been poking around trying to get rsync to work.  After following a how-to and finding nothing copied, I added the verbose output and ran the following command:

```
rsync -avvvz myuser@myserver:/backupdir/myuser /home/myuser/
```

The output was:

```
receiving file list ... 
server_sender starting pid=10746
make_file(1,dcroxton)
expand file_list to 4000 bytes, did move
recv_file_name(dcroxton)
received 1 names
done
recv_file_list done
get_local_name count=1 /home/dcroxton/
recv_files(1) starting
send_file_list done
send_files starting
generator starting pid=11470 count=1
delta-transmission enabled
recv_generator(dcroxton,0)
generate_files phase=1
recv_files phase=1
generate_files phase=2
send_files phase=1
send files finished
total: matches=0  tag_hits=0  false_alarms=0 data=0
recv_files finished
recv_generator(dcroxton,0)
generate_files finished

sent 16 bytes  received 344 bytes  102.86 bytes/sec
total size is 0  speedup is 0.00
_exit_cleanup(code=0, file=main.c, line=1298): about to call exit(0)
```

No doubt I am doing something incredibly stupid here...I just don't know what.  I tried running the command as root in case it was a permissions issue, but that didn't help.  I tried moving the backup directory to one under my home directory on the remote machine, but that didn't help, either.  (The username for the local and remote host is the same.)  I just don't know where to look.

Thanks,
Derek

---

### Post by raja on 2007-03-27
For starters, rsync should be called with source first and destination second. So maybe you should try after changing the order of the directory names. You can run with the -n option to just test it without copying any files.

---

### Post by dcroxton on 2007-03-28
I knew it was something stupid. :)  Actually, the rsync man page is rather confusing, and shows source and destination in both places.  The how-to I copied from had the source second, but I suspect that is related to the fact that it was using "-e ssh."  I tried removing the ssh because it didn't work and I wanted to try it without, but I guess that changed the meaning of the command.

In any case, it works now, and I am grateful.

Sincerely,
Derek

---

