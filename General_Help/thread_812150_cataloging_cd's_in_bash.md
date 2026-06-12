---
title: "cataloging cd's in bash"
date: 2008-05-29
forum: General Help
---

### Post by kaiju on 2008-05-29
i just scraped together a little shell script for indexing my optical disks, based on this article: [http://www.freesoftwaremagazine.com/columns/indexing_offline_cd_rom_archives](http://www.freesoftwaremagazine.com/columns/indexing_offline_cd_rom_archives)

```

DRIVE="/media/dvdrw"
INDDIR="$HOME/DISKINDEX"
USAGE="usage: diskindex [disk_id]"
DISKID="$@"
if [ "$#" -ne 1 ]; then
  echo -e $USAGE
elif [ -f "$INDDIR/$DISKID.files" ]; then
  echo "index file already exists for $DISKID."
else
  PADDSK=`echo $DRIVE | sed "s/\//\[\/\]/g"`
  eject -t $DRIVE
  clear
  echo "indexing $DISKID..."
  sleep 15
  mount $DRIVE
  find $DRIVE | sed s/"$PADDSK"/"$DISKID"/g > $INDDIR/$DISKID.files
  eject $DRIVE
  echo "done."
fi

```

even though searching with grep will display filenames anyway, i thought it'd be good to replace inside the index files the cdrom path (as it's not useful information anyway) with the name of the indexed disk - this way the file will give a passable representation of the directory tree, too.
and here comes the first oddity: i came up with the PADDSK variable because i couldn't figure out any other way to escape the "/"-s in the stream.

another problem is that i had to use sleep in order to get mount to wait for the drive to spin up. if i could somehow make mount automatically check whether the drive is ready, that would be much better.

and while the process is working, it would be nice to be able to display something more dynamic than that plain "indexing $DISKID..." message.


so that's all i've got til now, any ideas are very welcome :)

[and i'm sorry if this is the wrong place for this post, but i couldn't find anything more appropriate]

---

### Post by kaiju on 2008-06-20
present state of the script - with add, remove, list and basic search functions, mostly solved disk mounting and ejecting, as a bash function (mainly as a note to self, as it seems no one will ever read this).

```
diskid()#disk indexing and searching utility
{
DRIVE="/media/dvdrw"
INDDIR="$HOME/DISKINDEX"
USAGE="Usage:\tdiskid [searchword]\n\tdiskid -a|d [disk_id]\n\tdiskid -l"
if [ "$#" -eq 2 ]
then 
  DISKID="$2"
  if [ "$1" = "-a" ]
  then
    if [ -f "$INDDIR/$DISKID.files" ]
    then
      echo "index file already exists for $DISKID."
    else
      PADDSK=`echo $DRIVE | sed "s/\//\[\/\]/g"`
      echo "------------------------------------"
      echo -n "mounting disk"
      eject -t $DRIVE
      while [ -z "`cat /etc/mtab | grep $DRIVE`" ]
      do
        echo -ne "." && mount $DRIVE > /dev/null 2>&1 && sleep 5;
      done
      echo ""
      echo "indexing $DISKID..."
      find $DRIVE | sed s/"$PADDSK"/"$DISKID"/g | sort > $INDDIR/$DISKID.files
      while [ ! -z "`cat /etc/mtab | grep $DRIVE`" ]
      do
        umount $DRIVE && sleep 3 && eject $DRIVE;
      done
      echo "done."
      echo "------------------------------------"
    fi
  elif [ "$1" = "-d" ]
  then
    rm -iv $INDDIR/$DISKID.files
  else
    echo -e $USAGE
  fi
elif [ "$#" -eq 1 ]
then
  if [ "$1" = "-l" ]
  then
    ls -C $INDDIR
  else
    grep -h -i --color $1 $INDDIR/*
  fi
else
  echo -e $USAGE
fi
}
```

---

