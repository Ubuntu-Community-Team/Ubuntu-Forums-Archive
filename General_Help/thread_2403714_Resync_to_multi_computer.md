---
title: "Resync to multi computer"
date: 2018-10-15
forum: General Help
---

### Post by RobGoss on 2018-10-15
Hi everyone I was hoping someone can help me with this problem I have

I want to be able to sync all my photos 
And files  to multi computers.  I know there are a few ways to do this but I've never tries it. What is the easiest way to accomplish this any advice 

Thanks so much

---

### Post by edadasiewicz on 2018-10-15
I have set up public/private keys locally to use ssh.  I then use the following script to pull from my server onto either another desktop or laptop.

```

#!/usr/bin/env bash

function usagexit() {
   printf "Usage: %s: [-d]\n" ${0##*/}
   printf "  -d: dry run\n"
   exit $1
} >&2

RSYNC="rsync -avzz -e ssh --info=STATS0,FLIST0 --delete"

while getopts 'd' OPTION
do
   case $OPTION in
   d) RSYNC=$RSYNC" --dry-run"
      ;;
   ?) usagexit 1
      ;;
   esac
done
shift $(($OPTIND - 1))

case $# in
0) ;;
*) usagexit 2
   ;;
esac

$RSYNC spike:/spare/music /spare
$RSYNC spike:/spare/pics /spare

```

I use a pull from the server rather than a push from the server since the other machines are not always active.  My actual script has a lot more $RSYNC lines and be aware of the --delete option which is why I added a dry-run.

---

### Post by Dennis N on 2018-10-15
_Low tech method_:

For my group of computers, I collect the files to be distributed on a large flash drive from all the computers (since each machine may have some files the others don't), then plug the flash drive into each computer to update them so they each get all files collected. 

Useful commands:

**cp -n** will add files that don't already exist to the flash drive.
**cp -u** will add both newer versions of files and/or non-existent files to the flash drive.

Same commands can be used to transfer from the flash drive collector to each computer. Each computer might have prepared commands stored in a script to handle the transfer if you do it regularly.

**rysnc** will also work if you know how.

---

### Post by RobGoss on 2018-10-15
Thank you both for the help. I've heard rysnc works well I would like to learn how to use it. I want to save a few files and pictures to more then one machine

---

### Post by #&amp;thj^% on 2018-10-15
I myself use Unison: [http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)
> Unison is a file-synchronization tool for OSX, Unix, and Windows. It allows two replicas of a collection of files and directories to be stored on different hosts (or different disks on the same host), modified separately, and then brought up to date by propagating the changes in each replica to the other.

 this is run manually, but is very fast, reliable and effective. Requires both machines being synchronized to be on at the same. It has a nice user interface to allow you to deal with the almost inevitable conflicts, and tracks and propagates deletions correctly. The graphical app/package is called unison-gtk.

As you have stated there are few choices that I consider personal choices so I'll leave you with a few more to hash over.

Worth looking at:

OwnCloud: [https://owncloud.org/](https://owncloud.org/)

SparkleShare: [http://www.sparkleshare.org/](http://www.sparkleshare.org/)

Seafile: [https://www.seafile.com/en/home/](https://www.seafile.com/en/home/) 

Osync: [http://www.netpower.fr/osync](http://www.netpower.fr/osync)

PowerFolder; [https://sourceforge.net/projects/powerfolder-/](https://sourceforge.net/projects/powerfolder-/)

Rsync: [https://rsync.samba.org/](https://rsync.samba.org/)
Rsync fast and effective and been around for decades, however it doesn't keep a history so you have to choose a direction to decide whether a file is new or deleted. Graphical tools are available like "grsync">> "I" also like this one.

Lsyncd: [https://github.com/axkibe/lsyncd](https://github.com/axkibe/lsyncd)

I recommend not syncing the entire home folder, but instead picking specific folders to sync such as Documents/, Pictures/ etc. This will avoid the pain of being forced to deal with the speed / performance / disk space issues of automatically synchronizing   everything. It also avoids having to maintain exclusion lists.
If you want rsync with a GUI then try  "grsync"

---

### Post by sudodus on 2018-10-15
> **1fallen said:**
> I myself use Unison: [http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)


I use Unison too and it works well for me.

Edit:

Unison does two way syncing, which can be quite useful.

When one-way syncing is enough, rsync is a very good alternative, that I often use too, first a dry run

```
sudo rsync -Havn source/ target
```

then the real copying after removing the option **n**.

---

### Post by RobGoss on 2018-10-16
Thanks so much for the helpful information I will take a look at the links posted

---

