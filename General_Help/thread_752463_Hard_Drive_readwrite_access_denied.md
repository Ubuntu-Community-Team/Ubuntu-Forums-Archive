---
title: "Hard Drive read/write access denied?"
date: 2008-04-11
forum: General Help
---

### Post by brijizacks on 2008-04-11
I have been running Ubuntu for several months and am totally addicted.  Yesterday, I was copying some files from one of my partitions to another.  Today, I look at the drive and it says I can't write to it at all.  When I go to the properties it says the owner is unknown, not root like everything else.  THEN, when I tried to delete the partition and start again, I still have the same problem.  ARRRGH - someone tell me how this bad boy imploded please :)

---

### Post by ibuclaw on 2008-04-11
type in
```
 ls -l 
```
in the directory where the hard-drive is mounted is. Don't enter the folder (yet) just get the permissions of the root of the folder.

And copy and paste the line in "/etc/fstab" which notes the mounting of your hard-drive.

Regards
Iain

---

### Post by brijizacks on 2008-04-11
Thanks for the help!  Buuuut - I am a TOTAL noob when it comes to the terminal.  Quite frankly it scares me.  How do I get to where I need to type that bad boy in.

Thanks!

---

### Post by brijizacks on 2008-04-11
I mean, I know how to get to terminal

but it is always in the desktop folder and I don't know how to move from there other than to folders I see...

---

### Post by dondad on 2008-04-12
> **brijizacks said:**
> I mean, I know how to get to terminal

but it is always in the desktop folder and I don't know how to move from there other than to folders I see...

You use the cd command. You can do it relative, but if you don't know how to move around, then it is probably easier to use the full path. For instance, if the folder that you are trying to write to is in your home directory and named foo, you would type:
```

cd /home/foo

```
note that there is a space after the cd.

if it was in your home directory in the documents directory, the command would be 
```

cd /home/documents/foo

```

You should then see the path to foo after the prompt. At that point, you can do 
```

ls -l

``` 
 to see the enclosed files along with owners and permissions.

Post the output of that and someone should be able to help you.

---

### Post by brijizacks on 2008-04-14
arrrrrrrrrrgh!

First off - thanks for helping me navigate - I had no idea you had to put that space in

BUT

I type in the ls -l and it says total 0
then that's it
so what do I do from there?

---

### Post by brijizacks on 2008-04-14
this is what I did/got in the terminal

brijizacks@brijizacks-laptop:/media/sda2$ 
brijizacks@brijizacks-laptop:/media/sda2$ cd /media
brijizacks@brijizacks-laptop:/media$ dir
cdrom  cdrom0  sda2  sda3
brijizacks@brijizacks-laptop:/media$ ls -l
total 14
lrwxrwxrwx 1 root root       6 2008-03-12 15:16 cdrom -> cdrom0
dr-xr-xr-x 3 root root    2048 2008-03-31 03:05 cdrom0
drwxr-xr-x 2 root root    4096 2008-03-12 15:16 sda2
drwxrwx--- 1 root plugdev 8192 2008-04-14 18:00 sda3
brijizacks@brijizacks-laptop:/media$ /etc/fstab
bash: /etc/fstab: Permission denied
brijizacks@brijizacks-laptop:/media$ 

I really appreciate you helping me through this

---

### Post by logos34 on 2008-04-14
it's

**cat** /etc/fstab

Is sda2 the one you're trying to mount and access?  Is this an external drive?

---

### Post by brijizacks on 2008-04-14
score!  sort of....  

So now the owner is root, but I still don't have permission to write to it

It USED to work fine - it is a partition of my 100gb internal drive so I am baffled how it just all of a sudden started not letting me do anything with it....

For some reason in my file explorer it lists the drive as simply disk??

Weird - it says root is the owner when I go through media

but when I simply explore computer:///, it still says owner is unknown.  Even when I format it stays.... but it worked fine a couple of days ago and all I did was copy some files to the drive so I have no clue why this is doing this.
Here is what I get when I type in what you said in terminal.
brijizacks@brijizacks-laptop:/media/sda2$ 
brijizacks@brijizacks-laptop:/media/sda2$ cd /media
brijizacks@brijizacks-laptop:/media$ dir
cdrom  cdrom0  sda2  sda3
brijizacks@brijizacks-laptop:/media$ ls -l
total 14
lrwxrwxrwx 1 root root       6 2008-03-12 15:16 cdrom -> cdrom0
dr-xr-xr-x 3 root root    2048 2008-03-31 03:05 cdrom0
drwxr-xr-x 2 root root    4096 2008-03-12 15:16 sda2
drwxrwx--- 1 root plugdev 8192 2008-04-14 18:00 sda3
brijizacks@brijizacks-laptop:/media$ /etc/fstab
bash: /etc/fstab: Permission denied
brijizacks@brijizacks-laptop:/media$

---

### Post by dondad on 2008-04-14
> **brijizacks said:**
> score!  sort of....  

So now the owner is root, but I still don't have permission to write to it

It USED to work fine - it is a partition of my 100gb internal drive so I am baffled how it just all of a sudden started not letting me do anything with it....

For some reason in my file explorer it lists the drive as simply disk??

Weird - it says root is the owner when I go through media

but when I simply explore computer:///, it still says owner is unknown.  Even when I format it stays.... but it worked fine a couple of days ago and all I did was copy some files to the drive so I have no clue why this is doing this.
Here is what I get when I type in what you said in terminal.
brijizacks@brijizacks-laptop:/media/sda2$ 
brijizacks@brijizacks-laptop:/media/sda2$ cd /media
brijizacks@brijizacks-laptop:/media$ dir
cdrom  cdrom0  sda2  sda3
brijizacks@brijizacks-laptop:/media$ ls -l
total 14
lrwxrwxrwx 1 root root       6 2008-03-12 15:16 cdrom -> cdrom0
dr-xr-xr-x 3 root root    2048 2008-03-31 03:05 cdrom0
drwxr-xr-x 2 root root    4096 2008-03-12 15:16 sda2
drwxrwx--- 1 root plugdev 8192 2008-04-14 18:00 sda3
brijizacks@brijizacks-laptop:/media$ /etc/fstab
bash: /etc/fstab: Permission denied
brijizacks@brijizacks-laptop:/media$

Try this. Change to the directory that you need to set permissions for. In this case, cd /media/sda2.

Then do this, where user is your user name.

```


sudo chown -R user:user .

(Note the dot, it is important)

then 

sudo chmod -R u_rwx .

again, note the dot.

```

---

### Post by brijizacks on 2008-04-15
ok so the first part worked, but then the second didn't

here is what I got

cdrom  cdrom0  sda2  sda3
brijizacks@brijizacks-laptop:/media$ cd /media/sda2
brijizacks@brijizacks-laptop:/media/sda2$ sudo chown -R user:user .
[sudo] password for brijizacks:
chown: `user:user': invalid user
brijizacks@brijizacks-laptop:/media/sda2$ sudo chown -R brijizacks:brijizacks .
[sudo] password for brijizacks:
brijizacks@brijizacks-laptop:/media/sda2$ sudo chmod -R u_rwx .
chmod: invalid mode: `u_rwx'
Try `chmod --help' for more information.
brijizacks@brijizacks-laptop:/media/sda2$ sudo chmod -R u_rwx .
chmod: invalid mode: `u_rwx'
Try `chmod --help' for more information.
brijizacks@brijizacks-laptop:/media/sda2$ 

I copied all the data from the drive that I wanted to save - isn't their a way I can just reset it via a partition or something?  Every time i've tried to format and remount it still says owner is unknown!

Thanks again for your patience with this ultra noob

---

