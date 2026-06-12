---
title: "No partitions with Gparted"
date: 2006-11-12
forum: General Help
---

### Post by JMO707 on 2006-11-12
I was using, extensively, the Gparted LiveCD to resize some partitons. Lastly, I extract some free space from my primary partiton to make a NTFS one. It worked, only that I give it too little space, so now I got to expand it a little bit.
The problem is that, in the LiveCD and in Ubuntu, I see this:

[[IMG]http://img387.imageshack.us/img387/7018/pantallazohf7.th.png[/IMG]](http://img387.imageshack.us/my.php?image=pantallazohf7.png)

Whats the problem?

Have I broke something?

---

### Post by smoker on 2006-11-12
hi, did you click the commit icon at the top of the screen when you did your changes on the partition window? gparted wont actually do the changes till this is done, in english version it is a 'green tick'

it looks as if the picture you posted is showing one large unformatted partition!

hope this helps

---

### Post by JMO707 on 2006-11-12
Yes, I did it!

Thats why Im surprised. Everything works fine, even Grub or the system monitor are fine.

:???:

---

### Post by smoker on 2006-11-12
maybe the ubuntu gparted is damaged, you could maybe try uninstall and reinstall it.

i remember when i installed (dapper) the partitioner froze a couple of times during setting up partitions, but has been fine ever since.

you could check your partitions with your gparted disk again. maybe someone with more knowledge than me will come along and offer other advice.

---

### Post by JMO707 on 2006-11-12
[[IMG]http://img295.imageshack.us/img295/3935/pantallazo1lp3.th.png[/IMG]](http://img295.imageshack.us/my.php?image=pantallazo1lp3.png)

I tried cfdisk. Basically, it says that it has been a really serious error and that the disk unit cannot be open. 

(Im afraid...)

---

### Post by smoker on 2006-11-13
try downloading a diagnostic from your harddrive manufacturers website and running that to test your harddrive, they are free and generally download an iso to burn to a floppy or cd which you boot from and they run some manufacturers tests, some can repair a harddrive, depending on what fault is found, if any!

at least it will put your mind at ease about your harddrive if it passes:-)

---

