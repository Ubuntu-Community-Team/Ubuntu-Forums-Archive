---
title: "Grub Error 17"
date: 2008-04-04
forum: General Help
---

### Post by skydiver|goose on 2008-04-04
I can't get my laptop to boot up anymore. I googled around and found out that it'll speed the fixing process if I post my output of "sudo fdisk -l"

(I'm running damn-small-linux live on CD)
```

Device        Boot                Start                  End                   Blocks                  ID                  System
/dev/hda1    *                    1                        2361                  18964701           7                   HPFS/NTFS
/dev/hda2                          2362                  9541                  57673350          83                  Linux
/dev/hda3                          9542                  9729                  1510110            5                    Extended
/dev/hda5                          9542                  9729                  1510078+         82                   Linux Swap
```

---

### Post by tamoneya on 2008-04-04
mount your root partition in DSL and then post the contents of /boot/grub/menu.lst

---

### Post by skydiver|goose on 2008-04-04
I know this is a very nooby question; but how?

edit:

when I "mount /dev/hda2" I get "mount: relocation error: mount: undefined symbol: blkid_known_fstype"


apologies for any typos, I can't copy/paste because DSL won't connect to my network, I have to type all the outputs by hand

---

### Post by tamoneya on 2008-04-04
when you mount something you first of all say sudo mount but is also of the form```
mount device directory
```
use the following code to mpunt /dev/hda2
```
su
mkdir /ubuntu
mount /dev/hda2 /ubuntu
```

---

### Post by skydiver|goose on 2008-04-04
I get the same "mount: relocation error: mount: undefined symbol: blkid_known_fstype"

exact commands you provided

---

### Post by tamoneya on 2008-04-04
do you get the same errors with your other three partitions?

---

### Post by skydiver|goose on 2008-04-04
all of them except hda1

and the swap (hda5) won't mount because it's "swapspace"

---

### Post by skydiver|goose on 2008-04-04
I looked at hda1 and it's my windows XP partition. I have some data in my linux partition that I can't lose; even if I just back it up to an external HD and end up having to reformat and start over from scratch, I need that data; although I'd prefer to just fix grub if at all possible...

---

### Post by confused57 on 2008-04-04
Maybe there's something in this thread that may help, if you're not getting a grub boot menu:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

If your system booted normally previously and you're getting a grub boot menu now(with error 17); do you know what you may have changed or done to cause this?

---

### Post by skydiver|goose on 2008-04-04
I've read that thread more than once. lol

I've found something else that says something about finding my grub loader, in which I type:

```

sudo -s
su
grub
find /boot/grub/stage1

```

and I get "Error 15: File not found"





before the error happened, my laptop had something eating up all the memory to the point where I couldn't even kill the processes of the only 4 programs I had open, Firefox, XChat, Pidgin, and Terminal, so I hard to do a hard/force-shutdown

---

### Post by confused57 on 2008-04-04
You might try doing a filesystem check on your Ubuntu partition:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

There are also instructions for mounting Linux & Windows partitions...You may be able to do a filesystem check using DSL, with the partition unmounted.

Herman, a forum member, is the developer of the above site...here's instructions he gave to another user for doing a filesystem check:
[http://ubuntuforums.org/showpost.php?p=4598444&postcount=3](http://ubuntuforums.org/showpost.php?p=4598444&postcount=3)

---

### Post by skydiver|goose on 2008-04-04
I know that /dev/hda2 is my Ubuntu partition, I just can't mount it. I run:

```

mkdir ubuntu
mount /dev/hda2 /ubuntu

```

and I get my earlier mentioned error

---

### Post by confused57 on 2008-04-04
Here are CLI instructions for doing a filesystem check with the Ubuntu live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

It might work with DSL from a root prompt, so you can issue the commands without sudo.

If you have access to another pc, you might want to burn a copy of Gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by wesley_of_course on 2008-04-05
Shot in the dark  here  , not trying to confuse the issue or help but  Super Grub
   has worked for me in the past .  I keep a copy around  for "accidents " .

                                      :-$

---

