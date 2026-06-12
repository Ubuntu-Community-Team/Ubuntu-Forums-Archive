---
title: "Need to reset file permissions"
date: 2008-03-19
forum: General Help
---

### Post by JT9161 on 2008-03-19
I've searched all over and I cant resolve it. Somehow my file permissions are very much messed up I have tried to fix it once on my own and that just made it worse I cant login to my account and root gives me "$home/.dmrc can not be loaded". I am simply looking for  a way to reset all file permissions to there default with out having re install.

---

### Post by bodhi.zazen on 2008-03-19
.drmc file permissions, in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown -R user_name /home/user_name

	OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

Where  user_name = your log-in name :p

---

### Post by JT9161 on 2008-03-20
Thanks. I can now login like normal though I had to login as root. But now I have another problem I am unable to use Firefox when ever I try to start it I get this:   

[IMG]http://farm3.static.flickr.com/2394/2347139382_4db3ae095b_o.png[/IMG]

So I checked my filesystem permissions and was not greated by a pretty site. I tried but was unable to change them 

[IMG]http://farm3.static.flickr.com/2064/2347139384_3b86b27cf3_o.png[/IMG]

---

### Post by bodhi.zazen on 2008-03-20
Looks like your file system is mounted read only. This can happen if there are problems mounting the root file system (ie impending hardware failure).

Can you open a terminal and post the output of :

```
ls -lA /home
```

Edit out your user name(s) if you like, but lets look at the ownership / permissions ;)

Also look at the ownership /  permissions of /

---

### Post by JT9161 on 2008-03-20
```
jackson@jackson-laptop:~$ ls -la /home
total 12
drwxrwxrwx  3 jackson jackson 4096 2008-03-10 07:33 .
drwxrwxrwx 21 jackson jackson 4096 2008-03-19 17:47 ..
drwxr-xr-x 33 jackson jackson 4096 2008-03-20 15:49 jackson

```

---

### Post by bodhi.zazen on 2008-03-20
Ownership of /home looks OK, can you check the ownership and permissions on / and /home/jackson ?

just

ls -la /

ls -la ~jackson

you do not need to post the output here, bu I am concerned your ownership and permissions of / are off :

in the output of ls -la /home

. (/home) and .. ( / ) should be owned by root ... and the permissions should not be 777

---

### Post by JT9161 on 2008-03-20
What would the proper permissions be ?

And is this the proper command

```
chmod 123 /
```

---

### Post by bodhi.zazen on 2008-03-20
Most look like this :

> bodhi@VirtualUbuntu:~$ ls -l /

drwxr-xr-x   2 root root  4096 2007-10-16 22:01 bin
drwxr-xr-x   3 root root  4096 2007-10-16 22:04 boot
drwxr-xr-x  10 root root 13440 2008-03-19 01:25 dev
drwxr-xr-x 126 root root 12288 2008-03-20 13:32 etc
drwxr-xr-x   4 root root  4096 2008-02-27 14:57 home

<clip>



But if your permissions are off, best re-install

[http://ubuntuforums.org/showthread.php?t=730384](http://ubuntuforums.org/showthread.php?t=730384)

---

### Post by JT9161 on 2008-04-05
Sorry to dig this up but I have an issue and don't want to start a new topic. I re-installed  and copied my  Home folder to a new partition and want to set that as my home folder I know I need to edit my fstab but how? Currently my /home is on '/dev/sda6' and I want it to use the one on '/dev/sda3'  My fstab looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d8173e0d-571c-4901-9cdf-a5ef5f1c30c1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C090E58C90E5896C /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=588c2d87-6c23-4bfe-99c6-508d59f3784b /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=4d3658a2-e7a8-4a0b-8e23-0720633ba4be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by bodhi.zazen on 2008-04-05
If you are wanting to move /home to it's own partition, best follow a how-to:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

