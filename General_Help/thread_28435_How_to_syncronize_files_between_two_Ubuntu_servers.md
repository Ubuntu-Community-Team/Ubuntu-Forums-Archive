---
title: "How to syncronize files between two Ubuntu servers"
date: 2005-04-20
forum: General Help
---

### Post by zeldeamipro on 2005-04-20
Hi,

I'm installing two ubuntu web servers, I will make load balancing with Linux-Ha or Linux Virtual Server, the database replication will be make with mysql replication, but I don't know how to syncronize the files I will store in htdocs folder, because I need that all the changes I make in this folder need to be the same in the other server.

Please, help me, because I have been searching and I don't find anything.

Thanks for all

---

### Post by localzuk on 2005-04-20
Take a look at 'rsync'. There is a tutorial of sorts at:

[http://sunsite.dk/info/guides/rsync/rsync-mirroring.html](http://sunsite.dk/info/guides/rsync/rsync-mirroring.html)

Also have a look at 'man rsync'.

---

### Post by speedman on 2005-04-20
localzuk has you pointed in the right direction.  rsync with ssh keys is pretty easy to setup.  Once you have your ssh keys generated and in place on both ends you can use rsync as per the following example to sync a directory and it' contents from one system to another:

rsync -az --rsh="ssh -l root" --recursive --delete xxx.xxx.xxx.xxx:"/path/on/remote/system" /path/on/local/system

Replace xxx.xxx.xxx.xxx with the remote system's IP address.


Regards,

SM

---

### Post by zeldeamipro on 2005-04-20
Thanks for all, it's just I need, I will put an "at" for sync the directory each hour, because there isn't any for sync in real time, or yes?

---

### Post by Alexander Kirillov on 2005-04-20
Another option is unison. I like it much better than rsync...
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

---

