---
title: "Unable to remove files: Cannot read symbolic link / cannot lstat : Not a directory"
date: 2008-02-11
forum: General Help
---

### Post by j.daniel on 2008-02-11
**Hello,**

I just ran into a problem which I have not seen before in my limited linux experience.

I was messing around with KDevelop and after a while I decided I would delete the project directory in order to start fresh. As I tried to remove the contents of the project folder I ran into problems witn a set of directories called things like **conf6702.dir**. In these there is a single link called **conf6702.file**, however here the problem starts.

The files are on an cifs mounted external harddrive with the fstab/mount options "rw,user,noauto,exec,iocharset=utf8". I have no problems accessing/reading/writing any other file on this disc nor creating or deleting symbolic links.

As I 'ls' the conf6702.dir, the output is:
```
ls: cannot read symbolic link conf6702.dir/conf6702.file: Not a directory
total 0
lrwxrwxrwx 1 master master 13 2008-02-11 18:03 conf6702.file
```

The file is written with a red font on a black background.

If I try to 'rm -i' the conf6702.file, I get:
```
rm: remove symbolic link `conf6702.file'? y
rm: cannot remove `conf6702.file': Not a directory
```

Trying 'unlink' on the file gives me:
```
unlink: cannot unlink `conf6702.file': Not a directory
```

...anybody have a clue? :confused:

Cheers!
/ Daniel

---

