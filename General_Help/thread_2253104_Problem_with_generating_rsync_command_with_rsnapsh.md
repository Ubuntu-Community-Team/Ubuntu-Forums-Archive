---
title: "Problem with generating rsync command with rsnapshot"
date: 2014-11-17
forum: General Help
---

### Post by errata2 on 2014-11-17
So, I'm trying to use rsnapshot to sync remote files to my own computer. However, I have some trouble when I need to access files which are not owned by user who is SSH-ing to the remote machine.


My /etc/rsnapshot.conf looks like this:

```
config_version  1.2
snapshot_root   /shared/.backup/
cmd_cp          /bin/cp
cmd_rm          /bin/rm
cmd_rsync       /usr/bin/rsync
cmd_ssh         /usr/bin/ssh
cmd_logger      /usr/bin/logger
cmd_du          /usr/bin/du

retain      hourly  6
retain      daily   7
retain      weekly  4
retain      monthly 3

verbose     2
loglevel    5
logfile     /shared/.backup/rsnapshot.log

ssh_args    -i ~/.ssh/id_rsa -p 62222

# BACKUP DEFINITIONS
backup  username@10.10.11.11:/          dev.local.root/     exclude_file=/shared/.backup/exclude.root,+rsync_long_args=--rsync-path='sudo rsync',rsync_short_args=-zalhHx
```

After running **rsnapshot hourly** I see this error:

```
bash: sudo rsync: command not foundrsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: remote command not found (code 127) at io.c(226) [Receiver=3.1.0]
----------------------------------------------------------------------------
rsnapshot encountered an error! The program was invoked with these options:
/usr/bin/rsnapshot hourly
----------------------------------------------------------------------------
ERROR: /usr/bin/rsync returned 127 while processing username@10.10.11.11:/
```


If I check my rsnapshot.log file, I can see that rsnapshot tried this command:

```
/usr/bin/rsync -zalhHx --delete --numeric-ids --relative --delete-excluded --exclude-from=/shared/.backup/exclude.root --rsync-path='sudo rsync' --rsh=/usr/bin/ssh -i ~/.ssh/id_rsa -p 62222 username@10.10.11.11:/ /shared/.backup/hourly.0/dev.local.root/
```

If I try to run the same command in terminal, I get this error:

```
Unexpected remote arg: username@10.10.11.11:/
rsync error: syntax or usage error (code 1) at main.c(1348) [sender=3.1.0]
```

However, if I put quotation marks around --rsh part everything works fine:

```
/usr/bin/rsync -zalhHx --delete --numeric-ids --relative --delete-excluded --exclude-from=/shared/.backup/exclude.root --rsync-path='sudo rsync' --rsh='/usr/bin/ssh -i ~/.ssh/id_rsa -p 62222' username@10.10.11.11:/ /shared/.backup/hourly.0/dev.local.root/
```

Some facts which are good to know :)

- On remote machine, there is a line **username ALL=(ALL) NOPASSWD:ALL** in sudoers file.
- I can normally SSH to the remote machine with my SSH key.
- I can invoke sudo commands on server without being asked for a password.
- I cannot SSH as root to remote machine because of **PermitRootLogin on** and **AllowUsers username** in sshd_config
- If I try **ssh username@10.10.11.11 -p 62222 -i ~/.ssh/id_rsa which rsync**, the output is **/usr/bin/rsync**
- If I try **ssh username@10.10.11.11 -p 62222 -i ~/.ssh/id_rsa echo $PATH**, the output is **/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games**

So.... My question is simple: how do I properly construct this rsync command in rsnapshot?

Thanks for help!

---

### Post by TheFu on 2014-11-17
So ... I've never used rsnapshot, but I routinely use librsync-based tools for backups.

I would begin by setting up the ~/.ssh/config file on the client machine to remove the need to specify username, IP address, port and the default key.
Simplify and retest.
```

host sync-srv
 user username
 hostname 10.10.11.11
 port 62222 
```
Just use "sync-srv" in the command going forward - all rsync/ssh tools understand this and will use the username, ip, port automatically.

BTW - ssh has been the default for rsync for many, many years - no need to use the -e or -rsh options.

Anyway, if nobody else responds, I can share alternative options that I use for backups which are root-ish, but not root.

---

### Post by Lars Noodén on 2014-11-17
In your --rsync-path, maybe you could try absolute paths?

---

