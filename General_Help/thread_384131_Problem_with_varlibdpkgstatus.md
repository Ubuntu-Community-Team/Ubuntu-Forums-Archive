---
title: "Problem with /var/lib/dpkg/status"
date: 2007-03-14
forum: General Help
---

### Post by sfoo on 2007-03-14
Hi,

I've got an Ubuntu installation running under VMWare Server. It was ticking along fine then one minute I wanted to see if a package was installed and what I got was:

$ aptitude show gcc
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.


Hrmm.. so I look into /var/lib/dpkg/status and the first few lines are:

7c92d1b792e7a3ec7eca0741e2533c0e  sbin/mdadm
46f98d92e5af8e2ee78888386bee7bc5  sbin/mdrun
d2642f66c52d62dab9e16b13a4b3c562  usr/share/mdadm/mkconf
b5b4f25e9376626be9f50fc5e878c226  usr/share/bug/mdadm/script

The rest of the file is similar... Now, that's obviously not a proper status file... 
So, I look at the status-old file and that looks like part of my dhclient.eth0.leases file! 

 Is it possible to recover from this? If I blat the file or copy a valid file from somewhere else, will that help or make it worse?

I'm wondering if vmware has anything to do with this. The host system is otherwise fine and I've been having trouble with iso's under vmware mysteriously changing their md5sums. 

Thanks,

Shawn

---

