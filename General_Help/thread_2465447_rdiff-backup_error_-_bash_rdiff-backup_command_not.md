---
title: "rdiff-backup error - bash: rdiff-backup: command not found"
date: 2021-08-02
forum: General Help
---

### Post by freeflyjohn on 2021-08-02
I am trying to backup data from my Mac Book Pro to my server (Ubuntu 20.04) by running rdiff-backup from the server via SSH, but I get the following error:

```

rdiff-backup -v9 macuser@macbookpro.fritz.box::/Users/macuser/Downloads/rdiff /media/storage/Backup/rdiff
2021-08-02 11:05:29.760350 +0100  <CLIENT-16285>  Using rdiff-backup version 2.0.0
2021-08-02 11:05:29.760428 +0100  <CLIENT-16285>      with cpython /usr/bin/python3 version 3.8.10
2021-08-02 11:05:29.769811 +0100  <CLIENT-16285>      on Linux-5.4.0-80-generic-x86_64-with-glibc2.29, fs encoding utf-8
2021-08-02 11:05:29.770388 +0100  <CLIENT-16285>  Executing ssh -C macuser@macbookpro.fritz.box rdiff-backup --server
2021-08-02 11:05:29.771440 +0100  <CLIENT-16285>  Client sending (0): ConnectionRequest: Globals.get with 1 arguments
2021-08-02 11:05:29.771676 +0100  <CLIENT-16285>  Client sending (0): version
Password:
bash: rdiff-backup: command not found
2021-08-02 11:05:33.066059 +0100  <CLIENT-16285>  Fatal Error: Truncated header string (problem probably originated remotely)

Couldn't start up the remote connection by executing    

ssh -C macuser@macbookpro.fritz.box rdiff-backup --server

Remember that, under the default settings, rdiff-backup must be
installed in the PATH on the remote system.  See the man page for more
information on this.  This message may also be displayed if the remote
version of rdiff-backup is quite different from the local version (2.0.0).




```

rdiff-backup on the server is version 2.0.0 and rdiff-backup on the Mac is version 2.0.5.

rdiff-backup work on both the server and the Mac when used locally.

If I SSH from the server to the Mac, the rdiff-backup command is recognised.

I noticed the comment in the error that "rdiff-backup must be installed in the PATH on the remote system" but I don't know how to do this despite reading the rdiff-backup FAQ's which states:[INDENT]**Why does rdiff-backup say it's not in my $PATH? It is when I login!**[/INDENT]
[INDENT]If you get an error like sh: line1: rdiff-backup: command not found, but rdiff-backup is in your $PATH when you login to the remote host, it is happening because the value of bash's $PATH is set differently when you login to an interactive shell than when you run a command remotely via SSH. For more information, read the bash manpage and look at your .bashrc and .bash_profile files.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]In particular, this can happen if rdiff-backup was installed via Fink on a remote Mac OS X system. /sw/bin is magically added to your $PATH by the script /sw/bin/init.sh when you login with an interative shell. Fink did this behind the scenes when you set it up. Simply add /sw/bin to your path manually, or copy rdiff-backup to a directory that is in your $PATH.[/INDENT]

Is the path the issue and if so, does it need to be fixed on the server or the Mac ?  And if so, how do I fix this ?

Some background info:


I originally used rsync (via SSH) to backup my Mac to my server, the data was 'pushed' to the server as shown in the diagram below:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288908&stc=1[/IMG]

The rsycn command ran from the Mac was:
```

rsync -a -b --rsh='ssh -p 12345' --progress --backup-dir="deleted_$(date +\%Y-\%m-\%d)" --delete --exclude-from /Users/macuser/.rsync/exclude_mac.txt /Users/macuser serveruser@HOMESERVER:/media/storage/Backup/Mac/rsync


```

I now want to use rdiff-backup (via SSH) to backup my Mac to my server and this time 'pull' that data from the Mac to the server as shown in the diagram below:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288907&stc=1[/IMG]

The rdiff-backup command ran from the server was:

```

rdiff-backup -v9 macuser@macbookpro.fritz.box::/Users/macuser/Downloads/rdiff /media/storage/Backup/rdiff

```

---

### Post by freeflyjohn on 2021-08-02
Fixed it...

On the Mac in the users home directory, there needs to be a file called .bashrc

i.e. 

/Users/macuser/.bashrc


In this case, rdiff-backup was installed on the Mac using:

```

sudo pip3 install rdiff-backup

```

The folder rdiff-backup was installed in on the Mac is '/usr/local/bin'

So I created the file '/Users/macuser/.bashrc' and in that file I put the path where the rdiff-backup command is located: 

```

PATH=/usr/local/bin:$PATH

```

Now when the server calls a command on the Mac via SSH, it will also check the path '/usr/local/bin' on the Mac which is where rdiff-backup is installed.

---

### Post by freeflyjohn on 2021-08-02
I do get a warning after the backup, about the different versions of rdiff-backup on the Mac and the server:

[INDENT]"Warning: Local version 2.0.0 does not match remote version 2.0.5."[/INDENT]

The Mac is running version 2.0.5 and the server is running version 2.0.0

How can I make the versions match, so that they are both 2.0.5 (or both 2.0.0) ?

To install rdiff-backup on Ubuntu (which is the older version 2.0.0)  I used...

```

sudo apt-get update
sudo apt-get install rdiff-backup

```

To install rdiff-backup on the Mac (which is the newer version 2.0.5) I used...

```

sudo pip3 install rdiff-backup

```

---

