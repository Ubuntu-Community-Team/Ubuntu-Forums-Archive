---
title: "unable to execute /opt programs"
date: 2007-06-08
forum: General Help
---

### Post by balak on 2007-06-08
hi all,

It'll be great if any of you can help me with this perplexing problem.

I had edgy in my old hard drive (sda). 
Partition in sda for Edgy
/dev/sda1  /boot
/dev/sda2 /
/dev/sda3 /home
/dev/sda4  swap

I decided to get a new harddrive (sdb) and load feisty in it. I wanted to use the programs that I had installed in edgy like google-earch, cxoffice etc. Since I had installed these in /opt,  I decided to copy them and mount  as a separate partition in Feisty

so this is the table for feisty

/dev/sdb1 /boot
/dev/sdb2 /
/dev/sdb3 swap
/dev/sdb4 extended
/dev/sdb5 /home
/dev/sdb6 /opt          ext3     defaults    0     2

When I boot into feisty, I am unable to execute any program in /opt/

This is the error:
bash: ./googleearth-bin: No such file or directory

I can see the file, it has execute permissions etc.

I think this may have something to do with the /etc/fstab entry (as given above).  Any ideas will be helpful.

thanks in advance!

---

### Post by taurus on 2007-06-08
You need to add /opt to your path since the default PATH doesn't include /opt.

Edit ~/.bashrc

```
gedit ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH:/opt/googleearth
export PATH
```
Replace /opt/googleearth with the actual path to googleearth-bin.

Then, either log out and back in again or rehash it with

```
source ~/.bashrc
```

---

### Post by balak on 2007-06-08
taurus, 

thanks for your quick reply. But it is not a PATH issue. I should have mentioned this earlier - I had tried to execute the file from its own directiory (/opt/google-earth/).

I have the same error after adding /opt/google-earth to PATH

> $googleearth
exec: 50: ./googleearth-bin: not found
$googleearth-bin
bash: /opt/google-earth/googleearth-bin: No such file or directory

---

### Post by taurus on 2007-06-08
Is googleearth-bin in /opt/google-earth/?

```
ls -la /opt/google-earth
```
Any chance you are mixing x86 with x86_64?

---

### Post by balak on 2007-06-08
the permissions are fine:

```
ls -al /opt/google-earth/googleearth*
-rwxr-xr-x googleearth
-rwxr-xr-x googleearth-bin
```

But your second point may be valid. I remember adding 32 bit libraries to my edgy build so I am going to dig into this further

However, shouldn't it have given me "Unable to execute binary error' - the kind you get when you mistakenly run in linux an exe or a binary compiled for solaris ?

---

### Post by yabbadabbadont on 2007-06-08
Change ```
/dev/sdb6 /opt ext3 defaults 0 2
``` to ```
/dev/sdb6 /opt ext3 defaults,exec 0 2
```
and see if it helps.

---

### Post by balak on 2007-06-08
> **yabbadabbadont said:**
> Change ```
/dev/sdb6 /opt ext3 defaults 0 2
``` to ```
/dev/sdb6 /opt ext3 defaults,exec 0 2
```
and see if it helps.

Doesn't help. 

Curiously, I tried executing the programs in /dev/sdb6 from edgy and they work!

/media/sdb6/google-earth/googleearth runs.

All the programs I installed in /opt (skype, google-earth, picasa, rainlendar) are 32 bit programs. I need to figure out what libraries I need to install to be able to run them!

---

### Post by Mr. C. on 2007-06-08
This may indeed be a shared library or library incompatibility issue, with the shell returning in incorrect error code.  What do you get if you try starting csh and running the command using a full path name?

MrC

---

### Post by balak on 2007-07-01
OK, I was able to fix this issue.

Just posting it here for completeness! (if somebody else ends up having this issue).

Basically I just added a bunch of 32 bit libraries:
ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6 linux32

using synaptic

I dont think all of these are required, but the linux32 and ia32-libs should be.

---

