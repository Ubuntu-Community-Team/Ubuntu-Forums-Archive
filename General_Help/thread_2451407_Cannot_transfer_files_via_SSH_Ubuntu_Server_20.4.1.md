---
title: "Cannot transfer files via SSH Ubuntu Server 20.4.1 on Raspberry Pi 4"
date: 2020-10-03
forum: General Help
---

### Post by j-h-g on 2020-10-03
rsync, scp, and sshfs, all show the same behavior:
When trying to transfer files from one computer to an other over ssh, after entering a password the process hangs with no output to the terminal or logs. 

Any debugging tips or other assistance would a be a huge help. I've spent a whole day trying to make this work. 

More details in this stack overflow post [https://stackoverflow.com/questions/64094215/rsync-over-ssh-hangs-after-password-is-entered](https://stackoverflow.com/questions/64094215/rsync-over-ssh-hangs-after-password-is-entered)

---

### Post by HermanAB on 2020-10-04
I would type another /. after the destination username.

---

### Post by j-h-g on 2020-10-04
HermanAB, thanks for your reply.
The destination path doesn't seem to be the issue (at least it's not the only issue). Usually when the path is wrong it will give feedback like "directory not found," and exit. But in this case there is not feedback and the process stays active.

---

### Post by dinkidonk on 2020-10-04
How large are the files? Could take some time to complete, try to add option "--progress" to rsync..

---

### Post by j-h-g on 2020-10-04
Dinkidonk, the file is just a couple of KB. Adding the -P/--progress or -vvv flags doesn't ever display anything, nor does using the --log-file feature.

---

### Post by TheFu on 2020-10-04
Please post the exact command used.

The general format for scp is just like rcp:
```
scp /path/to/source/file  username@IP:/path/to/destination/
```
Or 
```
scp username@IP:/path/to/source/file  /path/to/destination/
```

To see more information, add a few -vvv to the command:
```
scp -vvv  /path/to/source/file  username@IP:/path/to/destination/
```

Filename globbing can be used for the source.
```
scp username@IP:/path/to/source/file*txt  /path/to/destination/
```

The trailing / on the destination isn't required, but commands like rsync get picky about that.

The source requires for the userid to have "read" access to the directory and files.
The destination requires for the userid to have "write" access.
These access controls follow the standard Unix model.

scp has a recursive mode.
sftp works the same way, but most Linux desktop file managers will support URLs: sftp://username@IP/path/to/source/ with drag-n-drop between 2 windows of the same file manager supported. It works as you'd want.  Local to local, local to remote, remote to local, and remote -to- remote.
rsync automatically used ssh.

If different the username on both systems is the same, then no need to include it in the commands.
If a port other than 22/tcp is used, the different commands support a -p or -P option. Always look up which for the command -----or----- just setup a **~/.ssh/config** file with a stanza for the connection parameters and alternate port. All ssh, scp, sftp, rsync, rdiff-backup and 50 other commands honor the config file and port, username, host settings so you'll never actually need to know or use them in any command line again.  An example:
```
host pi3 
  user osmc
  port 62280
  hostname 192.168.55.32

```
So, if I use ```
scp /etc/hosts pi3:
``` and on my current desktop my usename is "thefu", the command used will become
```
scp -P 62280  /etc/hosts osmc@192.168.55.32:
``` 
automatically. I don't need to know or remember the IP, username, or non-standard port.  It will do the same for ssh, sftp, rsync and 50 other ssh-based tools.

---

### Post by j-h-g on 2020-10-04
TheFu, thanks for your thorough reply. As requested, below is the exact command, along with the output (this is trying to go from one Raspberry Pi to another one):

```
rsync -vvvP [EMAIL="pi@192.168.0.20:/home/pi/test/test-file.md"]pi@192.168.0.20:/home/pi/test/test-file.md[/EMAIL] /home/pi/test/
opening connection using: ssh -l pi 192.168.0.20 rsync --server --sender -vvv.Lsfxc . /home/pi/test/test-file.md
pi@102.168.0.20's password:
```


After putting in the password it hangs indefinitely. I'm not 100% sure what all the flags in the verbose output mean when put together. It's a little strange that the terminal output is different if I run the same command on a Mac:
```
opening connection using: ssh -l pi 192.168.0.20 rsync --server --sender -vvve.LsfxCIvu . /home/pi/test/test-file.md  (10 args)
```

 
I've tried on multiple machines and it seems like it has something to do with the Raspberry Pi(s). I've used the same command on other machines running Ubuntu on the same network with no issues.

Could it be the the raspberry pi is an arm processor? Or that it's 32bit? I'm really grasping at straws here. The same thing is happening with Raspberry Pi OS light on both a Raspberry Pi 3 B+ and a Raspberry Pi 4.

---

### Post by TheFu on 2020-10-04
Try
```
scp     pi@192.168.0.20:test/test-file.md   /home/pi/test/
```

for 1 file, rsync is overkill.

---

### Post by j-h-g on 2020-11-14
**SOLVED**

This turned out to be a networking issue similar to these: 
[https://serverfault.com/questions/692026/cant-complete-ssh-connection-after-successfully-exchanging-keys-to-ubuntu-from](https://serverfault.com/questions/692026/cant-complete-ssh-connection-after-successfully-exchanging-keys-to-ubuntu-from)
[https://access.redhat.com/discussions/3265241](https://access.redhat.com/discussions/3265241)

My ISP requires that I use a [CenturyLink Technicolor 2100T]("https://www.centurylink.com/home/help/internet/modems-and-routers/technicolor-c2100t.html"), which is causing the issue (no fix found yet).

Thanks everyone for your responses.

---

### Post by TheFu on 2020-11-14
pi@102.168.0.20 seems a typo two posts above. hopefully, that wasn't the real cause.

If these systems are on the same LAN, you could put a cheap $5 switch in to avoid the router issue.

---

