---
title: "how do i specify a port number in rdiff-backup?"
date: 2019-08-09
forum: General Help
---

### Post by Skaperen on 2019-08-09
my server operates sshd on an obscure port number and not on the standard port 22.  this has eliminated flooding my log file with lame password attempts (they have been disabled for years).  i can specify a port with -p on ssh and with -e on rsync.  i'm trying to set up rdiff-backup to see if works as well as the backup script i wrote many years ago (has worked well with no changes for years).  a review of rdiff-backup documentation shows a lot of nice features mine does not have, but i can't tell from that if any features are missing, besides being able to set the port number.  if there is a way to set the port number, that might let me actually use rdiff-backup.

hint:  the port number i use is not 1728

---

### Post by Holger_Gehrke on 2019-08-09
Found after three minutes of googling: [https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg02169.html](https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg02169.html)

Holge

---

### Post by #&amp;thj^% on 2019-08-09
Unless I miss-read you, will something like this work for you?
```
rdiff-backup /source/dir "-p 1234 user@host.com"::/remote/dir
```
Include the correct paths & -p# (port number)

---

### Post by Skaperen on 2019-08-10
if **[FONT=courier new]rsync[/FONT]** constructs the ssh command *before* tokenizing, that could work.  but i can also see general exploit exposure if it works that way.  that's why all *my* programs construct commands in a pre-tokenized state.

---

### Post by TheFu on 2019-08-10
I don't specify the port.  It is picked up by the ~/.ssh/config setting for the ssh connection.

Set the stanza for the backup connection in that file with the alias, userid, port and it will be picked up.
Since it is a backup, I assume you are using a root or root-equiv account for the connection and running from root or root-equiv account.

The backup server /root/.ssh/config file contains this
```
host hadar-backups
  user backup684
  hostname 199.101.32.163
  port 61200
```

So the bonehead simple rdiff-backup command to "pull" backups for /etc/ looks like this:
```
# rdiff-backup  --exclude-special-files   hadar-backups::/etc/    /Backups/hadar/etc/
```

The backup684 userid on 199.101.32.163 has a uid of 0, it is root-equiv.  It only allows connections from my backup server for that account.  The root -to- backup684@199.101.32.163 ssh-keys were exchanged already.  Passwords aren't allowed to that account.

All ssh, scp, sftp, rsync, and any other ssh or rsync-based tools will honor that config file.  No need to remember ports usernames or IPs/funky hostnames for about 20 yrs.   Want to use different ports or different accounts for different reasons?  Add more  "host" stanzas.  The "host" is just the alias you want to use.  You'll never need to hunt for ports or IPs again.

---

### Post by Holger_Gehrke on 2019-08-10
The posts in the rdiff-backup mailing-list I linked to earlier give two ways to do it: either set your ssh client to always connect to this server on a specific port or pass rdiff-backup a new schema for constructing the ssh command.

Holger

---

### Post by Skaperen on 2019-08-10
i use 4 different ports, one for root, one for sudo users, and the third for other users.  oh, wait, that's only 3.  the fourth is for guest users.  i have not figured out how to configure ssh to choose by destination user.

---

### Post by TheFu on 2019-08-11
> **Skaperen said:**
> i use 4 different ports, one for root, one for sudo users, and the third for other users.  oh, wait, that's only 3.  the fourth is for guest users.  i have not figured out how to configure ssh to choose by destination user.

Multiple stanzas in the ~/.ssh/config file, each with a different alias that has different ports listed.  I'm confused as to why you'll have different ports based on user and not based on forced program by the ssh authorized_hosts key?  Perhaps I'm missing something?

Explicitly:```

host hadar-backups
  user backup684
  hostname 199.101.32.163
  port 61200
host hadar-general
  hostname 199.101.32.163
  port 61201

host hadar-amz
  hostname 199.101.32.163
  port 61202

host icarus-backups
  user backup855
  hostname icarus.example.com
  port 60022

host steves
   hostname any-long.aws-east.amazon.com
```
That all goes into a single file.  Only the **host** parts need to be unique.  user is optional.  port is optional. If the hostname isn't provided then the host will be attempted.  Hostname can be DNS or IP.  We can add specific keyfiles to each stanza as well or any valid option that is documented in the ssh_config file manpage.

If you are using non-standard ports at all, you should be using this config file.  The file makes documenting all ssh connections built-in and we don't need to keep track of them in our heads or scripts, beyond the "host" entry.


I really hope everyone here is using **ssh-copy-id** and **ssh-keygen -t ed25519** to create more secure keys and copy those public keys to other systems without pain.

---

### Post by Skaperen on 2019-08-13
the different ports are a form of security compartmentalization (c18n).  each is a different configuration.  each is restricted in various ways i can't do on a common port.  for example, 3 of them do not allow root access.  and the one that does is limited to the two hosts that pull backups.

---

### Post by TheFu on 2019-08-13
> **Skaperen said:**
> the different ports are a form of security compartmentalization (c18n).  each is a different configuration.  each is restricted in various ways i can't do on a common port.  for example, 3 of them do not allow root access.  and the one that does is limited to the two hosts that pull backups.

sshd_config can do that using the **match user** or/and **match address**, but whatever works for you is great.  Having the firewall control port access never hurts too.  Most long-time daemons support tcp-wrappers too.

---

### Post by Skaperen on 2019-08-14
i could use a different config file under purposeful userids, such as one intended to be doing backups.  it is only going to login as a specific user on the remote.  but i might need to test a variety of user based things from a generic user.

is the "user" directive in the config file the local user running ssh or the remote user the connection is to login as?  i would need for it to be the latter.

---

