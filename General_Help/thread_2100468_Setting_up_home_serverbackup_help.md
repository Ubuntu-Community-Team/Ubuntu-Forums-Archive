---
title: "Setting up home server/backup help"
date: 2013-01-01
forum: General Help
---

### Post by michaelkayy on 2013-01-01
Hello,

I have two laptop. I've searched online trying to find a way to make my old laptop as a wireless backup. Both laptops are running at least two GiB ram,  240 GB+ Disks, and both are running 32-bit Ubuntu 12.10 OS. 

I was wondering if anyone has set up something similar who want to toss me a bone to help me figure it out? I've seen a lot people saying dropbox(which I do use), google drive, which is fine for small documents and pictures. I want something more core to what I need [Backup laptop A to Laptop B] I've look for something simple. I don't need bells and whistles just honestly a "push/sync" backup.

Though I'm newer to Ubuntu/Linux -- I'm not afraid of running terminal :]

Thank you.

---

### Post by chadk5utc on 2013-01-01
one of many options and worth reading
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by BBQdave on 2013-01-01
How about [vsftpd]("https://security.appspot.com/vsftpd.html") with [filezilla]("http://filezilla-project.org/") as the client :)

I am using an old eMac with tiger - 10.4 as a ftp file server. I have filezilla on my notebook, 12.04.1LTS.

Simple set up on my home network, easy to back up my data.

---

### Post by Cheesehead on 2013-01-01
1) You connect two computers (usually using ssh).

The primary machine needs to be able to locate the backup machine, so that's a bit of fiddling with your router to reserve addresses...or setting up static IPs.

The primary machine needs to be able to log into the backup machine. Preferably using a special account unused by a human, permissions limited to just the job needed.

2) The primary machine, at some interval (or in response to an event), sends the backup data to the backup machine.

Lots of backup solutions in the Software Center. Some require software on both machines, some don't. Some are command-line only, some are graphical.

Some command-line utilities need to be told when to do the backup. The event that triggers a them can vary:
A cron job...every day at the same time(s), 
or an event...like connecting to a specific network,
or a udev rule...like a certain USB drive being plugged in, etc.


Does that help get your creativity working?


For example, I use an Upstart rule that detects home network availability. If I am at home on the LAN, the rdiff-backup application connects using SSH and incrementally backs up my /home directory.

---

### Post by michaelkayy on 2013-01-03
Thank you all for you're help! this is why I love using Ubuntu/Linux products. I actually when with using Crashplan as a *simple* workaround for it.  Slow at first, but uploaded 30 gigabytes within 6 1/2 hours and since has been intuitive with new files of all size rages. 

As I grow around Ubuntu I will look back and give your options a go. Once again thank you!

---

