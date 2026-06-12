---
title: "CLI for &quot;last access&quot; of packages and app's"
date: 2022-03-23
forum: General Help
---

### Post by wyattwhiteeagle on 2022-03-23
[https://www.gnu.org/software/coreutils/manual/html_node/stat-invocation.html#stat-invocation](https://www.gnu.org/software/coreutils/manual/html_node/stat-invocation.html#stat-invocation)
Using the above manual, I'm trying to formulate a command line that tells me which packages and applications I haven't used for a long time or have never used.

I don't want to use a GUI for this.

The manual say's %x specifies the "last access".
I chose /usr just to see what the terminal would print.

Which files or directories do I need to specify to get the desired output?
What am I missing in the following...

```
wyatt@wyatt-Latitude-E5400:~$ stat -f %x /usr
stat: cannot read file system information for '%x': No such file or directory
  File: "/usr"
    ID: 5836c66ee96d2ea9 Namelen: 255     Type: ext2/ext3
Block size: 4096       Fundamental block size: 4096
Blocks: Total: 239965708  Free: 233157286  Available: 220950246
Inodes: Total: 61022208   Free: 60840095
wyatt@wyatt-Latitude-E5400:~$ stat -f /usr %x
  File: "/usr"
    ID: 5836c66ee96d2ea9 Namelen: 255     Type: ext2/ext3
Block size: 4096       Fundamental block size: 4096
Blocks: Total: 239965708  Free: 233157286  Available: 220950246
Inodes: Total: 61022208   Free: 60840095
stat: cannot read file system information for '%x': No such file or directory
wyatt@wyatt-Latitude-E5400:~$
```

---

### Post by SeijiSensei on 2022-03-23
```
ls -lutr --time-style +%Y-%m-%d /usr/bin | awk '{print $7 "\t" $6}'
```

returns a tab-separated list sorted by access time ("-u") with the dates in a common YYYY-MM-DD format. 

```

dirsplit        2006-11-25
debugapp        2007-10-30
pnm2ppa 2016-08-12
calibrate_ppa   2016-08-12
linux-boot-prober       2017-01-21
syslinux-legacy 2017-04-21
time    2017-04-21

[...]

man     2022-03-23
preconv 2022-03-23
tbl     2022-03-23
nroff   2022-03-23
groff   2022-03-23
less    2022-03-23
troff   2022-03-23
grotty  2022-03-23
[etc.]

```

If you need hours, minutes, and seconds look at the man page for date.

---

### Post by wyattwhiteeagle on 2022-03-23
> **SeijiSensei said:**
> ```
ls -lutr --time-style +%Y-%m-%d /usr/bin | awk '{print $7 "\t" $6}'
```

returns a tab-separated list sorted by access time ("-u") with the dates in a common YYYY-MM-DD format. 

If you need hours, minutes, and seconds look at the man page for date.

I need the date to also include the hour minute and seconds.

I've looked at four different manual and tried each thing to no avail.

Which man page were you refering to?

---

### Post by MAFoElffen on 2022-03-23
> **wyattwhiteeagle said:**
> I need the date to also include the hour minute and seconds.

I've looked at four different manual and tried each thing to no avail.

Which man page were you refering to?
Modified SeijiSeinsi]s response to include Hours:Minutes.Seconds
```

ls -lutr --time-style '+%Y-%m-%d %H:%M.%S' /usr/bin | awk '{print $6 "\t" $7 "\t" $8}'

```
But you know you also should also run this for /usr/sbin, right?
```

ls -lutr --time-style '+%Y-%m-%d %H:%M.%S' /usr/sbin | awk '{print $6 "\t" $7 "\t" $8}'

```

The man (manual) he was referring to was for the Linux utiilty 'ls'... 'man ls'

---

### Post by wyattwhiteeagle on 2022-03-24
Thanks a bunch
Is there a way to show app's and/or packages that I haven't accessed?

---

