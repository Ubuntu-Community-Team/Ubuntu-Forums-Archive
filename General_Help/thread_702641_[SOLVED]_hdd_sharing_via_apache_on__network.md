---
title: "[SOLVED] hdd sharing via apache on  network"
date: 2008-02-20
forum: General Help
---

### Post by nicho12 on 2008-02-20
hello
I have a computer running ubuntu connected directly to my router.
my problem is I can't figure out how to make the other 3 hard drives / partitions in the ubuntu machine accessible/viewable via apache. 
What I want to do is for users on my home network (via a netgear dsl router) to be able to type in my ubuntu computers ip address in a web browser, and be able to access the files I have on those hard drives.

I installed xampp and its running fine, I can type the computers name/ip address and it will go to the xampp page fine. I can create directories in the htdocs/xampp folder and browse to them.
I tried creating a link in the htdocs/xampp folder to one of the folders in one of my hdds, but it's not viewable via apache.
I thought this might be a permissions problem so I changed the permissions to 777, but either that didn't work, or the permissions didn't change because it's still not viewable.
I have been wracking my brains over this for ages now and I still can't figure out a solution.

I have got these hdds shared over the network, and its working fine, but I still can't get them accessible via apache.

My apologies if I'm being stupid here, I'm not that used to linux yet and haven't tried anything like this before.
I am using vnc and putty to control the ubuntu computer from this machine

Many thanks for your time

edit:
so you know, the file format of the hard drives is NTFS

---

### Post by freelinuxhelp on 2008-02-20
I'm not familiar with XAMP, but for a standard Apache installation, look at the apache conf file and allow follow-symlinks

---

### Post by nicho12 on 2008-02-20
Thanks for your reply.
you can close the thread now as I figured it out.
I replaced xampp with apache2, remounted the hard drives in /home/...
I added alias's in teh config folder and specified they have indexing and followsymlinks so then you avoid the 'you do not have permission' thing if you have no index file.

hope it helps someone else
N

---

### Post by freelinuxhelp on 2008-02-21
I'm not sure, but I believe you have to mark the thread as Solved. under thread tools.

---

