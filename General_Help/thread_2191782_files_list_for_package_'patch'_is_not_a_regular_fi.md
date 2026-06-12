---
title: "files list for package 'patch' is not a regular file"
date: 2013-12-04
forum: General Help
---

### Post by be4truth on 2013-12-04
Linux av-projects 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 
x86_64 x86_64 x86_64 GNU/Linux
Ubuntu 14.10

I had a strange boot yesterday with some files little corrupt. I could repair most of it but I can't install and remove software with apt-get or dpkg. I get always this error:

dpkg: unrecoverable fatal error, aborting:
files list for package 'patch' is not a regular file
E: Sub-process /usr/bin/dpkg returned an error code (2)

it complains at the moment upgrading Virtualbox but it applies to any install, upgrade or remove.

Can somebody help me? I have read most of what is online to this error message but could so far not resolve this issue.

I have done already the common things like apt-get update, upgrade, dpkg --configure -a

This is the full output.

root@xxxxxx:~# apt-get upgrade Reading package lists... Done Building dependency tree
Reading state information... Done The following packages will be upgraded: virtualbox-4.2 1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. Need to get 0 B/64.2 MB of archives. After this operation, 828 kB of additional disk space will be used. Do you want to continue [Y/n]? y Preconfiguring packages ... Selecting previously unselected package virtualbox-4.2. dpkg: unrecoverable fatal error, aborting: files list for package 'patch' is not a regular file E: Sub-process /usr/bin/dpkg returned an error code (2)

I tried this one without success:
try -

    Go into the /var/lib/dpkg directory
    Make a backup of the "status" file
    Open the status file as root and find the package that causes the error.
    Delete all the text until the next PACKAGE: declaration in the file.

or you can use terminal to edit the status file as shown below but make a copy of that file before editing -

sudo edit /var/lib/dpkg/status

 I deleted the entries mentioning virtualbox and it looks like it is not installed anymore but when I run an upgrade or remove I get the same error message.  
	
I also tried to do the same with package "patch" but then it complains about package "libpocketsphinx1" and so one.

---

### Post by drmrgd on 2013-12-04
Two questions:

1. You said you did all the common things.  By chance did you try:
```

sudo apt-get clean

```
to purge out any cached packages.  Could there be a broken package mucking up the works?

2.  I found this thread about restoring previous versions of the dpkg status file to the last known working copy.  Have you tried this by chance (see the second answer below)?  

[http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file](http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file)

---

### Post by be4truth on 2013-12-05
I tried apt-get clean - no success
I followed the link above - no success

I notice that in /var/lib/dpkg/info/patch.list only one file is there and it is encrypted. Should this file be encrypted? I have the /home encrypted but not /var/lib....

Could that be a bug ?

---

### Post by be4truth on 2013-12-05
Can somebody help me with the decryption. I have my passphase.

---

### Post by steeldriver on 2013-12-05
For just a single corrupted .list file, it might be easiest to rebuild it manually - if you don't still have the .deb you can download it from [http://packages.ubuntu.com/trusty/amd64/patch/download](http://packages.ubuntu.com/trusty/amd64/patch/download) and then list the contents with

```

dpkg --contents /path/to/downloaded/patch_2.7.1-4_amd64.deb

```

The actual patch.filelist should correspond to those files (minus the 'ls -l' style permissions), with the following tweaks:

[LIST=1]
[*]the leading . and trailing / where present 
[*]the root entry is ./ in the dpkg --contents output but needs to be /. in the *package*.list file 
[/LIST]

I *think* that the following one-liner will do it for you

```

dpkg --contents /path/to/downloaded/patch_2.7.1-4_amd64.deb | awk 'NR==1 {print "/."; next}; {sub("^\.","",$NF); sub("/$","",$NF); print $NF}' > patch.list

```

e.g. on my (i386 box)

```

$ dpkg --contents /var/cache/apt/archives/patch_2.6.1-3_i386.deb | awk 'NR==1 {print "/."; next}; {sub("^\.","",$NF); sub("/$","",$NF); print $NF}' > patch.list
$ diff -s patch.list /var/lib/dpkg/info/patch.list
Files patch.list and /var/lib/dpkg/info/patch.list are identical

```

---

### Post by steeldriver on 2013-12-05
Hmm... maybe l'm overthinking this. If you have the .deb file (either in cache or downloaded) then maybe just installing it with 'dpkg -i' will update the .list file?

---

### Post by be4truth on 2013-12-05
Steeldriver - thanks for the reply. I already fixed it 1/2 hour before you posted but along your suggestion.

I noticed that for about 5 packages the .list file was corrupted. I looked up the files on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and copied the file list entry into a new files I made in /var/lib/dpkg/info and added on the top line ./
Then all worked

---

### Post by steeldriver on 2013-12-05
OK that's good - in fact I posted exactly that solution, but then second-guessed myself and deleted it

The only thing that worries me about the way you did it (and the reason I edited myself) is the list from the packages website only includes the actual files, whereas the /var/lib/dpkg/info version has every path component for each file as well, e.g. for the /usr/share/lintian/overrides/patch file it has

```

./usr/share/
./usr/share/lintian/
./usr/share/lintian/overrides/
./usr/share/lintian/overrides/patch

```

What would worry me about that is suppose you have packageA that contains file /usr/lib/subdir/fileA and packageB that has /usr/lib/subdir/fileB, then if your package list for fileA does not include /usr/lib/subdir then apt-get may attempt to remove it when packageB gets removed. I'd be tempted to re-install each of the packages you fixed ('apt-get install --reinstall' or equivalent) just to be extra safe. But again, maybe I'm over thinking.

---

### Post by drmrgd on 2013-12-05
> **steeldriver said:**
> OK that's good - in fact I posted exactly that solution, but then second-guessed myself and deleted it

The only thing that worries me about the way you did it (and the reason I edited myself) is the list from the packages website only includes the actual files, whereas the /var/lib/dpkg/info version has every path component for each file as well, e.g. for the /usr/share/lintian/overrides/patch file it has

```

./usr/share/
./usr/share/lintian/
./usr/share/lintian/overrides/
./usr/share/lintian/overrides/patch

```

What would worry me about that is suppose you have packageA that contains file /usr/lib/subdir/fileA and packageB that has /usr/lib/subdir/fileB, then if your package list for fileA does not include /usr/lib/subdir then apt-get may attempt to remove it when packageB gets removed. I'd be tempted to re-install each of the packages you fixed ('apt-get install --reinstall' or equivalent) just to be extra safe. But again, maybe I'm over thinking.

I was thinking along those lines too, which was why I was trying to source a old / working copy of the list. Seemed to me that going one by one might end up in a vicious cycle or a domino like cascade of problems. Maybe I too was over thinking?  Hopefully everything is fixed now and you're back in business!

---

### Post by be4truth on 2013-12-06
I reinstalled the 5 packages now (doesn't harm) and indeed now the files should be in good state. Thanks for all the help.

---

