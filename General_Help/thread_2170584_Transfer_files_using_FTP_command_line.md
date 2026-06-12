---
title: "Transfer files using FTP command line"
date: 2013-08-26
forum: General Help
---

### Post by alfirdaous on 2013-08-26
Good day to you

I am looking if possible to transfer files using FTP command line options like:

+ If the file exists on the remote machine and similar (same size), FTP will not transfer the file
+Transfer all files in a specific folder "AAAA" except files likes: file1.php, file2.asp, file3.mp4, folder2...

Thanks in advance

---

### Post by Lars Noodén on 2013-08-27
You might look at a [rsync](https://help.ubuntu.com/community/rsync) instead.  It will only transfer the components that have actually changed.  Further, it does the transfer over SSH so it is secure to use unlike FTP.  The community documentation for rsync will help, but be sure to at least skim the manual page.  The manual page is the ultimate reference as to what it can and can't do.

---

### Post by Crusty Old Fart on 2013-08-27
> **Lars Noodén said:**
> ...it does the transfer over SSH so it is secure to use unlike FTP...

Secure ftp:
```

man sftp

```

---

### Post by Crusty Old Fart on 2013-08-27
> **alfirdaous said:**
> Good day to you

I am looking if possible to transfer files using FTP command line options like:

+ If the file exists on the remote machine and similar (same size), FTP will not transfer the file
+Transfer all files in a specific folder "AAAA" except files likes: file1.php, file2.asp, file3.mp4, folder2...

Thanks in advance
I use SFTP instead of FTP to transfer files in a secure manner.

I don't know this for certain, but I don't think you're going to find FTP or SFTP command line options that will do what you want. The same might be true of rsync -- again. I'm not completely certain.

You might have to manually invoke the transfer command a few times, with different options to get the job done.

On the other hand, if this job is one that you will be doing many times in the future, you might consider writing a shell script to do it.

Good luck,

Crusty

---

### Post by Lars Noodén on 2013-08-27
> **Crusty Old Fart said:**
> The same might be true of rsync -- again. I'm not completely certain.

Try it and be sure. ;)

rsync transfers files and directories just fine.  It can also [include or exclude](http://manpages.ubuntu.com/manpages/raring/en/man1/rsync.1.html) files or directories.  I use it all the time for that.  It is also secure because it now uses ssh by default.  That also means that keys can be set up so that transfers can  be automated.

---

### Post by Crusty Old Fart on 2013-08-27
> **Lars Noodén said:**
> Try it and be sure. ;) ...
Thanks, Lars. I've stayed away from rsync because I read on a different thread that if you're not really careful with it, you can lose a lot of data. Use of a different program was recommended instead. I don't recall what the recommendation was. Perhaps the person who experienced a data loss using rsync was a little too sloppy with it.

Most of the file transfer I do has been happening automatically with custom scripts running as cron jobs that I wrote years ago. Since then I really haven't had the need for anything else.

However, considering your positive recommendation, I'll play around with it.

Thanks again,

Crusty

---

### Post by Lars Noodén on 2013-08-27
Take similar precautions as you would with [cp](http://manpages.ubuntu.com/manpages/raring/en/man1/cp.1.html) or [scp](http://manpages.ubuntu.com/manpages/raring/en/man1/scp.1.html) and you should be ok.  I find it to be one of the staples of system maintenance whether copying between drives or from machine to machine.

---

### Post by Crusty Old Fart on 2013-08-27
> **Lars Noodén said:**
> Take similar precautions as you would with [cp]("http://manpages.ubuntu.com/manpages/raring/en/man1/cp.1.html") or [scp]("http://manpages.ubuntu.com/manpages/raring/en/man1/scp.1.html") and you should be ok...
Ah...yet another new tool for my box. I'd never known about "scp" until now.

Thank you.

---

### Post by SeijiSensei on 2013-08-27
I've used rsync for years and never lost data.  There is a lot of misinformation about Linux systems floating around on the Internet.  I recommend sticking with vetted documentation like the Ubuntu help documents, the Linode ones in my signature, and, with perhaps more detail than you want, the "man" pages.  Running a command like rsync with the option "--help" also provides a quick overview of options.  I haven't used FTP or SFTP for file transfer tasks in years because rsync is so reliable and easy to set up:

```
rsync -av source target
```

will replicate "source" onto "target".  Future executions of that command send only new files and ones that have changed since the last sync.

---

### Post by Crusty Old Fart on 2013-08-27
Wow! I just finished my second reading of the man page for "rsync", which is much more like a man "chapter" than just a page. In terms of the number of options and complexity, the "find" command takes top spot in my experience, but "rsync" is running a close second. The pattern matching capability comes close to what can be done with regular expressions. However, rsync has its own set of wild cards that shouldn't be confused with those used in regex. Some wild card characters have the same meaning in both, whereas other have completely different meanings in each of them. You can easily end up with unintended consequences if you rely on your knowledge of regex matching if you try to write your rsync matches on the fly without jamming your nose into its man page to make sure you're writing your matching patterns pursuant to rsync's special syntax.

 There are also some dangerous consequences of the --delete option.
Fortunately, the man page warns:
```

This option can be dangerous if used incorrectly!  It is a very good idea to first try a run using the --dry-run option (-n) to see what files are going to be deleted.

```

There are many more comments that could be made regarding this command, but rather than ramble on, I'll skip straight to my bottom line:

Rsync appears to be a very robust command with an extensive set of options, which make it flexible enough to be tailored for just about any copying situation. With such flexibility comes a fair amount of complexity, which leads me to encourage those who are unfamiliar with the command to not only read, but also study, the man page (all of it) before using rsync for the first time. Making use of the --dry-run option is highly recommended as it might save your bacon.

Thanks to Lars and Seiji for sparking my interest.
My apologies to alfirdaous for what may seem like I've hijacked his thread.

Crusty

---

### Post by alfirdaous on 2013-08-28
it is an FTP storage area, can we use rsync?

---

### Post by Lars Noodén on 2013-08-28
[FTP should not be used](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) except for anonymous downloads.  It is insecure and cannot be made secure.  Do they offer regular SSH or SFTP?  It's very common.  If so, then you can probably use rsync.

---

### Post by alfirdaous on 2013-08-28
I have installed backup-manager, and the options are:

```

# Which method to use for uploading archives, you can put 
# multiple methods here.
# Available methods:
# - scp
# - ssh-gpg
# - ftp
# - rsync
# - s3
# - none


```

how can I use rsync instead of FTP?

---

### Post by Lars Noodén on 2013-08-29
You don't need backup-manager.  rsync is already there on your machine.  The only question is if it is also there on the remote machine.  It should be there by default if the remote machine is Linux or BSD (including OS X).  You use it as SeijiSensei pointed out but a more specific example could be like this:

```

rsync -av 192.168.0.101:/home/alfirdaous/ /backups/alfirdaous/ 

```

That will copy from the remote machine to the local machine.  Mind the trailing slashes.  It also assumes that your user name is the same on both machines.

---

