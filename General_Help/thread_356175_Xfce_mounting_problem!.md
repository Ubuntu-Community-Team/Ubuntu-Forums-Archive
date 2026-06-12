---
title: "Xfce mounting problem!"
date: 2007-02-08
forum: General Help
---

### Post by cmulax on 2007-02-08
I just got xubuntu 6.10 up because I wanted to try out xfce, but I am having mounting issues.
I have a gnome ubuntu on sda while xubuntu is on sdb, so of course the first time I get on xubuntu I mount sda to /mnt/ so as to backup information and such.  HOWEVER whenever I restart, /mnt is empty and I have to remount the drive (also my background disappears since its from sda and I did not copy it over)

Is there a way to keep drives mounted? /is this a problem with my xfce only (searches have not come up with anything) or does this need configuration?

---

### Post by dan_kent on 2007-02-08
You need to create a folder to mount to;

sudo mkdir /mnt/ubuntu
 
Then you'll going to need to add an entry to your /etc/fstab
something like this

/dev/sda      /mnt/ubuntu               ext3    defaults,errors=remount-ro 0       1

---

