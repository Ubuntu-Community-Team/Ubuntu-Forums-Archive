---
title: "Cron job unable to write to NFS share - command line can ?"
date: 2013-02-13
forum: General Help
---

### Post by mikeyw on 2013-02-13
Hi,

I'm running this basic script to backup to an NFS share however i get permission denied when i try and copy to it

day=`date | cut -c 1-3`
ulimit -f 9186055680
tar -cvf "/confbck/srvc$day".bck /srv/c
tar -cvf "/confbck/homec$day".bck /home/c
cp "/confbck/srvc$day".bck /bck/
cp "/confbck/homec$day".bck /bck/

From the log file

cp: cannot create regular file `/bck/srvcWed.bck': Permission denied
cp: cannot create regular file `/bck/homecWed.bck': Permission denied

However both as sudo and not sudo i can manually copy these files successfully from the command line

Any ideas ?

Tia
M

---

### Post by schragge on 2013-02-13
Just to be sure, you're running this script from /etc/crontab as root, right? What options are set in */etc/exports* on your backup server?

---

### Post by mikeyw on 2013-02-13
> **schragge said:**
> Just to be sure, you're running this script from /etc/crontab as root, right? What options are set in */etc/exports* on your backup server?

I've been using sudo crontab -e to edit root's cron file, is this no longer the correct method ?

I'll try putting an entry in /etc/crontab

---

### Post by mikeyw on 2013-02-13
with the entry in /etc/crontab the cp failed in exactly the same way.

The share is set up as follows 

share -F nfs -o root=xxxx-xxxxxx /bck

---

### Post by schragge on 2013-02-13
I'm not sure, but I think when editing crontab for root it's better to explicitly specify the user (*sudo crontab -eu root*). From [crontab(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/crontab.1.html") manpage:
> 
Note that su(8) can confuse crontab and that if you are running inside of su(8) you should always use the -u option for safety's sake.


---

### Post by schragge on 2013-02-13
> **mikeyw said:**
> 
The share is set up as follows 

share -F nfs -o root=xxxx-xxxxxx /bckOh it's Solaris then I don't know :( . Have near to zero experience with Solaris. Just guessing, try
share -F nfs -o rw,root=xxxx-xxxxxx /bck

---

### Post by mikeyw on 2013-02-13
It's actually HP-UX where the NFS share resides.

As i said before though i can do the cp fine manually so if it was the share options it would surely prevent this.....

For me the issue lies on the Ubuntu server.

---

### Post by Habitual on 2013-02-13
> **schragge said:**
> I'm not sure, but I think when editing crontab for root it's better to explicitly specify the user (*sudo crontab -eu root*). From [crontab(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/crontab.1.html") manpage:

One of the most powerful linux commands there is even has a "disclaimer".:(

---

