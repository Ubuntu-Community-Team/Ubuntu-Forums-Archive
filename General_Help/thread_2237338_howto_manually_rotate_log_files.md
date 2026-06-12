---
title: "howto manually rotate log files"
date: 2014-08-01
forum: General Help
---

### Post by J_Me on 2014-08-01
I want to manually compress the var/log files, tried using 'sudo /etc/cron.daily/logrotate' but it doesn't work.
Thanks

---

### Post by Lars Noodén on 2014-08-01
That way would only run the regular rotation scheme which would only move or compress the files according to the normal schedule.  If you want to force a rotation, then use [--force](http://manpages.ubuntu.com/manpages/trusty/en/man8/logrotate.8.html)

```
sudo /usr/sbin/logrotate --force /etc/logrotate.conf 

```

However, while that will force rotation, it will only compress those that are scheduled to be compressed.  See /etc/logrotate.d/* for the specifics for individual files.  Some files will have *delaycompress* in their configuration.  Also, forcing rotation will cause some archived logs to fall off the end of the queue and be erased.  Maybe that is not what you want.  

What is your goal with this?

---

### Post by J_Me on 2014-08-01
I appreciate your reply but it went over my head.
What I would like to do is simply delete '/var/log/kern.log' as it's 3.2gigs but I read somewhere that deleting someFile.log or even someFile.log.1 will cause problems, which seems reasonable So my approach was to rotate all log files including '/var/log/kern.log' to '/var/log/kern.log.1' and then to '/var/log/kern.log.2.gz' which could then be deleted.

What I did in brief.
1- used a broken usb dvd drive on a broken dvd.
2- kern.log grew to 3.2gigs.
3- the error is 'kernel: [55005.853560] end_request: I/O error, dev sr1, sector 5479765'

If I come across as blunt/rude please don't take it personally, I'm just fedup.
Thanks

---

### Post by SeijiSensei on 2014-08-01
Use "sudo cat /dev/null > /var/log/kern.log".  It will truncate the file immediately.

You know what the source of the problem is.  Why don't you just remove the bad drive and disk?  Seems like an easy solution to me.

Actually the error seems to apply more to the disk than to the drive.  Have you tried other disks?

---

### Post by J_Me on 2014-08-01
Firstly thanks to both of you for the help.
> You know what the source of the problem is. Why don't you just remove the bad drive and disk? Seems like an easy solution to meI have. I knew the disk was bad from the start and so used the broken dvd drive on it, I didn't want to ware out a good drive on that disk. My mistake was not checking the logfiles.
> Use "sudo cat /dev/null > /var/log/kern.log". It will truncate the file immediately.Thanks for the solution. So I can delete the contents of a logfile without any problem as long as the permissions for that file remain intact things wont break.
Could I ask how you came to know that solution, was it from books or experience. Personally I hate asking people for every single thing that I need to do but the commandline tends to have me stumped. The man pages never seem to give any follow on clues for me to explore. Anyway I suppose the magic search word would have been 'truncate'.
Thanks again

---

### Post by Impavidus on 2014-08-01
/dev/null is a special file/device. If you read it, it shows up as empty. There are several of those special files in /dev. cat reads the file and sends it to standard output, the > redirects the standard output to a file, after truncating it to zero length. So **cat /dev/null >file** truncates the file to zero length. This is all standard command line stuff that you can learn by, for example, reading this post. So that's experience mostly, but it helps if you find some guides on the web.

In fact, the command is not entirely correct. The leading sudo causes cat to run with root permissions, which you don't need, but it doesn't make the output redirect work with root permissions, so you'll get permission denied. What works is```
cat /dev/null | sudo tee /var/log/kern.log
```| sends the standard output of cat to the standard input of tee, tee is a command that reads standard input and writes it to the named file, in this case with root permissions. It also writes it to standard output, but as there is zero output in this case, you won't notice. If you wish, you can suppress the standard output by redirecting it to /dev/null, which I will leave as an exercise.

---

### Post by SeijiSensei on 2014-08-01
> The leading sudo causes cat to run with root permissions, which you don't need, but it doesn't make the output redirect work with root permissions, so you'll get permission denied.

I've used "sudo cat /dev/null > filename", or the equivalent after becoming root on systems that allow it, many times in my life.  It's never been an issue.  I've never had a permissions problem.  I just tested it again to zero out a random file, and it worked as advertised.

---

### Post by SeijiSensei on 2014-08-01
> The leading sudo causes cat to run with root permissions, which you don't need, but it doesn't make the output redirect work with root permissions, so you'll get permission denied.

I've used "sudo cat /dev/null > filename", or the equivalent after becoming root on systems that allow it, many times in my life.  It's never been an issue.  I've never had a permissions problem.  I just tested it again to zero out a random file, and it worked as advertised.

Also he certainly does need root permissions to zero out /var/log/kern.log, which the "syslog" user owns by default.

---

### Post by Impavidus on 2014-08-02
I tried and it didn't work. We must be doing something differently.```
$ ls -l test.txt
-rw-rw-r-- 1 root root 768 aug  2 09:58 test.txt
$ sudo cat /dev/null >test.txt
bash: test.txt: Permission denied
$ ls -l test.txt
-rw-rw-r-- 1 root root 768 aug  2 09:58 test.txt
$ cat /dev/null | sudo tee test.txt
$ ls -l test.txt
-rw-rw-r-- 1 root root 0 aug  2 09:59 test.txt
```

---

### Post by SeijiSensei on 2014-08-02
Ah, I see what is different.  I owned the file I was zeroing out, not root.

Usually I don't encounter these problems because I often run as the root user.  I would certainly do so if I were trying to manipulate the contents of /var/log.

---

### Post by J_Me on 2014-08-02
@Impavidus thanks for the correction, explanation and tee exercise but in future I'll ask for help right away rather than banging my head against the terminal endless times.
Although in the past I was able to hobble together a program that included cat,tee,sed etc which worked on the whole, the thing is it was more trial and error than anything else, took me ages.

@SeijiSensei running 'sudo /bin/bash' first did the trick for me.


Thanks again

---

