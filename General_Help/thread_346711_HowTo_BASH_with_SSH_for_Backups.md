---
title: "HowTo: BASH with SSH for Backups"
date: 2007-01-26
forum: General Help
---

### Post by matthewstory on 2007-01-26
I see a lot of questions on here all the time about what is the best backup method, and there is generally a lot of debate about which program is best.  Wether your preference is to do a tar backup or a rsync backup, the best practice for any of these methods is to back your data up to an offsite server periodically, regardless of your local backups.  But scripting remote backup has a tendancy to be difficult and insecure, as most secure forms of backup have a password challenge, which makes automated scripting seem impossible.  This howTo will walk you through how to set up your SSH server and client for secure id_dsa based authentication, which will allow you to write scripts to automate your backup proceedures.  I have also attached an example script (under the LGPL v. 2.1) to illustrate the proper method of calling rsync with ssh from a script.

This HowTo is based on a blog post I made as part of an ongoing series called BASH Hacks:

[http://codeandfury.blogspot.com/2007/01/bash-hacks-scripting-with-ssh.html](http://codeandfury.blogspot.com/2007/01/bash-hacks-scripting-with-ssh.html)

One more note before we begin . . . alot of offsite backup services provide you only with SFTP access to their server, in which case RSYNC won't work, but this howTo will still work if you want to use tar backups offsite, and for your server, the work needed can all be done using only commands available to you through SFTP (in other words you don't need a full BASH shell and SSH access to your server).

To start, you'll need to generate a master key. To do this you'll need to use the ssh-keygen utility:


```
matt@$ ssh-keygen -t dsa -b 2048 -f ~/.ssh/id_dsa
```


This will generate a 2048 bit dsa key pair and put it into two files: id_dsa which is your private key, and id_dsa.pub which is your public key. You'll need to take the public key and put it into a file called authorized_keys:

```

matt@$ touch ~/.ssh/authorized_keys
matt@$ chmod 600 ~/.ssh/authorized_keys
matt@$ cat ~/.ssh/id_dsa.pub >> ~/.ssh/authorized_keys

```

You'll then need to edit the /etc/ssh/ssh_config file on your client machine and uncomment the following line:

```

# IdentityFile ~/.ssh/id_dsa

```

We now need to upload the authorized_keys file to the server that you will be connecting to. Every server you will connect to will need this authorized_keys file, and each client you will connect from will need the id_dsa and id_dsa.pub keys:

```

sftp > mkdir .ssh/
sftp > put ~/.ssh/authorized_keys .ssh/authorized_keys

```

Once you've done this, than you will be able to connect via SSH or SFTP without having to authtenticate via a password challenge. You can test this by trying to ssh or sftp to your server:

```

matt@$ ssh <Server FQDN or IP>
matt@$ sftp <Server FQDN or IP>

```

If you are logged directly into the server without a password prompt, then you have succeeded. If not, you may not be able to authenticate via dsa key pair to your SSH server, though this is turned on by default. If you are unable you should check the /etc/ssh/sshd_config file on your SSH server to see if dsa key pair verification is enabled.

To use SSH in a script now, you just need to know how to execute commands remotely with SSH from a BASH script. To do this you merely need to use your standard ssh command followed by the command(s) you wish to execute in quotes:

```

ssh <Server FQDN or IP> "command1; command2; command3;"

```

For SFTP it gets a little more complicated, as SFTP requires the use of a batch file to execute commands. Create a batch file with the list of commands you want to execute, one command per line:

```

put /path/to/file
get /path/to/file
lcd /local/path/change/
cd /remote/path/change/
put file
get file
bye

```

The line bye at the end will terminate the SFTP session. To execute a batch file with SFTP use the -b option like so:

```

sftp -b /path/to/batchfile.bat <Server FQDN or IP>

```

Once all of this is done, all you need to do is write a script, and allow the user you have just configured id_dsa configuration for to execute the script.  You need only execute the script . . . such as the example script in attached to this post, and voila!

Enjoy Backing up!

---

