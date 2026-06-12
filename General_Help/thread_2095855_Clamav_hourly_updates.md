---
title: "Clamav hourly updates"
date: 2012-12-18
forum: General Help
---

### Post by TheHippy on 2012-12-18
Hi Guys,

I'm running ubuntu server, I have just installed ClamAV and would like to scan the web directory /var/www/* hourly, but i would like to scan only the files created/modified within the hour..

How would i set up ClamAV to do that? scan web directories modified files hourly

---

### Post by dino99 on 2012-12-18
set clamav-daemon into a cronjob

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by TheHippy on 2012-12-18
Hi dino99 thanks for your reply

sorry for the misleading topic, i actually want to scan files every hour, but only scan files which are modified within that hour

---

### Post by SeijiSensei on 2012-12-18
You could a command that uses the "find" command, but why bother?  ClamAV is pretty quick.  Unless you have thousands of files in /var/www it should scan the whole directory in a just a few seconds.  Have you tried installing ClamAV and running "clamscan /var/www"?  What kind of performance do you see?

You can restrict it to particular types of files with commands like "clamscan /var/www/*.exe" or "clamscan /var/www/*.zip".

Just curious, but why would you let anyone post executable files to /var/www?  That's a big security hole, and not one you can fix just by running hourly scans.  If you want to let people post files, put them into a quarantine directory outside the web directories, then run a script periodically that scans each file with clamscan and moves clean ones into /var/www. Another alternative is to write a PHP script that handles the uploading task and scans each file as it is received.  I'd also add some code to send you an email if someone submits an infected file.

---

### Post by TheHippy on 2012-12-18
> **SeijiSensei said:**
> You could a command that uses the "find" command, but why bother?  ClamAV is pretty quick.  Unless you have thousands of files in /var/www it should scan the whole directory in a just a few seconds.  Have you tried installing ClamAV and running "clamscan /var/www"?  What kind of performance do you see?

You can restrict it to particular types of files with commands like "clamscan /var/www/*.exe" or "clamscan /var/www/*.zip".

Just curious, but why would you let anyone post executable files to /var/www?  That's a big security hole, and not one you can fix just by running hourly scans.  If you want to let people post files, put them into a quarantine directory outside the web directories, then run a script periodically that scans each file with clamscan and moves clean ones into /var/www. Another alternative is to write a PHP script that handles the uploading task and scans each file as it is received.  I'd also add some code to send you an email if someone submits an infected file.

Thanks for your advice - I am happy that what I develop is secure & there's no way i'd allow executable files to be uploaded unless there was a reason for it.. but we have a client who is requesting some space on one of our servers, and if we grant it i cannot guarantee that what he puts up there will be secure, and so i wanted to have something running which will notify me & purge anything bad. I.e if he writes a upload facility that someone exploits etc.

At the moment: 
> 
root@:/var/www# find . -type f | wc -l
56253


I will do what you said - let it scan and see how quickly it goes through them.

Ok that was quick!
> 
----------- SCAN SUMMARY -----------
Known viruses: 1395503
Engine version: 0.97.6
Scanned directories: 6921
Scanned files: 56170
Infected files: 0
Data scanned: 1415.58 MB
Data read: 2081.22 MB (ratio 0.68:1)
Time: 171.586 sec (2 m 51 s)


I guess it might as well just do that.

Thanks for your help!

just for reference, could you tell me how would i apply a find to the clamscan?

---

### Post by SeijiSensei on 2012-12-18
I find "find" to be a difficult command, but you can use things like the -ctime and -mtime switches to identify files changed within a particular period.  There's a way to pipe the list to another process like clamscan.  I suggest studying the man page for find.

---

### Post by TheHippy on 2012-12-19
SeijiSensei, thanks a lot for your direction.

This morning i have done the following:

Modified two files, then done

> find . -mmin -60 -type f -print0 | xargs -0 -r clamscan


> 
----------- SCAN SUMMARY -----------
Known viruses: 1400628
Engine version: 0.97.6
Scanned directories: 0
Scanned files: 2
Infected files: 0
Data scanned: 0.01 MB
Data read: 0.00 MB (ratio 2.00:1)
Time: 2.966 sec (0 m 2 s)


Works a treat! 

I ended up using -mmin as it appears to be specifically for grabbing files modified between now and -x minutes ago.

---

### Post by TheHippy on 2012-12-19
So i added it into a file like this

> 
find /var/www/ -mmin -60 -type f -print0 | xargs -0 -r clamscan | mail -s "xxx.xxx.xxx.xxx (SVR5) Scan Results for `date +%T` - `date +%D`" [email]me@myemail.com[/email]

named it hourlyscan

and added it to crontab -e 

> 
0 *  *   *   *     /home/www/mycron/hourlyscan


but it doesnt appear to be running?

Could you please point me in the right direction again

---

### Post by SeijiSensei on 2012-12-20
Did you start the script with a "hash-bang"?

```

#!/bin/bash

[stuff]


```

Is the script marked executable? Is it in root's crontab (/var/spool/cron/root)?  If it is in /etc/crontab, you need to include the username like this:

```
1 * * * * root /path/to/your/script
```

---

### Post by TheHippy on 2012-12-21
i didn't add the hash bang!

I kept getting an error when i added root to the script like in your example
> /bin/sh: root: command not found

So i took it out and it works perfectly now.

Thanks a lot for your help SeijiSensei!

---

### Post by SeijiSensei on 2012-12-22
That last example is a sample entry in the file /etc/crontab.  That is a global crontab that runs with root privileges.  Unlike the crontabs created with the "crontab -e" command and stored in /var/spool/cron, /etc/crontab entries have an additional field to identify the username under which the scheduled job is to be run.

Sounds like everything is working for you now, though.  Congratulations!

---

