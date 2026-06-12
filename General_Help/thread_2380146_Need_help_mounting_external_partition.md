---
title: "Need help mounting external partition"
date: 2017-12-13
forum: General Help
---

### Post by grier-devon on 2017-12-13
Hello,

So the other day I had my home server mother board die. Being the genius that I am I did not back up any of my data. I have pulled the 1TB HDD out of my Ubuntu home server and I have it connected to my laptop via an adapter to my USB drive.  Could someone help me mount the partition so I can copy my data off? I attached a screenshot of my HDD info, please help and thanks.
[ATTACH=CONFIG]277827[/ATTACH]

---

### Post by DuckHook on 2017-12-13
Do you have encryption enabled? That's usually the case for an LVM. Otherwise, I don't know why yours is.

You cannot mount an LVM the usual way.

To do so, I haven't come across any instruction set more succinct or effective than the following: [http://www.linuxwave.info/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://www.linuxwave.info/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

---

### Post by grier-devon on 2017-12-13
First off, your awesome. I don't think I setup encryption on the server and I set this up so long ago I am not sure why I used LVM. So I ran through the guide but I am getting told I need to add this to my fstab. I know where that is but how would I add that to my fstab?

```

devon@MrUbuntu:~$ sudo lvscan  ACTIVE            '/dev/GrierServer-vg/root' [923.19 GiB] inherit  ACTIVE            '/dev/GrierServer-vg/swap_1' [7.84 GiB] inherit
devon@MrUbuntu:~$ sudo mount /dev/GrierServer-vg/rootmount:
 /dev/GrierServer-vg/root: can't find in /etc/fstab.

```

---

### Post by DuckHook on 2017-12-13
Your mount command is wrong/incomplete. First, make sure your /mnt is not being used for any other mount (the directory is empty). Then try:```
sudo mount /dev/GrierServer-vg/root /mnt
```You need a space between the "root" and "/mnt"

---

### Post by grier-devon on 2017-12-13
Awesome, that worked perfectly! I can now access my data! Thank you so much!

---

### Post by DuckHook on 2017-12-13
You're welcome. Glad it all worked out.

As a postscript, you may wish to reconsider using LVM. While it is a great technology and has many good applications, it does tend to complicate things in a typical install when it is not really necessary.

Also, you have probably learned from this to do proper backups from now on, but I am emphasizing this for anyone else who comes across this thread,

Good Luck and Happy Ubuntu-ing!

---

