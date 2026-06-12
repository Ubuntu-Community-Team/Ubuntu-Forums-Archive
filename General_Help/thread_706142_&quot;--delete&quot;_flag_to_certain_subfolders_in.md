---
title: "&quot;--delete&quot; flag to certain subfolders in rsync"
date: 2008-02-24
forum: General Help
---

### Post by geo909 on 2008-02-24
Hello everybody.

I am using rsync to make recursive backups of a folder that contains my files.
I just do ```
rsync -a /path/to/myfolder/ /path/to/backupfolder 
```
and everything is OK except one thing:

 I need to flag with "--delete" some certain subfolders of "myfolder".
Is there a way to achieve this? Importing info from a file or something?


Any help would be really appreciated!

---

### Post by rapiscan on 2008-02-24
If I'm not mistaken, you could use --exclude to exclude entire directories.  Then you could make specific rsync rules for those directories that you excluded.  So you would be able to specify --delete only for the directories that you want.  

If you read the man page for rsync, it looks like there are other more elegant ways to do this, but I'm not familiar enough with rsync to offer an example.

---

### Post by SeanTater on 2008-02-24
Rapiscan is correct. 

Suppose your source folder contains folders : a, b, and c.
and you don't want b in the destination, you do:
```
rsync -a --exclude b /path/to/myfolder/ /path/to/backupfolder
```

Be mindful though! Those last slashes make a difference to rsync.

If you keep it that way, your actual destination will be:
```
/path/to/backupfolder/myfolder
```

If you don't want it as a subdirectory, change ```
/path/to/backupfolder
``` to ```
/path/to/backupfolder/
``` so your destination will be:

```
/path/to/backupfolder
```


If you are wondering what --delete does, it's for if you had backed up that folder there before, and the files you had** already deleted in the source **you also want deleted in the backup.

---

### Post by geo909 on 2008-02-24
Thank you for your answers!

Yes, I am familiar with the "/" thing and the '--delete' flag.

> If I'm not mistaken, you could use --exclude to exclude entire directories. Then you could make specific rsync rules for those directories that you excluded. So you would be able to specify --delete only for the directories that you want.

It seems that a script would do the job just fine.

rsync the first time excluding the subfolders and then rsync again the previously excluded subfolders, but with the "--delete" flag added to them.

The thing is that I know nothing about scripts and I couldn't write one.
Could you please tell me how a script that tells ubuntu to run several rsyncs would look like?

Also, if anyone is familiar with another more elegant way, please say so!
Thanks again.

---

### Post by rapiscan on 2008-02-24
Check out this link:
[http://www.freeos.com/guides/lsst/ch02sec01.html](http://www.freeos.com/guides/lsst/ch02sec01.html)

It's actually rather straight forward.  You just create a text file containing the appropriate shell commands, give it the correct permissions, then run it.

---

### Post by geo909 on 2008-02-24
Hmm..
Anybody knows a way I could do that without using a script?

---

### Post by geo909 on 2008-02-25
bump

---

### Post by rapiscan on 2008-02-25
Ok, I read through the man page and I think I've figured out how to do this.  I highly recommend going through and reading in detail about the things that I describe here.  Also note that I don't have time to make a complete working example, so you'll have to play around and test it to get it working (but I'm confident this is your answer).

First, you need to learn about the --filter option.  

```
--filter=&#8217;: /.rsync-filter&#8217;
```

"That rule tells rsync to scan for the file .rsync-filter in all directories from the root down through the parent directory of the transfer  prior to the start of the normal directory scan of the file in the directories that are sent as a part of the transfer. "

So this is perfect, you want to be able to specify certain rules on a per-directory basis.  You can use this option and put in your rule.  This is the format of the rule that you will put in the .rsync-filter file:

```
protect, P specifies a pattern for protecting files from deletion.
```

There are more rules that you can read about in the FILER RULES section of the man page.  So you'll want to set your filter, then create your .rsync-filter files in the directories that you want to protect.  Pretty straight forward, but one important thing to note:

> PER-DIRECTORY RULES AND DELETE
       Without  a  delete  option,  per-directory rules are only relevant on the sending side, so you can feel free to exclude the merge files themselves
       without affecting the transfer.  To make this easy, the &#8217;e&#8217; modifier adds this exclude for you, as seen in these two equivalent commands:

              rsync -av --filter=&#8217;: .excl&#8217; --exclude=.excl host:src/dir /dest
              rsync -av --filter=&#8217;:e .excl&#8217; host:src/dir /dest

       However, if you want to do a delete on the receiving side AND you want some files to be excluded from being deleted, you&#8217;ll need to be  sure  that
       the  receiving  side  knows  what  files  to  exclude.   The  easiest  way  is  to  include  the per-directory merge files in the transfer and use
       --delete-after, because this ensures that the receiving side gets all the same exclude rules as the sending side before it tries  to  delete  any&#8208;
       thing:

              rsync -avF --delete-after host:src/dir /dest


In short, you want to be sure to use --delete-after, otherwise your files might get deleted before your extra rules are read.

Hope this helps.

---

### Post by geo909 on 2008-02-26
Hello again,
thanks a lot of your answer, from a quick look I gave,it seems it works..

As soon as I test it myself (I'm really out of time now) I will write what happened in details..
Thanks a lot, again!

---

