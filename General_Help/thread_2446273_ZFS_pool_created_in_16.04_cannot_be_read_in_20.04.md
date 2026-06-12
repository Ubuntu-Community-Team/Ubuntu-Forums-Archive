---
title: "ZFS pool created in 16.04 cannot be read in 20.04"
date: 2020-06-27
forum: General Help
---

### Post by laceiba2 on 2020-06-27
I have a ZFS pool full of data that is functioning nicely on a 16.04 installation of Ubuntu. When I try to import that pool into a 20.04 installation, I get the following error:

```
$ sudo zpool import data

cannot import 'data': pool is formatted using a newer ZFS version
```

"Data" is the name of my pool, btw. To further test this, and determine if something strange had occurred during my years of usage of the main data pool, I created another new pool using different disks that didn't contain anything besides a few text files. Same problem. When I do a modinfo zfs, I get following information:

16.04  –  0.6.5.6-0ubuntu28
20.04  –  0.8.3-1ubuntu12

The ZFS version does not appear to be the problem. My 20.04 installation does not currently have any pools, but when I run this command, this is the output I receive:

```
$ sudo zpool upgrade

This system is currently running ZFS pool version 23.

All pools are formatted using this version.
```

Running a similar command in 16.04 produces less helpful output, probably because I have enabled LZW compression.

```
$ sudo zpool upgrade data

This system supports ZFS pool feature flags.

Pool 'data' already has all supported features enabled.
```

Google does not seem to be able to point me in the right direction. Has anyone here encountered this before? I can always blow the existing pool away and restore from backup, but I would like to avoid that given the amount of work involved. It is decidedly strange that an Ubuntu version that is four years newer should throw an error suggesting that the ZFS pool in 16.04 is using too new of a version. Am I missing something obvious here? Thanks in advance.

---

### Post by kneutron on 2020-06-29
--That is completely bizarre, you would expect it to be the other way around.  If you have new disks of the same size or larger, I'd recommend creating a new pool on 20.04 and migrating your data over since the old drives will be pushing warranty expiration and possible failure anyway

---

