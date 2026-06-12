---
title: "Ubuntu (6.10) and /var/run"
date: 2006-12-21
forum: General Help
---

### Post by gpolo on 2006-12-21
Hello ;)

I don't understand what Ubuntu does with directory /var/run, but here is my story.. =)
I installed Ubuntu, then after some days I decided I needed a new partition, and it would mount as /var. Ok, I did it, it mounts and has all the data that the old /var had. After this I started having some problems, like ifup saying my interfaces were up when they werent. Then I checked some Ubuntu start up scripts and saw it does some "different" things inside /var. It mounts /var/lock as varlock, and that is ok, it is fine I believe. It also mounts /var/run as varrun, but that isnt fine. It isn't mounting /var/run as varrun. I believe I've made /var/run a static directory after I created new partition and transfered old data to this new /var, and that would be fine in any other distribution I've used I believe but not with Ubuntu.

So, I need help fixing my /var/run so Ubuntu can do what he wants to do. I tried doing rm -rf /var/run and rebooting to check if it would magically fix, but it didnt work. Well, my system runs, but I need to do some things by hand (coded a script now) to make it work properly. Some daemons cant start during boot by themselves. I dont know what I need to do with /var/run, help me =)

Thanks ;)

---

### Post by chrisccoulson on 2006-12-21
I've had the same problem as you, when putting /var on to a separate partition. I believe that the problem is because the 'loopback' script is executed before /var is mounted - so /var/run does not yet exist.

The solution is to put the folders /var/run and /var/lock on the root filesystem. I believe your current implementation is that the partition containing /var currently has folders called run and lock, and the folder /var on the root filesystem is empty

To fix mine, I used the Live CD to mount my /var filesystem and deleted run and lock. I then mounted my root filesystem and added the folders /var/run and /var/lock.

I think there might be a quicker way to do this but I can't remember how.

---

### Post by gpolo on 2006-12-21
you can do: init 1
and do these actions, i will try something like what you said

Thanks =)

---

### Post by gpolo on 2006-12-21
nice, it worked :D

what I did was:

init 1
umount /var/lock/
umount /var
mkdir /var/run
reboot # just to verify if it really worked

thanks :D

---

