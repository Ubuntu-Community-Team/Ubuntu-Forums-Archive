---
title: "Rsync exclude from root directory"
date: 2016-10-23
forum: General Help
---

### Post by Andrew_Welham on 2016-10-23
Strange one and i'm pretty sure its just a / missing in the right place, but i cant work out the right combination.

If short i'm trying to rsync most of my root file systems excluding specified directories and i just cant get it to work. In my test directory
 rsync -aAXv --exclude-from exclude-list.txt /rsynctest/ /data/rsynctest
with the exclude-list.txt
containing 
- /a/

excludes only the /a/ directory from the /rsynctest directory but only if i add the training / to the source location in the rsync comment i.e 

rsync -aAXv --exclude-from exclude-list.txt /rsynctest /data/rsynctest
does not work

The same is true for the real (not rsync root directory
if i add a directory called a to the root of my file system and type 

rsync -aAXv --exclude-from exclude-list.txt / /data/backup
the /a directory is also copied

Ignore the obvious error with the recursive loop on /data as its a mount point which will be excluded by the one file system option.

so the question is how do i rsync the real / directory excluding the local directory a

Many Thanks

---

### Post by HermanAB on 2016-10-23
The trouble is that it doesn't work like one would assume.  The leading / is not necessarily the root of the file system.

Global rsync filter rules beginning with a leading / are anchored to the root of transfer. Quoting from the "INCLUDE/EXCLUDE PATTERN RULES" section of the man page:

    if the pattern starts with a / then it is anchored to a particular spot in the hierarchy of files, otherwise it is matched against the end of the pathname. This is similar to a leading ^ in regular expressions. Thus "/foo" would match a name of "foo" at either the "root of the transfer" (for a global rule) or in the merge-file's directory (for a per-directory rule).

In your command (rsync ... -arv /home/ben home-ben/), the file /home/ben/foo would be transferred to home-ben/ben/foo. The root of transfer is home-ben and the correct filter path is /ben/foo. Thus,

    to match /home/ben/.ccache you need a filter path of /ben/.ccache
    to match /home/ben/build/ you need a filter path of /ben/build/

A more detailed explanation can be found in the "ANCHORING INCLUDE/EXCLUDE PATTERNS" section of the rsync(1) man page.

Note that simply leaving out the leading / is not necessarily what you want. Quoting again from the same man page section:

    An unqualified "foo" would match a name of "foo" anywhere in the tree because the algorithm is applied recursively from the top down; it behaves as if each path component gets a turn at being the end of the filename. Even the unanchored "sub/foo" would match at any point in the hierarchy where a "foo" was found within a directory named "sub". See the section on ANCHORING INCLUDE/EXCLUDE PATTERNS for a full discussion of how to specify a pattern that matches at the root of the transfer.

Thus a filter pattern of build/ would match a build directory anywhere in /home/ben, even /home/ben/many/sub/directories/build/.

---

### Post by Andrew_Welham on 2016-10-23
did you reply to the wrong thread. I recognise the Ben part from a different thread i was reading , but this is about the root or a file system not a sub directory.

---

### Post by SeijiSensei on 2016-10-23
Use 
```

a/

```
in the exclude list, then run
```

cd /
rsync -av . /path/to/destination

```
Run with "-avn" first to make sure everything goes into the right locations.  You may need a trailing slash in "/path/to/destination/".

Rsync is very picky about slashes; read the man page for details.

---

