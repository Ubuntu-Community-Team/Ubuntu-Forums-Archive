---
title: "permissions problem and I do not understand how to solve it?"
date: 2019-01-06
forum: General Help
---

### Post by adrian-h on 2019-01-06
I have two computers on my home network but ubuntu 16.04 command line only.
say they are localuser1@ubuntu1 and localuser2@ubuntu2 respectivly

I can ssh from one machine to the other no problems and I can run a command line that copies files from users accounts to the other using scp.

So from localuser1@ubuntu1 I can
```
sshpass -p"password" scp -r /home/localuser1/backups localuser2@ubuntu2:/home/localuser2/

```

And that all works.

But if the directory I wish to copy is in localuser1@ubuntu1:/etc i.e. a root directory and I wish to copy it to localuser2@ubuntu2:/etc     another root directory, how would I accomplish that?  I do not mind passing the passwords as part of a command line, I just can not figure it?

Adrian

---

### Post by CatKiller on 2019-01-06
The user for ssh can't be root. That is as it should be.

Non-root users can't write to /etc. That is also as it should be.

You can copy the files you're interested in to the target machine - anywhere convenient - and then move them to the appropriate place on that machine as you would normally administer it.

You don't have to do everything in one step.

---

### Post by HermanAB on 2019-01-06
To copy a file from one user account to a different user account, you need super user privileges and then after copying, you need to reset the user:group of the files to that of the destination user.

Therefore, you cannot do it with scp.  

Log in with ssh, set user to root, copy the files and finally chown the files.

---

### Post by adrian-h on 2019-01-06
The end game is to do this as part of a cron task, part of automatic backup copying some files from the /etc directory to a backup machine.

I guess I could make a root account for the backup machine and do it from root's crontab, possibly?

@CatKiller  Would I loose links doing that?

If I run a job in /etc/crontab    so effectively root@ubuntu1 having created a root account on ubuntu2 would I then be able to do scp ten?  rsync is a better option I know but one stage at a time.

Adrian

---

### Post by CatKiller on 2019-01-06
What are you trying to achieve? For each scenario I can think of, you wouldn't want to do what you're trying to do.

System files are generally static. 

For backups, you wouldn't write to system files on another machine. You'd just dump them somewhere.

For system preservation or standardisation you'd take an image of the whole system rather than individual files and, again, you wouldn't write that image to the system files of another machine. You'd redeploy from the image.

Small configuration changes that you've made to one machine that you also want to make to another machine are better done by actually making those changes rather than moving files around.

---

### Post by adrian-h on 2019-01-06
@CatKiller  (hope that name is regards to the cat command!)  OK long reply.

I have two HP Thin clients a T5740 and a T5730, they are not identical machines and definitely have different size Flash/HD's

As much as I can for my age I am trying to learn more about Linux rather than just be a graphical user (typically Opensuse).

So I installed ubuntu 16.04 32 bit on both machines, I started out with the T5730 and managed to install a vehicle tracker system on it.  [www.traccar.org](www.traccar.org). This is only for family use.

I was surprised it worked for me, I have then been following instructions to change to a MySQL database, and https:  

Also doing scripts to gzip the MySQL database and copy to the back up machine T5740, which is installed with the same packages.  The idea being as a backup should the other fail I should be able to manually switch over.

I was unsure about https:  I have a certificate from the letsencrypt.org bunch, it was an automatic install with a script file so no real issues for me. but installed on the main machine the T5730, I asked about the same certificate being on the backup machine and was told that I should copy the whole directory /etc/letsencrypt from one machine to the other, the directory changes as new certs are issued checks are done etc.  hence the reason for trying to automate a method of copying it from the main to backup as an eventual cron job.

Very recently I had a response from encrypt engineer saying I could have a second certificate for the same home domain and should not trip the weekly limit, so I have just done that and it works negating the immediate requirement.

The idea is having a project such as this it makes me have to ask and learn more about it, I have a couple of books to read, just got one on MySQL and another on Linux administration, but a lot is still beyond me I am afraid to admit.

But I will plod on and get further up the tree.  Thanks for your answers, just need to figure out why I am not getting notifications of postings from the site.

Cheers

Adrian

---

### Post by CatKiller on 2019-01-06
Thanks for the detailed reply. That makes it clearer. I believe the situation you describe is referred to as failover. 

One way to approach it would be to create a new user that is only able to write to that specific directory on each machine, and then use scp/rsync as that user to transfer the files. That way you aren't exposing root to SSH. 

For the last part, I believe it's one of the forum settings to automatically subscribe to threads you post in. That way you can pick Subscribed Threads from the Quick Links menu at the top.

---

### Post by adrian-h on 2019-01-06
> **CatKiller said:**
> Thanks for the detailed reply. That makes it clearer. I believe the situation you describe is referred to as failover. 

One way to approach it would be to create a new user that is only able to write to that specific directory on each machine, and then use scp/rsync as that user to transfer the files. That way you aren't exposing root to SSH. 

For the last part, I believe it's one of the forum settings to automatically subscribe to threads you post in. That way you can pick Subscribed Threads from the Quick Links menu at the top.

In reverse order, I am subscribed but not getting any emails after the first time you replied.  So just included a filter in my email rules to check if getting blocked as spam?

The new userat is an idea I can try at some point, one thing I have done already that I could have possibly tried is to chown the letsencrypt directory to the localuser i.e. chown localuser:users /etc/letsencrypt   ???

I have don e that with a directory in /opt for the GPS software, but I am also running the service as localuser and not as root, so then any changes to files are kept at the same user:group, where as I believe lLE is root driven.  something to look at some point, permissions is something I really need to understand.

lastly failover and being cheeky here, have you any thoughts on my other post trying to achieve this [https://ubuntuforums.org/showthread.php?t=2409744](https://ubuntuforums.org/showthread.php?t=2409744)

Cheers

Adrian

---

### Post by CatKiller on 2019-01-06
There are standard users and groups, like root or audio. Some software will create new users: Apache creates a user called www-data, I believe, to restrict access. But it's fairly easy to create new users and groups for whatever purpose you can think of, and then use group membership and permissions to have fine-grained control over what they can and can't do.

I've never done server admin, so I can't give specifics. I've only picked up some stuff through osmosis.

---

