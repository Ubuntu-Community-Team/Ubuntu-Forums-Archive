---
title: "rsync not deleting files: just renames file with a tilde symbol (~) at the end"
date: 2023-12-27
forum: General Help
---

### Post by freeflyjohn on 2023-12-27
I am using rsycn over a wiregaurd vpn tunnel for offsite backups.

When I delete a file from the source folder and re-run rsync, the file is not deleted on the destination folder.

Instead the file is just renamed with a tilde symbol (~) at the end of the file extension
[INDENT]e.g. if the file to be deleted is named readme.txt, then after running rsync the file gets remaned to readme.txt~
[/INDENT]

Why doesn't rsync delete the file from the destination folder ?

I dont have the same problem when using rsync on my local network, it only happens when I run it over the vpn tunnel.

The rsync command is shown below:

```

rsync -a -b --progress -l --delete --rsh='ssh -p 12345’ user@192.168.6.1:/media/general/SWAP/vpntest /Volumes/OSB_TEST

```

I have to use the --rsh option because the Ubuntu SSH is running on a different port (e.g. 12345) rather than the standard port (22).

The setup is shown in the diagram below...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293250&stc=1[/IMG]

---

### Post by MAFoElffen on 2023-12-27
It's becaseu you have one too many options in your command of this:
```

rsync -a -b --progress -l --delete --rsh='ssh -p 12345&#8217; user@192.168.6.1:/media/general/SWAP/vpntest /Volumes/OSB_TEST

```
Change that to this
```

rsync -a --progress -l --delete --rsh='ssh -p 12345&#8217; user@192.168.6.1:/media/general/SWAP/vpntest /Volumes/OSB_TEST

```
Removing the "-b" option... 

The reason it was 'renaming' the file with that suffix was because with the '-b' option, it tells it to leave a backup file, and without using the '--suffix' option, the default suffix is the tilde sign (~)... So it was doing what you were telling it to do... Which those options, used in conjunction with --delete, vary what the '--delete option does, renaming the backup file to indicate it is no longer there in the source, instead of deleting it...

---

### Post by freeflyjohn on 2023-12-27
Many thanks MAFoElffen :P

I can't remember where I got the -b switch from, its been a while since I used rsync but I documented the syntax and must have forgotten about the -b switch !

---

### Post by MAFoElffen on 2023-12-27
Please try that to test. You could use "--dry-run" to test the results of what it would do.

If solved, please use the "thread Tools" link at the top of the page to mark your thread as "Solved". That will help others find what worked for you, to help with their own similar problems.

---

### Post by TheFu on 2023-12-28
If ssh is working between the 2 systems, there's no need for a VPN.
Also, any specific ssh options can be put into the client-side ~/.ssh/config file and those options will be used automatically, greatly simplifying all ssh-based tools, including rsync.

~/.ssh/config
```
host proxy.example.com
  user backup11923
  hostname 149.248.61.99
  IdentityFile ~/.ssh/id_vultr_ed25519
  port 59099

```
Then the rsync "pull" command looks like this:

```
rsync -a --progress -l --delete  proxy.example.com:/media/general/SWAP/vpntest      /Volumes/OSB_TEST
```
It will use the user, hostname, port and identity specified automatically based on proxy.example.com as the "host".  This really cleans up commands AND documents it.  If you need anything different, just create a slightly different named "host" with the other settings.

When I use rsync, I generally want the source directory to be directory/ so all the files inside it are pulled, but not the directory name.  To each their own.

---

### Post by ActionParsnip on 2023-12-28
If you add "-P" then if the communication breaks then you can resume it where you left off

---

