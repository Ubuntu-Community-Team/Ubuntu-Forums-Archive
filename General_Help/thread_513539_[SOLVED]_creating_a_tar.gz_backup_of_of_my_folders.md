---
title: "[SOLVED] creating a tar.gz backup of of my folders?"
date: 2007-07-30
forum: General Help
---

### Post by xl_cheese on 2007-07-30
Is there a quick and dirty way to back everything up?  Say I have to reinstall the OS again I can just extract my tar.gz to the root and presto everything is back the way it was.

Seems like I should be able to do this, but I'm not sure how.

---

### Post by dougfractal on 2007-07-30
google "tar example"
from  [http://www.cs.duke.edu/~ola/courses/programming/tar.html](http://www.cs.duke.edu/~ola/courses/programming/tar.html) 
>    tar cvzf foo.tgz cps100
will tar the directory cps100 (and its files/subdirectories) into a tar file named foo.tgz.

To see a tar file's table of contents use:
  tar tzf foo.tgz

To extract the contents of a tar file use:
   tar xvzf foo.tgz

also see:
man tar    # tar manual
tar --help    # help

---

### Post by CrucifiedEgo on 2007-07-30
The only problem with your plan (and i know this from personal experience) is that eventually tar will try to include your backup file, which will continue to grow infinitely.  You'll want to make sure that tar outputs to another device to avoid this.

An alternative is just to backup certain directories.  Usually, i just take backups of /home and /etc and call it a day.  Anything that would take a lot of work for me to recreate is in those two directories.

</j>

---

### Post by scooper on 2007-07-30
In case it might help, I have written a Python script I call "larch" which I've used for a couple of years that can back up files, directories, and create gzip or bzip2 archives to .larch subdirectories.  Just place the script in your path and from the parent of whatever you want to back up use this command to create a timestamped tarball of "mydirectory" (tar.gz file) in a .larch hidden subdirectory.  

[Download larch]("http://wijjo.com/file_download/11")

```
larch -z mydirectory
```

Here's the help displayed by running it without a path.

```
larch [OPTIONS] PATH ...

  OPTIONS
    -c,--compare    compare archive and current directory (interactive)
    -d,--delete     delete original files and directories after archiving
    -h,--help       display this help
    -j,--bzip2      bzip2 compress (and tar if a directory)
    -u,--unarchive  unarchive - restore an archive (interactive)
    -s,--source     exclude object files (*.o, etc.) from source trees
    -z,--gzip       gzip compress (and tar if a directory)

  The --source option applies only to directories, and only when creating a
  tarball with either the gzip or bzip2 compression options.

  The compression, source and delete options have no effect with unarchive.

  Archives are stored in .larch subdirectories wherever the larch command is run.
```

If you have "pv" installed (sudo apt-get install pv) you'll get a progress report of megabytes processed.  Let me know if you use it and have questions or suggestions.  It's the first time I've released it to the public, but I've used it for quite a while myself.

Note that unarchiving and comparing will only work with tarballs, not straight copies of files or directories.  It will refuse to do anything, but shouldn't cause a problem.

I've found it handy, because I only have to specify the target file and the archive type option (optional) and it figures out how to build the appropriate tar, cp or mv command lines.

Enjoy,
Steve

---

### Post by xl_cheese on 2007-07-30
I dug this up.  Exactly what I was thinking of.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

