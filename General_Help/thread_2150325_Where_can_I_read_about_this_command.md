---
title: "Where can I read about this command?"
date: 2013-05-31
forum: General Help
---

### Post by mikodo on 2013-05-31
In setting up partitioning and booting, I have seen this command before. Where can I read about it? 

[Most recently, I see it here in post #2.]("http://ubuntuforums.org/showthread.php?t=2149793&p=12671941#post12671941")

```
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
```

Thanks.

---

### Post by Isamu715 on 2013-05-31
I don't know where you can read about this specific command but I can tell you what it does. It's basically a simple *for* loop that'll execute the command between *do *and *done* once for every argument(here "/dev /dev/pts /proc etc."). $i will be replaced by the argument. It's equivalent to running:
```
sudo mount -B /dev /mnt/dev
sudo mount -B /dev/pts /mnt/dev/pts
sudo mount -B /proc /mnt/proc
sudo mount -B /sys /mnt/sys
sudo mount -B /run /mnt/run
```
For command-specific options to commands like *mount* see the man page, for example:
```
man mount
```

---

### Post by Cheesemill on 2013-05-31
There's a few different commands there, which one are you talking about?

sudo - Runs the following command with root privileges.

mount - Used to mount filesystems.

The bash for loop - A list of commands is executed for each value in the list.

One way to find out about a command is to look at its man page, for example...
```
man sudo
man mount
```
I wouldn't recommend the man page for bash as it's so massive but there are plenty of good articles on the internet, just Google for 'bash for loop'.
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_01.html)

In the example you gave in your post it's just being used as a shorthand way of writing the following commands...
```
sudo mount -B /dev /mnt/dev
sudo mount -B /dev/pts /mnt/dev/pts
sudo mount -B /proc /mnt/proc
sudo mount -B /sys /mnt/sys
sudo mount -B /run /mnt/run
```
This saves on typing as well as reducing the chance of making a typo. Also if you wanted to add another directory to the list, you only have to add it in one place.

I'd say that it's being used to bind mount the directories needed to be able to chroot into a different installation. The **ch**ange **root** command is used amongst other things to install or remove software on a non-running system from a different running system (you change root to the other system before running your commands).
```
man chroot
```


Edit - Ninja'd. I obviously took too long typing that :)

---

### Post by mikodo on 2013-05-31
Thanks folks.

The > i < had me confused.

;p

---

