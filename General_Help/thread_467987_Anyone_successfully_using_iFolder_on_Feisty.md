---
title: "Anyone successfully using iFolder on Feisty?"
date: 2007-06-08
forum: General Help
---

### Post by flar on 2007-06-08
Has anyone gotten iFolder to compile on Feisty?  I've tried numerous versions and none seem to work.  I've also tried installing from RPMs and it wouldn't run.  

Simias (a requirement of iFolder) usually compiles, but iFolder gives various errors.

Anyone successfully using iFolder on Feisty?

---

### Post by flar on 2007-06-08
I managed to build the most recent SVN version, but it wasn't working correctly with my existing simias simpleserver.  Perhaps the newer clients only work with the newer simias server?

I also managed to build version 3.4 of the ifolder client (with a minor hack), but it crashes when run on feisty.

I guess I'll have to start from scratch by building a new server and clients all around.

---

### Post by flar on 2007-06-11
update:

The svn version of the ifolder client that I built did not work properly with the older simias simpleserver or the enterprise ifolder server.  I also built and tested several other versions of the ifolder client without success (usually the client ran but did not work properly).


Finally I found a version of the ifolder client that works on feisty:

iFolder:
```
svn co https://forgesvn1.novell.com/svn/ifolder/branches/ifolder_3_4_sled10sp1
```

Simias:
```
svn co https://forgesvn1.novell.com/svn/simias/branches/ifolder_3_4_sled10sp1
```


Build simias first because it is a dependency for ifolder.  To get ifolder to build, you'll likely have to change two references to TrayIcon to Egg.TrayIcon in src/LinuxClient/application/iFolderApplication.cs

So it is possible to have the iFolder client on Feisty.  This client works with both the simpleserver and the enterprise server.

---

