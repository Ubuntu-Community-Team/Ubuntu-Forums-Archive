---
title: "Copied my home directory (~) to another folder by mistake, can't remove it now"
date: 2008-05-11
forum: General Help
---

### Post by voidstar on 2008-05-11
Hello everyone, I'm after making a silly mistake and I'm not sure how to back it out without deleting my home directory.  

I was installing maven and had downloaded the tar ball to my home directory, I was than copying the tar ball to /usr/local/apache-maven/ but I wrote this command by mistake:

 sudo cp apache-maven-2.0.9-bin.tar.bz2 /usr/local/apache-maven/~

The result of this is my /usr/local/apache-maven/ dir now contains ~, if I attempt to cd into ~ it brings me directly to my home directory so I'm afraid to try and remove it.  I also don't want to leave it incase in the future I'm removing /apache-maven and recursively delete my home directory.

if I try and cd into /usr/local/apache-maven/~ it just brings me to my home directory as well.

Is there any safe way to remove this directory/link?

---

### Post by voidstar on 2008-05-11
Ok I decided to be brave and after backing up my home directory and attempted the mv the file using ./~ this worked fine and left my home directory in tact, I've since delete the offending dir and all is well.

---

### Post by Monicker on 2008-05-11
You can get into it or move it if you put the full path in single quotes:

```
cd '/usr/local/apache-maven/~'

mv '/usr/local/apache-maven/~' /some/dir
```

Or even delete it, if you are sure

```
rm -rf '/usr/local/apache-maven/~'
```

---

