---
title: "cmd line help"
date: 2017-03-22
forum: General Help
---

### Post by ex_isp on 2017-03-22
Greetings all!

I have a website that is 30GB/9000+pages/8 or 9 directories deep.  Using commercial hosting that has ssh avail.
The issue is I use cmd line so infrequently I need a little help.

Directory structure is typical...    web page is in /public and I have created a directory called  /backup

Filezilla fails miserably trying to download this site as it is (a) so big and (b) so many directories deep.
Multiple attempts have gotten root files and one or two folders deep.

Can someone build me a cmd line to create a tar.gz file of /public and deposit it into /backup?

Any help here is highly appreciated!

Ex

---

### Post by SeijiSensei on 2017-03-22
Is the /backup directory on the same machine or not?  When you talk about "downloading" the site with Filezilla, it sounds like you're trying to back it up off site.

Either way, you should use the rsync utility.  If you're downloading the files from a remote server, use:
```

cd /backup
sudo rsync -av server:/public .

```
This will create a /backup/public folder with the contents of the site.

Rsync will use ssh to create the connection.  I recommend setting up keys for the local root user and transferring that key to the server.  Because Ubuntu doesn't permit root logins by default, that's probably the easiest solution.  If root has a password on the remote server, you'll be prompted to enter that when you run rsync.

If the directories are both on the same machine, you can use:
```

cd /backup
sudo rsync -av /public .

```
to accomplish the same task.

It takes a bit of doing to get the proper directory references in rsync.  Whether to include a trailing slash makes a difference.  The first time you try this, use "-avn" as the parameters which will show you which files will be copied but not actually do the transfer.  If the results look wrong, try adding or removing the trailing slash on the source directory reference.  For more details, see the [rsync man page]("https://linux.die.net/man/1/rsync").

---

### Post by #&amp;thj^% on 2017-03-22
See if you can make this work to your needs: [http://osxdaily.com/2012/04/05/create-tar-gzip/](http://osxdaily.com/2012/04/05/create-tar-gzip/)

Nin'jed by SeijiSensei :)

---

### Post by ex_isp on 2017-03-22
> **SeijiSensei said:**
> Is the /backup directory on the same machine or not?  When you talk about "downloading" the site with Filezilla, it sounds like you're trying to back it up off site.

Either way, you should use the rsync utility.  If you're downloading the files from a remote server, use:
```

cd /backup
sudo rsync -av server:/public .

```
This will create a /backup/public folder with the contents of the site.

Rsync will use ssh to create the connection.  I recommend setting up keys for the local root user and transferring that key to the server.  Because Ubuntu doesn't permit root logins by default, that's probably the easiest solution.  If root has a password on the remote server, you'll be prompted to enter that when you run rsync.

If the directories are both on the same machine, you can use:
```

cd /backup
sudo rsync -av /public .

```
to accomplish the same task.

It takes a bit of doing to get the proper directory references in rsync.  Whether to include a trailing slash makes a difference.  The first time you try this, use "-avn" as the parameters which will show you which files will be copied but not actually do the transfer.  If the results look wrong, try adding or removing the trailing slash on the source directory reference.  For more details, see the [rsync man page]("https://linux.die.net/man/1/rsync").

Yes, trying to get offsite backup.    /public and /backup are both on the server at aplus.net.  Need to compress entire /public folder into one file.
Using ssh (putty) into remote server.  goal is to .tar.gz the entire /public directory into ... /backup/site.tar.gz    That will give me one big file that filezilla 'should' be able to download across the interwebz to my home office.   To get an idea of this site I need to save and it's complexity.

---

### Post by SeijiSensei on 2017-03-22
To create the tar archive use
```

cd /public
tar czvpf /backup/site.tar.gz .

```
But I'd just use rsync to make a complete copy of the site on the local client.  Why bother with a tar file that you're only going to unzip anyway once it's transferred?  

You can use "rsync -avz" to apply gzip compression to an rsync transfer.  That can help if you're on a slow connection.

---

