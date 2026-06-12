---
title: "crond - how to start it up"
date: 2007-05-14
forum: General Help
---

### Post by Lutherian on 2007-05-14
Hi all.

I'm going nowhere fast with something that I thought would be easy.
Basically, when I run a test crontab nothing happens.
eg.
30 20 * * * sudo wget -t0 -c -P/home/userx -i /home/userx/downloads.txt

So I checked the docs and presumed that crond wasn't loaded, so I typed

/sbin/service crond start.

the response is "command not found" 
although cron -e does bring up the editor.

now there is another old problem that's raised it's ugly head to bite me on the backside (again)

You'll notice that the execution command requires the "sudo" command.
One of my first post was around how to use the sudo command in scripts and in this case as part of crontab.
Is there anyway I can include the password on the command line / script? 
Yea I know it's not good practice but I don't know of any alternative at present.

Anyway thanks for taking time to read this, much appreciated.

---

### Post by heimo on 2007-05-14
Just a quick tip: Search visudo and sudoers

---

### Post by psusi on 2007-05-14
Crond is already running unless your system is messed up.  The problem is with sudo.  It's not going to be able to read your password.  For that matter, why on earth do you think you need to run wget with root access?

---

### Post by Lutherian on 2007-05-14
Yup excellent Question psui. The directory that I'm downloading to is on a remote computer linked via smb. 
The computers drive is mounted as a local directory at my "main" PC. Because I'm a noob (or maybe just plain dumb LOL) I worked out how to have read-write access to the remote drive, but only as root, so far...I struggled in the beginning getting to grips with fstab smb chmod etc...

---

### Post by psusi on 2007-05-14
You need to specify the uid=xxx mount option to make the files owned by another user than root.

---

