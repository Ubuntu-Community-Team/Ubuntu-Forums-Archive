---
title: "Anacron question"
date: 2013-01-31
forum: General Help
---

### Post by PSBTornado on 2013-01-31
(Meant Ubuntu not LUbuntu)
Hi
 
I have a script called dssedit (Disk space script edit) which I want to run everyday about 20 mins after I boot up. I can run it directly from my command line by typing dssedit. I have added the path in bash.rc so it finds it in /home/myusername/myscripts.
 
I have put an entry in anacrontab that looks like follows
 
1 20 disk_space_script dssedit
 
Should this work? Or do I need to specify the full path to dssedit? I've googled quite a bit and can't quite work it out.

---

### Post by Cheesehead on 2013-01-31
> **PSBTornado said:**
> 
I have a script ... which I want to run everyday about 20 mins after I boot up. I can run it directly from my command line by typing dssedit. I have added the path in bash.rc so it finds it in /home/myusername/myscripts.
 
I have put an entry in anacrontab that looks like follows
 
1 20 disk_space_script dssedit
 
Should this work? Or do I need to specify the full path to dssedit? I've googled quite a bit and can't quite work it out.

1) Use full pathnames. Anacron runs as root, so it doesn't load user .bashrc files. 

2) Child processes like your script will also run as root (not your user), so any file activities will be done as root. Everything in the script needs to use full pathnames (or import an environment). Your user may not have permission to read/write changed files after the anacrontab job runs.

3) Remember to document your custom anacrontab thoroughly so you aren't stuck six months from now when you have forgotten exactly how you did this.

4) Check /var/log/syslog for job failure information. Sometimes it helps, sometimes it doesn't.
 
5) If you're not sure if the crontab/anacrontab is actually working, use a very simple test, like /usr/bin/touch /tmp/testfile.

There may be simpler ways to accomplish the delay, or a more direct trigger for your script caused by a system event. For example, a 'sleep' command at the beginning of the script.

---

### Post by PSBTornado on 2013-01-31
Thanks Cheesehead I will look at that. I had it working on my old setup but forgot to document how I did it before I installed my new Ubuntu update.

---

### Post by PSBTornado on 2013-02-01
Hi Cheesehead. 

I got it working. Thankyou. I put the full pathname in and it worked as I intended. I've saved a backup of my configuration for further reference.

---

