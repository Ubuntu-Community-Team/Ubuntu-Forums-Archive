---
title: "Is there a problem with the repositories?"
date: 2007-06-17
forum: General Help
---

### Post by nelstomlinson on 2007-06-17
Hello, All,

I just installed Feisty, and I'm trying to install some things I need.  Is there a problem with the Ubuntu servers?  When I try to do an update on the main or U.S. repositories, I get the following errors, consistently since Thursday night.  It is now Saturday night.  

Is there a problem on the server, or do I have something wrong with my sources.list?  I'm new to Ubuntu, but I've used Debian for a few years.

Thanks!

Nels

Errors:
=======================================
tomlinso@desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [3754kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [3754kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Sources
99% [4 Packages bzip2 14399488]                                                         1228kB/s 0s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                                          
  Sub-process bzip2 returned an error code (2)
99% [5 Packages bzip2 14925824]                                                                    
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process bzip2 returned an error code (2)
Fetched 5B in 19s (0B/s)       
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tomlinso@desktop:~$ 
========================================

---

### Post by dreadlord_chris on 2007-06-17
Has it fixed itself yet?
Mine did. Looks like it was just corrupt package info from that repository - I got the same errors last night, but not this morning.

---

### Post by nelstomlinson on 2007-06-18
> **dreadlord_chris said:**
> Has it fixed itself yet?
Mine did. Looks like it was just corrupt package info from that repository - I got the same errors last night, but not this morning.

I'm still getting the same errors, on a number of repositories.  I'm starting to wonder if there is something wrong with my system; maybe a problem with gzip, or with checking the md5sums?

Is there any way to check my system?  I've tried to download a single zip file, and it failed to decompress,  which doesn't look good but isn't quite conclusive.

Nels

---

### Post by dreadlord_chris on 2007-06-18
> **nelstomlinson said:**
> I'm still getting the same errors, on a number of repositories.  I'm starting to wonder if there is something wrong with my system; maybe a problem with gzip, or with checking the md5sums?

Is there any way to check my system?  I've tried to download a single zip file, and it failed to decompress,  which doesn't look good but isn't quite conclusive.

Nels

It's only some of the respositories that are giving you problems, not all - right?
*Sub-process bzip2 returned an error code (2)* <== this tells you that **bzip** (not gzip) was passed a corrupt archive. If there were a problem with gzip on your end - in all likelyhood **all** the repoistory downloads would fail.

Try this:
```

sudo apt-get clean && sudo apt-get check

```
That will clean out your cache and then do some internal checks....

Any errors or diagnostic messages with that? If not, do a:
```

sudo apt-get update

```

---

### Post by nelstomlinson on 2007-06-18
> **dreadlord_chris said:**
> It's only some of the respositories that are giving you problems, not all - right?
No, it's all of them.
> **dreadlord_chris said:**
> 
*Sub-process bzip2 returned an error code (2)* <== this tells you that **bzip** (not gzip) was passed a corrupt archive. If there were a problem with gzip on your end - in all likelyhood **all** the repoistory downloads would fail.

Try this:
```

sudo apt-get clean && sudo apt-get check

```
That will clean out your cache and then do some internal checks....

Any errors or diagnostic messages with that? If not, do a:
```

sudo apt-get update

```

Did the clean and check, which returned no errors or diagnostics, and still getting the same errors from the update.  So, I think that means I have a problem with gzip?  Any suggestions for a fix, short of a new install?

Thanks for the help.

Nels

---

### Post by dreadlord_chris on 2007-06-18
well... that exhausts my ideas...

sorry I couldn't be more help...

---

### Post by nelstomlinson on 2007-06-18
> **dreadlord_chris said:**
> sorry I couldn't be more help...

You've been a big help.  Knowing that the repositories are working for others means the problem is on my machine.  I had been hoping things were screwed up for everyone, which would be great for me: I wouldn't be the one who had to fix it!  Oh, well.

Knowing that someone was having problems with a repository earlier suggests that I might have gotten a bad package to install, which gives a possible explanation for my current problems.  I won't be surprised if a re-install makes it all better.

Thanks,

Nels

---

### Post by nearly_nickless_head on 2007-08-12
i read this in one of the forums
"It seems that if the files are downloaded to an ntfs file system, and then transferred to an ext3 file system, tar/bzip2/gzip are unable to uncompress properly."
i had s similar problem with fat32 ...bzip2 not working on some tarballs...
so do check if ur apt-get is downloading packages to ntfs or fat32...try changing it...(i am not sure how)

---

### Post by teedabu on 2007-09-27
I am having the same problem. After exhausting aptitude and apt-get commands I think I traced the problem to a corrupt file on the ubuntu archive servers.

I downloaded the package listing directly from the archives here

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2)
and
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2)

```
tar -jxvf Packages.bz2

bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors
```

Packages.gz, which is in the same url directory, also is corrupt. 

Can someone verify this?

---

### Post by teedabu on 2007-09-28
Nevermind. My problem was a faulty router.

---

