---
title: "Scripts executed in SSH"
date: 2007-12-24
forum: General Help
---

### Post by Spazztastic on 2007-12-24
Ok, so I have roughly ten Cisco 2600 series routers, two Catalyst 3550 Switches, and one 2511-DC Access Server. I'm planning on setting them up in my house and having them accessible via SSH. So, I have remote access to my house and lets say that for whatever reason I have to shut down this said equipment, I want to be able to execute a simple command to backup their configurations via SCP and shut them down. So, what I hoped would be done is connect to the router, backup the configuration, then I can have whoever is nearby just flip the breaker and shut them off. Here's what would need to be done:

ssh cisco@10.1.1.100

Then, while inside of the shell, it would have to do this:
```
enable
pause 3
<password>
pause 3
copy running-config startup-config
pause 10
copy running-config scp://10.1.1.120
exit
```

Is there any way to do this? Preferably so I can just go:
```
taylor@nix:~$ ./backuplol.sh
```
If I'm being vague or if I have to get further in depth, please say so.

---

### Post by Spazztastic on 2007-12-24
Bump

---

### Post by p_quarles on 2007-12-24
Not sure exactly what you're asking, but if you just want to make a shell script out of that set of commands, just put them in a file. The first line should read:
```
#!/bin/sh
```
Then you'll need to make the file executable:
```
chmod 744 backuplol.sh
```
Finally, if you have a Bourne shell on these routers, why not just use that to shut them down safely?
```
shutdown -P now
```
You don't need physical access to do that.

---

### Post by Spazztastic on 2007-12-24
> **p_quarles said:**
> Not sure exactly what you're asking, but if you just want to make a shell script out of that set of commands, just put them in a file. The first line should read:
```
#!/bin/sh
```
Then you'll need to make the file executable:
```
chmod 744 backuplol.sh
```
Finally, if you have a Bourne shell on these routers, why not just use that to shut them down safely?
```
shutdown -P now
```
You don't need physical access to do that.

The Cisco Internetwork Operating System supports SSH v1 and v2 access. It doesn't support the majority of actual shell scripts. What I am talking about is while having the SSH terminal open, it would execute commands on the remote party.

So, say that I am on my server. On my server I type in:```
./backup.sh
```
After doing so, the server opens up an SSH connection to a router. Then it performs a set number of commands inside of it. Only, when I would do that command it wouldn't continue to do the ones listed inside of the script.

---

### Post by p_quarles on 2007-12-24
Hmm. I'd say a situation like this would be better served used rsync. You'd want to create an alias or script with something like this:
```
rsync -vrtplze ssh --progress --stats --delete cisco@10.1.1.100://running-config /home/username/backupdir
```
rsync will work with any OS that can be connected to via SSH. Have a look at the rsync man page for full details, but basically this will give you a verbose, recursive synchronization between the source (first path) and the destination (second path). It will also delete any files from the destination directory that no longer exist in the source directory, making your backup a good drop-in replacement for any lost configs. 

You can also use the --password-file= option to automate authentication. 

This strikes me as your best bet, because it shouldn't rely on the scripting capabilities of the router's shell. You can also use the --dry-run option, which will give you all the verbose output, but won't actually transfer or delete any files. That's the best way to test if this is a viable solution or not.

---

