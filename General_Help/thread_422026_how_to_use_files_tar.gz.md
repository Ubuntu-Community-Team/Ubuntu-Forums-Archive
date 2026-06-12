---
title: "how to use files tar.gz"
date: 2007-04-24
forum: General Help
---

### Post by kystorms on 2007-04-24
Where would the documentation for Dapper talk about how to open and use downloaded files, with extensions such as tar.gz and such?

:confused:

---

### Post by dcstar on 2007-04-24
> **kystorms said:**
> Where would the documentation for Dapper talk about how to open and use downloaded files, with extensions such as tar.gz and such?

:confused:

The Nautilus Archive Manager should open these for you, have you tried that?

---

### Post by KyleCardoza on 2007-04-24
> **kystorms said:**
> Where would the documentation for Dapper talk about how to open and use downloaded files, with extensions such as tar.gz and such?

:confused:

This is an easy one, but I can understand how a convert from a non-*nix OS would be stymied.

Tar is an archive format; it takes a bunch of files, and sticks them together into a bundle, usually with the extension ".tar". The program "tar" is used to manage them from the command-line, and the GNOME archive manager knows all about them.

Gzip is a compression format; it takes one file, and compresses it, usually replacing the compressed file with a compressed file of the same name, with the extension ".gz" appended. The programs "gzip" and "gunzip" (really a link to gzip; programs in *nix OSes are smart enough to know under what name they were called) manage them from the command-line, and again, GNOME's archive manager knows all about them.

Between them, they are equivalent to Zip, Rar, or whatever other compressed archive format you normally use.

To extract from a .tar.gz (or .tgz) file, using the command-line the command:

```
tar -xzf myfile.tar.gz
```will do the job. Just double-click on a .tar.gz file to open it in the archive manager.

---

### Post by Ziggy72 on 2007-04-24
You would usually download files of the type you mention because you want to install something. Obviously, Synaptic Package Manager is best for installing most applications, but you may find the following link  [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) very helpful.

---

### Post by RedSquirrel on 2007-04-24
[Installing software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")

For more details about tar:

```
man tar
```or 

[GNU ]("http://www.gnu.org/software/tar/manual/tar.html")[tar]("http://www.gnu.org/software/tar/manual/tar.html")

---

