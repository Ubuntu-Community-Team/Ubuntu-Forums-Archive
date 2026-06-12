---
title: "move /home to another mountpoint"
date: 2006-11-17
forum: General Help
---

### Post by aparsons on 2006-11-17
I have a 10gb drive that hosts my Ubuntu OS and a 300gb "data" drive that mounts to /data.

I was wondering how I could move /home (10gb drive) to /data/home (300gb drive) to simplify maintainence.  Is it as easy as:

mkdir /data/home
mv /home /data/home
umount /home
rm /home
ln -s /data/home /home

My fstab is as follows:

> proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=fa336400-50d8-496a-81e0-874ec4683b8c /      reiserfs defaults  0 1
# /dev/hda1
UUID=07482e6c-d6db-439b-bbf1-c81f80adfd20 /boot  ext3    defaults  0  2
# /dev/hda2
UUID=7b690535-945e-42ba-8be6-fb250351f561 none   swap    sw  0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

/dev/hde1  /data defaults 0 3


---

### Post by meng on 2006-11-17
That should work, but I would forget about the last command
ln -s (etc)

and just change your fstab, last line:
/dev/hde1 /home defaults 0 3

then reboot.

---

### Post by aparsons on 2006-11-17
Thanks for the feedback.  However, /data holds /data/music, /data/software, /data/scripts (all on /dev/hde1).  So I'd like /home to be at /data/home so I don't have to worry about space.  Thanks for the quick reply.

---

### Post by meng on 2006-11-17
If you did make the change, then that would just mean that /dev/hde1 would hold
/home, /home/music, /home/software, etc.
Space would not be an issue, because if /dev/hde1 is mounted to /home, then /home is only limited by the size of /dev/hde1 (300GB). You may have a misconception of how mountpoints work.

However, do whatever suits you!

---

### Post by slavik on 2006-11-17
This should be done in the single user mode (the recovery/emergency boot.

Commands:
```

sudo -s -H #if in dapper
cd /data
mkdir home
tar cpf - -C /home . | tar xpf - -C /data/home
cd /home
rm -rf *
cd ..
ln -s /data/home /home
reboot

```

the reason for the tar command instead of mv or cp is to preserve permissions. another reason is that tar has no trouble packing up symbolic links (created with 'ln -s').

after those commands, /home will actually be /data/home

---

### Post by aparsons on 2006-11-17
Well, i'd like to reduce clutter in /data.  So, if I went that route, and because of my clutter phobia, i'd have to have user's home directories in /data/user_home/blah.  I guess I could take the following approach:

1) move /home/userA to /data/user_homes/userA

2) move the user's home directory to /home/user_homes/userA, userB, etc

3) add the following line to my fstab:

/dev/hde1 /home reiserfs defaults 0 3

I think that will work.  Thanks...

---

### Post by aparsons on 2006-11-17
> **slavik said:**
> This should be done in the single user mode (the recovery/emergency boot.

Commands:
```

sudo -s -H #if in dapper
cd /data
mkdir home
tar cpf - -C /home . | tar xpf - -C /data/home
cd /home
rm -rf *
cd ..
ln -s /data/home /home
reboot

```

the reasonf or the tar command instead of mv or cp is to preserve permissions. another reason is that tar has no trouble packing up symbolic links (created with 'ln -s').

after those commands, /home will actually be /data/home

This looks like exactly what I want.  I'll give it a try when I'm at the console!  This way, my scripts wont need to be rewritten.  Thanks again!

---

### Post by Jongi on 2006-11-17
1. mkdir /data/user
2. cp /home/user /data/user 
3. change fstab to what you have in post #6 (ie instead of mounting the partition as /data mount it as /home)

---

### Post by slavik on 2006-11-17
> **Jongi said:**
> 1. mkdir /data/user
2. cp /home/user /data/user 
3. change fstab to what you have in post #6 (ie instead of mounting the partition as /data mount it as /home)
cp will not always work (if there are symlinks) ...

Another thing I forgot, in my post above, remove /home line from /etc/fstab unless you have a single root partition (then it is simply part of the / mountpoint and you don't have to do anything).

---

### Post by kosmic on 2006-11-17
> **slavik said:**
> This should be done in the single user mode (the recovery/emergency boot.

Commands:
```

sudo -s -H #if in dapper
cd /data
mkdir home
tar cpf - -C /home . | tar xpf - -C /data/home
cd /home
rm -rf *
cd ..
ln -s /data/home /home
reboot

```the reason for the tar command instead of mv or cp is to preserve permissions. another reason is that tar has no trouble packing up symbolic links (created with 'ln -s').

after those commands, /home will actually be /data/home

For me this is the best solution.

---

### Post by aparsons on 2006-11-19
Do I need to be at the console to "boot into recovery mode"?  One of my servers is 1000 miles away, and I'm rarely at the console...

---

