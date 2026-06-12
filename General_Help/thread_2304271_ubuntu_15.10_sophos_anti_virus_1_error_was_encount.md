---
title: "ubuntu 15.10 sophos anti virus 1 error was encountered."
date: 2015-11-25
forum: General Help
---

### Post by sebastiaan5 on 2015-11-25
specs; ubuntu 15.10 lenovo y50-70 i7 16gb ram gtx 860m

So I've scanned my laptop with sophos antivirus. And I encountered 1 error but I don't know how to fix this.
command:

```
sudo savscan -f /
```

output:

```
Full Scanning

Could not open /var/run/user/1000/gvfs

94467 files scanned in 28 minutes and 6 seconds.
1 error was encountered.
No viruses were discovered.
End of Scan.
```


/home/sebastiaan/sophos-av/bin/savlog output:

```
#! /bin/sh
## Copyright (c) 1989-2013 Sophos Limited. All rights reserved.

DIR_NAME=`dirname "$0"`
BIN_PATH=`cd $DIR_NAME >/dev/null && pwd`
INSTDIR=`dirname "$BIN_PATH"`
EXE=`basename "$0"`
BINARY=$BIN_PATH/_/$EXE

[ -r "$BINARY" ] || [ `id -u` -eq 0 ] || { echo "You must be root to run this program." ; exit 2 ; }

ORIGINAL_PYTHONPATH="${ORIGINAL_PYTHONPATH-${PYTHONPATH}}"
ORIGINAL_LD_LIBRARY_PATH="${ORIGINAL_LD_LIBRARY_PATH-${LD_LIBRARY_PATH}}"
ORIGINAL_PYTHONHOME="${ORIGINAL_PYTHONHOME-${PYTHONHOME}}"
export ORIGINAL_PYTHONPATH
export ORIGINAL_LD_LIBRARY_PATH
export ORIGINAL_PYTHONHOME

PYTHONZIP=`ls $INSTDIR/engine/python*.zip 2>/dev/null`
[ -f "$PYTHONZIP" ] || PYTHONZIP=$INSTDIR/engine/python25.zip
[ -f "$PYTHONZIP" ] || PYTHONZIP=$INSTDIR/engine/python27.zip

PYTHONPATH=$INSTDIR/engine:$INSTDIR/engine/util.zip:$INSTDIR/engine/diagnose.zip:$PYTHONZIP:$INSTDIR/update/cidrep.zip
export PYTHONPATH
LD_LIBRARY_PATH=$INSTDIR/lib:$INSTDIR/lib64:$INSTDIR/lib32
[ -d /lib/nptl ] && LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/lib/nptl
export LD_LIBRARY_PATH
PYTHONHOME=$INSTDIR
export PYTHONHOME
[ -n "$BASH" ] && shopt -s execfail 2>/dev/null
unset LIBPATH
exec "$INSTDIR/engine/python" "$BINARY" "$@" || { echo "Unable to run python" ; exit 1 ; }
```

---

### Post by Ricardo_Velasco on 2015-11-25
Greeting:

Proof trying to give permissions to the file, put it in the terminal :

> sudo su : root password

> sudo nautilus

You enter the location of the file and you click on Properties , you go to the Permissions tab and change your root group your username ..

Then you put in Reading and Writing in the 3 tabs ..

Says if you keep your problem.

This image has to show up to change the permissions of that file location



[IMG]http://i.stack.imgur.com/hgZpP.png[/IMG]

---

