---
title: "Run Automatic Scripts for Backup"
date: 2008-07-09
forum: General Help
---

### Post by strange_cathect on 2008-07-09
I have a separate hard drive that I use rsync to do a full backup of my /home partition. However, sometimes I forget or get busy and it doesn't get done.

I want to make a script that will do a full backup of my /home partition that will be started when I select a shut-down.

How would I go about doing this? 

Thanks in advance.

---

### Post by apswartz on 2008-07-09
[NOTE: This requires a change to a system directory, please be careful.]

If you are the only user on your computer you may want to create a file

/etc/rc0.d/S00backup

and put your backup commands there. The /etc/rc0.d/ directory contains scripts that are executed when you shut down the computer.

That filename is spelled... Capital-S, Zero, Zero, backup

---

### Post by strange_cathect on 2008-07-09
Thanks for your reply.

Are there any references for how to construct a script out there? I don't have any experience with this.

Thanks!

---

### Post by apswartz on 2008-07-09
Here is an example of a simple backup script...
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-2.html#ss2.2](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-2.html#ss2.2)

Notice it is part of a larger howto on Bash scripting. Personally, I find it quite addicting!  ;-)

---

### Post by rraj.be on 2008-07-09
there is a  backup utility known as sbackup, it is very easy to setup. It does a full backup first and then only backups files that have been changed. You can set the interval on when it does a full backup and how often it just backs up changed files. Sbackup is in the repositories and you can use synaptic or Add/Remove Programs to install it.

```
sudo apt-get install sbackup
```

I think this is much handy than using some scripts.

---

### Post by strange_cathect on 2008-07-10
Thanks, fellas.

---

### Post by callagga on 2008-07-13
> **rraj.be said:**
> there is a  backup utility known as sbackup, it is very easy to setup.

How mature is sbackup in relation to the ones below I was starting to look at do you know?  

* [http://rsnapshot.org/]("http://rsnapshot.org/")

* [HOWTO: Backup nightly via rsync]("http://ubuntuforums.org/showthread.php?t=639979")

Thanks

---

