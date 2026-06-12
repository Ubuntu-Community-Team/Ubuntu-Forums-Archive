---
title: "FTP client/NCFTPput"
date: 2012-11-24
forum: General Help
---

### Post by techningeer on 2012-11-24
Hey y'all,
Been awhile since I posted on here. At any rate I am using Ubuntu 10.04 (still) and am needing to upload a large file to a FTP server. I have free bandwidth from midnight to 5AM every day, but don't want to stay up that late to start the FTP. I have heard of Ncftpput, but have not found a good guide to using it, and the manpage isn't clear either. Could someone give me a clear example? Also was wondering if there is a GUI that can handle scheduling FTP transfers. Thanks in advance!
--Keagan

---

### Post by dcstar on 2012-11-25
> **techningeer said:**
> Hey y'all,
Been awhile since I posted on here. At any rate I am using Ubuntu 10.04 (still) and am needing to upload a large file to a FTP server. I have free bandwidth from midnight to 5AM every day, but don't want to stay up that late to start the FTP. I have heard of Ncftpput, but have not found a good guide to using it, and the manpage isn't clear either. Could someone give me a clear example? Also was wondering if there is a GUI that can handle scheduling FTP transfers. Thanks in advance!
--Keagan

Just use standard FTP with a command script like people have been using for 20+ years.

Get it working and then put it in a CRON job.

---

### Post by andrew.46 on 2012-11-25
Or the lazy man's cron, work out the time from starting the command until your free time and:

```
sleep 6h && ftp blah blah
```

Not very sophisticated, but ok for a one off job :)

---

### Post by techningeer on 2012-11-26
```
 ncftpput -u *<username>* -p *password* <remote server> <remote directory>

```

Then I used at to schedule it. Some people don't like passing the password over the command line to the program and so you can use ncftpput's option to read from a config file. In my case I have free bandwidth from midnight to 5AM. So I used at to schedule it:

```
at 1AM tomorrow
```

hit return, then at the **at>** prompt:

```
ncftpput -u *<username>* -p *password* <remote server> <remote directory>
```

Hit CTRL+D then you're done.

To check it out:

```
atq
```

That's how I did it after finding instructions for NcFTP on Unix...

---

