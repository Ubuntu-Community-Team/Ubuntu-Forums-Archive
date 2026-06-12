---
title: "Change temp file location for firefox?"
date: 2007-05-16
forum: General Help
---

### Post by Pausanias on 2007-05-16
Very simple question with a nontrivial answer. I have already spent a long time researching this and have come up empty-handed.

When I am using firefox and view a pdf file, I have two options. Either open it with evince (which saves it to /tmp first), or save it somewhere else on the Disk.

How do I get it to save it somewhere else AND open it with evince??

This involves changing the temp file download location from /tmp to something else. But nowhere do I see a pref for this. Note that this location is **NOT** the same as the "download directory," which applies only to saved (and not opened) files.

One solution is to write a script that does a cp /tmp/$1 ~/Desktop/PDFs and then runs evince. Anyone got a way to do it entirely in firefox?

---

### Post by Tautoa on 2007-05-17
Will Firefox store such files in the cache as well? If so, you could change the location of the cache?
You can do this by opening Firefox, typing "about:config" into the addess bar (without quotation marks), adding a string called  "browser.cache.disk.parent_directory" (without quotes), and setting the value to whatever path you want the files to be stored in.

---

### Post by Pausanias on 2007-05-19
No, cache will eventually be deleted when you run out of space. The idea is to keep a copy of everything I read so that it will be indexed by tracker and never deleted.

Here is my solution... called fireopen. Using this as a helper application under firefox will cause the file (no matter what kind of file it is... doesn't have to be PDF) to be also stored in ~/Desktop/Downloads. It checks to make sure it avoids duplicating a file (hence no identical letter-1.pdf, letter-2.pdf are stored whenever you open the same file multiple times).

Post a reply to this thread if you would like more detailed instruction on how to use it.

gnome-open only works in GNOME obviously; not sure what the KDE replacement is.

```

#!/bin/sh
gnome-open $1
froot=`echo $1 | sed "s/-[0-9,A-z]*//g" | sed "s/\/tmp\///g"`
diff $1 ~/Desktop/Downloads/$froot &> /dev/null
result=$?
if [ $result = 2 ]; then
  cp $1 ~/Desktop/Downloads/$froot
elif [ $result = 1 ]; then
  datestr=`date +-%F-%T`
  outf=`echo $froot | sed "s/\.[0-9,A-z]*/$datestr&/g"`
  cp $1 ~/Desktop/Downloads/$outf
fi

```

---

