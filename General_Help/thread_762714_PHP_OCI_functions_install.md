---
title: "PHP OCI functions install"
date: 2008-04-22
forum: General Help
---

### Post by gambrjl on 2008-04-22
I'm having to rebuild a small server here at the office that we use to connect to oracle databases on other servers.

I'm trying to figure out if I need to install just the client libraries or do a full oracle installation for these OCI functions to work?

Most of the instructions I've found assume oracle is already installed on the machine.  I don't have it installed and guess I don't want it unless I absolutely have to have it.

What's the minimum I need just to have the oci functions work in my scripts when the oracle db's are on other machines?

---

### Post by gambrjl on 2008-04-22
Ok.  with a little bit of help from [this thread](http://ubuntuforums.org/showthread.php?t=92528&highlight=oracle+OCI) according to phpinfo() I have the OCI8 installed and enabled.  Now my problem comes in my tnsnames.ora

I setup $TNS_ADMIN to point to the directory where my tnsnames.ora file is located and am still getting this error

Warning: oci_connect() [function.oci-connect]: ORA-12154: TNS:could not resolve the connect identifier specified in

Did i miss something?  The tnsnames file is the same one i copied from my box when I use toad to connect to the databases

**edit:**ok.. I think I might have narrowed down my problem

I'm obviously doing somethign wrong setting the $TNS_ADMIN environment variable.  I tried

```
sudo export $TNS_ADMIN=/path/to/tnsnames.ora
```

but i get errors sudo: export: command not found.  If i issue the same command as a normal user it's not set globally so apache isn't seeing it.

What do I do?

---

