---
title: "Easy backups in ubuntu"
date: 2007-05-11
forum: General Help
---

### Post by miekg on 2007-05-11
**Disclaimer: I'm the main author of rdup**

**Making backups with rdup**
So you want to make backups, but all the programs you find are to complicated and even then don't allow you to make compressed, encrypted and remote backups? Then you might want to try rdup.
The goal of rdup is to provide some simple utilities to make a backup. It's designed to be run from CRON. Also it is not an imaging backup program; its main concern is backing up personal data.

In this short guide I will tell what you need to do to get a backup running:
[LIST]
[*] Installing rdup
[*] Configuration
[*] Compressed backup
[*] Remote backup
[*] Extra features
[*] More information
[/LIST]

I will not detail how rdup works or how the backup is done in a technical sense, see rdup's documentation for that. This guide is just to get people going with making backups.

** Installation**
Install the following packages:
[LIST]
[*]libglib2.0-0
[*]ibfile-copy-recursive-perl
[/LIST]

Download rdup from [http://www.miek.nl/projects/rdup/deb/rdup_0.3.9-1_i386.deb](http://www.miek.nl/projects/rdup/deb/rdup_0.3.9-1_i386.deb)
And install with with:

```
$ dpkg -i rdup_0.3.9-1_i386.deb
```

or use gdebi.

** Configuration**
This is easy part. What do you want to backup and where do you want to store the backup? Its best to keep backups on a different partition or better yet on a different harddisk altogether.

**Making a backup**

```
$ rdup-simple ~ /backup/$HOSTNAME
```

Will store you homedirectory in /backup/$HOSTNAME/YYYYMM/DD. So for today and my host this will be: **/backup/elektron/200705/11**

Each day will be stored in a new directory. This is done a space efficient matter (hardlinks). Because the files are not wrapped up in something like a tar file you can easily restore file from your backup.

** Compressed backup**
Simply add the '-z' flag to rdup-simple:

```
$ rdup-simple -z ~ /backup/$HOSTNAME
```

Will gzip you backup.

** Encrypted backup**
Simply add the '-k key' flag to rdup-simple:

```
$ echo "my key" > key
$ rdup-simple -k key ~ /backup/$HOSTNAME
```

Will encrypt the backup with the key stored in the file key.

**Remote backup**
Install 'rdup' on the remote host. This must be done because rdup needs some of its utilities to be available on the other system. After you have done that:

```
$ rdup-simple ~ ssh://user@remotehost/backup/$HOSTNAME
```

Will store your homedirectory on 'remotehost' in the directory /backup/$HOSTNAME/YYYYMMDD

The compression and encryption works the same as above.

**Extra features**
You simple want to exclude some directories? Simple create a file '.nobackup' in such directories and rdup will skip them. See the manual pages for details.

** More information**
You can mail questions to [email]rdup@miek.nl[/email] (moderated mailing list) or directly to me [email]miek@miek.nl[/email].
More documentation can be found the manual pages of rdup and on the
website of rdup: [http://miek.nl/projects/rdup](http://miek.nl/projects/rdup)

---

### Post by xfile087 on 2007-07-14
Nice program! I've been simply making a tar archive of my home/system folder, but now I think I may use this program and add it as a nightly cron job.

I'm no expert with Linux so i'm just wondering if I used rdup to backup my / - if I later restored / it would be fully bootable as if i'd used tar instead, right? Just want to be sure that's all.

---

### Post by tlwolf on 2008-06-28
This is pretty much exactly what I was looking for. Just wanted to tell you thanks:)

---

