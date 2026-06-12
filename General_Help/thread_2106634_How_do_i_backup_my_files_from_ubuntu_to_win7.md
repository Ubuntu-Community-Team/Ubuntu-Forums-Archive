---
title: "How do i backup my files from ubuntu to win7"
date: 2013-01-19
forum: General Help
---

### Post by Raafat1991 on 2013-01-19
Hi guys...

i want to sync files (about 2 TR)  from ubuntu to win7 but until now i did't find anything about that 

so

any an idea ?


thank you.......

---

### Post by MumbleFysh on 2013-01-19
There are a few ways to go about this. A Networked-like Drive, or a Dual Boot system with proper mounting of drives/directories.

The former is for mainly two separate boxes, or someone who likes to host their media on another drive which is then accessed by all devices. [Samba]("https://www.samba.org/") is a great choice for this, there is a tutorial to configure Ubuntu and Windows by using Samba [here]("http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html").

---

### Post by ibjsb4 on 2013-01-20
Another possibility would be a [data partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en") and use something like [rsync]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=rsync&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F") ([grsync]("http://www.opbyte.it/grsync/")).

---

### Post by Mark Phelps on 2013-01-20
Problem with just copying your files into a Win7 partition is that Windows doesn't understand Linux filesystem permissions.  So basically, once you copy them, they basically become "windows" files -- inherit the default permissions associated with your Win7 filesystem.

If all you want to do is backup your files to another partition, I would recommend that you create an Ext4 partition on your drive and backup the files there.

If all you want is a restorable backup of your Ubuntu setup, I would recommend that you use Clonezilla and image off your Ubuntu setup to another drive.

I used clonezilla to image off Ubuntu setups to an NTFS-formatted partition -- but that worked OK because it just treats the backup as one big file.  When it gets restored to the Linux filesystem, the original file permissions are restored, as well.

---

### Post by Raafat1991 on 2013-01-22
> **ibjsb4 said:**
> Another possibility would be a [data partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en") and use something like [rsync]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=rsync&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F") ([grsync]("http://www.opbyte.it/grsync/")).

Does grsync sync my files from ubuntu to windows7 ?

---

### Post by Raafat1991 on 2013-01-22
What i want execatly is a tool for synchronizing my files from a ubuntu machine to a windows7 machine .

thank you everyone...

---

### Post by Mark Phelps on 2013-01-22
> **Raafat1991 said:**
> What i want execatly is a tool for synchronizing my files from a ubuntu machine to a windows7 machine .

thank you everyone...


Then read on below ...

[http://www.myokyawhtun.com/downloads/how-to-sync-files-between-windows-and-ubuntu.html]("http://www.myokyawhtun.com/downloads/how-to-sync-files-between-windows-and-ubuntu.html")

---

### Post by Raafat1991 on 2013-01-23
> **Mark Phelps said:**
> Then read on below ...

[http://www.myokyawhtun.com/downloads/how-to-sync-files-between-windows-and-ubuntu.html](http://www.myokyawhtun.com/downloads/how-to-sync-files-between-windows-and-ubuntu.html)

But i want to sync my files on a local network from a ubuntu machine to another (windows7) on the same network also ubuntu on requires $3000 (I'm a poor man :o) , about dropbox i will see (i have sent a message to them)  ...

---

### Post by SeijiSensei on 2013-01-23
You cannot create a filesystem snapshot directly on a Windows machine because, as noted before, the NTFS filesystem Windows uses has no understanding of things like Unix permissions.

What you can do is create a compressed "tar ball" of your system and copy that to the Windows machine.  I'd split this task into parts, though, since most of the files will remain identical from day to day.  This is just an overview of how the process might work:

1)  Export a directory off the Windows machine and mount it with [cifs]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").  Let's call the mount point /media/backup.

2)  Create a tarball for the largely static directories like this:

```

cd /
sudo tar cjpf /media/backup/static.tar.bz2 bin boot etc lib root sbin usr

```

3)  Create another tarball of /home and /var which contain files that change often:

```

sudo tar cjpf /media/backup/$(date +%Y%m%d).tar.bz2 home var

```

That will create an archive named 20130123.tar.bz2.  You can rotate these as needed.

I've used the bzip2 compression engine as it provides the smallest images at a slight cost in speed.

You can extract a single file with

```
tar xjf /media/backup/20130123.tar.bz2 path/to/file.ext
```

If you use "cjvpf" when creating the tarballs, you'll get a listing of the files stored in the archive.

---

### Post by Raafat1991 on 2013-01-25
> **SeijiSensei said:**
> You cannot create a filesystem snapshot directly on a Windows machine because, as noted before, the NTFS filesystem Windows uses has no understanding of things like Unix permissions.

What you can do is create a compressed "tar ball" of your system and copy that to the Windows machine.  I'd split this task into parts, though, since most of the files will remain identical from day to day.  This is just an overview of how the process might work:

1)  Export a directory off the Windows machine and mount it with [cifs]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").  Let's call the mount point /media/backup.

2)  Create a tarball for the largely static directories like this:

```

cd /
sudo tar cjpf /media/backup/static.tar.bz2 bin boot etc lib root sbin usr

```3)  Create another tarball of /home and /var which contain files that change often:

```

sudo tar cjpf /media/backup/$(date +%Y%m%d).tar.bz2 home var

```That will create an archive named 20130123.tar.bz2.  You can rotate these as needed.

I've used the bzip2 compression engine as it provides the smallest images at a slight cost in speed.

You can extract a single file with

```
tar xjf /media/backup/20130123.tar.bz2 path/to/file.ext
```If you use "cjvpf" when creating the tarballs, you'll get a listing of the files stored in the archive.


I will try what you said and i will reply...thank you .

---

### Post by LewisTM on 2013-01-25
There is an alternative to dumping a Linux fs onto a Windows drive with tarballs or loopfiles. You can use **Metastore** which is in the repos.

Metastore saves extra Linux file metadata (owner, group, permissions, extended attributes) in a separate file. You can thus store the metadata of a file tree as a regular file on a Windows environment (FAT, NTFS, Samba). The same tool can be used to reapply the metadata once you have restored the backup onto a Linux fs.

Say you want to backup /home/foo
Just cd to the directory and save the metadata. You shouldn't need sudo unless you don't have read access to some files
```
cd /home/foo
metastore -s
```
The metadata will be stored in /home/foo/.metadata
You can now backup /home/foo with rsync or your favorite backup software. You can ignore any setting regarding saving attributes, you just need to backup the files.
To re-apply the metadata, restore your files into /home/foo and execute
```
metastore -a
```
Remember to run 'metastore -s' before every sync.
It can even be useful in the context of tar. I use user extended attributes (xattr) a lot and Ubuntu's version of tar doesn't store them. Putting the .metadata file in the tarball solves that limitation.

Cheers!

---

### Post by Raafat1991 on 2013-01-27
Hi guys...which of your ways when is backing up my files will backup( next time ) only what changed ?

that is important because i have (as i told you) about 2 TR that will spend my network's bandwidth

thank you guys thank you .

---

### Post by LewisTM on 2013-01-27
My "way" doesn't mention how to efficiently backup your files, that's up to you. It only gives you a method for preserving Linux filesystem metadata.

I would suggest **rsync** which is the preferred tool for backing up files on Linux. It has several graphical incarnations like grsync or Luckybackup. Rsync will compare files and only transfer new or modified ones. If the file has been modified, it will only send the modified part which can save a lot of transfer time for large files or slow connections.

You can learn about rsync with 
```
man  rsync
```
Like I said, you need not worry about preserving permissions and whatnot if you have an up-to-date .metadata file. So no need for -pog parameters. I would start with something like
```
rsync -rtv /source /destination
```
If you just want to sync the source contents without recreating the source directory itself, append a / to make it /source/

---

### Post by SuperFreak on 2013-01-27
grsync might be easier to use as it uses a graphical interface. It is based on rsync and I believe it has the same options including copying  EXT files to NTFS so they can be read by Windows. It is available at [http://www.opbyte.it/grsync/]("http://www.opbyte.it/grsync/")

---

