---
title: "Synchronizing folders over ftp"
date: 2007-05-26
forum: General Help
---

### Post by takethepain on 2007-05-26
I want to be able to synchronize a folder on my computer with a remote ftp server. I am aware of a few Windows programs that will allow me to do this but despite a google search I am in the dark on how to acheive this with Ubuntu! Any suggestions?

---

### Post by mitch.c on 2007-05-26
```
wget --mirror ftp://ftp.example.com
```
Running this would mirror the entire remote ftp site into the directory where it is run (a subdirectory called ftp.example.com would be created) and could be run from cron.

---

### Post by nami on 2007-12-08
what if sometimes the local files are newer that the files on the remote server?  in that case the remote server should be updated instead of the local folder.  what if the remote server is more uptodate than the local files, in this case, the local files should be updated.

finally, what if some of the remote files are more uptodate than the local files, and some of the local files are more uptodate than the remote files, the local and remote files should be updated accordingly.

how can i do this with ubuntu via ftp?

---

### Post by HermanAB on 2007-12-08
Look at lftp.  It has many more features than other FTP clients.

Cheers,

Herman

---

### Post by morningboat on 2007-12-09
> **nami said:**
> what if sometimes the local files are newer that the files on the remote server?  in that case the remote server should be updated instead of the local folder.  what if the remote server is more uptodate than the local files, in this case, the local files should be updated.

finally, what if some of the remote files are more uptodate than the local files, and some of the local files are more uptodate than the remote files, the local and remote files should be updated accordingly.

how can i do this with ubuntu via ftp?

You can have a look at [CrossFTP Pro]("http://www.gnomefiles.org/app.php/CrossFTP_Client"), which supports bi-directional synchronization and mirroring for FTP, as well as the preview of synchronization result. Hope this helps to solve your problem.

---

### Post by nami on 2007-12-09
i can't seem to find any instructions on how to install iftp.  crossftp is good but i would rather not pay for ftp software.

so basically, i am looking for free software which allows me to synchronize my local folder with my remote folder using ftp.

---

### Post by nami on 2007-12-09
oh Lftp.....

i've been searching for iftp........

i cant seem to find any syncing options for lftp.  help.

---

### Post by fragos on 2007-12-09
I recommend you look at "Unison".  It runs on both Windows and Linux and handles incremental synchronization well.  You can change files on either of both ends.  If it gets confused it will ask you to pick between the two files.  I use it all the time with NFS to sync my Ubuntu laptop and Desktop.  In Ubuntu you'd need to use the Shared folders setup and mount the remote on the master host.

---

### Post by themoebius on 2008-01-10
Yeah, I have the same problem as you, mate. Specifically for the purposes of web development syncing. And the problem is especially difficult if there is more than one deveper working on the project, we sometimes need to merge the files. We can't use something like cvs or rsync because we don't always have control over the server so we can't install new software server-side. Everything has to be done through FTP.

In windows or Mac, dreamweaver does this acceptably, but not exceptionally. It looks at the modified dates of all files and can detect of there are changes in the remote version as well as local, in which case they need to be merged. Unfortunately, it doesn't do the merging for you by taking a diff, you'll have to use external software for that.

I also need an equivilent for linux (I've found it hard to replace much of the software I rely on in Windows). Let me know if you find anything that does the job.

---

### Post by nami on 2008-01-10
I found the equivalent, infact I had it installed for ages and didn't realise it.  The answer for me was aptana.  it has ftp synchronisation builtin and that is what I use for web development. :D

---

