---
title: "Can't login-no space on disk (but there is!)"
date: 2006-07-28
forum: General Help
---

### Post by ryan76 on 2006-07-28
I started getting space warnings a couple of days ago and deleted a whole lot of music and ISOs etc. However I got more and more warnings, then rebooted and couldn't login - I get a warning that there is no space to create files needed to log me in.

I am using the Live CD now and have deleted even more stuff, but df -h looks like this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/casper-snapshot
                      2.0G  1.4G  577M  70% /
tmpfs                 343M  4.0K  343M   1% /dev/shm
tmpfs                 343M   14M  330M   4% /lib/modules/2.6.12-9-amd64-generic/volatile
tmpfs                 343M   12K  343M   1% /tmp
tmpfs                  10M  2.9M  7.2M  29% /dev
/dev/hda1              72G   71G     0 100% /mnt

I just can't work out where the space is being used and why deleting gigs of stuff hasn't helped. I am on the AMD64 version with a 32 bit chroot set up which seems to mirror everything to the chroot.

What can I do?! I just want to get back in to my normal system to back everything up then wipe it to install 6.06.

I have checked this thread
[http://www.ubuntuforums.org/showthread.php?t=160837](http://www.ubuntuforums.org/showthread.php?t=160837)

There is nothing in the /var/cache/apt/archive directory except a file with 0 bytes called lock and an empty directory called partial.

The contents of my whole system mounted on /mnt are only 20GB.

---

### Post by OpsVentus on 2006-07-28
Hello Ryan,

/dev/mapper/casper-snapshot < this is your root filesystem? Can you write to it?
What does your fstab look like?

Cheers,
Bart.

---

### Post by ryan76 on 2006-07-28
Hi Bart

This is my /etc/fstab:

/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0

I tried saving a file to my mounted home folder and got a General input/output error.

/dev/mapper/casper-snapshot isn't a folder? not sure what you mean.

Thanks

---

### Post by OpsVentus on 2006-07-28
Can you create a directory in your home folder?
/dev/hda1 72G 71G 0 100% /mnt <looks like /mnt is 100% full, maybe you can try to remove some file's there.

Cheers,
Bart.

---

### Post by ryan76 on 2006-07-28
No I can't create a directory, it says there is no space.

That's the thing, there is only 16GB used by my home folder, and it doesn't matter how much I delete from it, I still get the same results (that it's using 71 of 72G).

Since working on this again tonight I have deleted another 4GB from my home folder and am still getting the same error messages.

I'm thinking that there must be some huge files that aren't in my home folder but I don't know what to delete outside of it.

---

### Post by OpsVentus on 2006-07-28
Can you acces /mnt directly? And delete some stuff there?

---

### Post by ryan76 on 2006-07-28
Yes, that's what I have been doing, and it isn't helping.

---

### Post by ifokkema on 2006-07-28
If I understand correctly, you tried deleting stuff from /dev/hda1, which is full. Did you do this from a graphical interface, or through a terminal? If you used Gnome, the files may still reside in the .Trash folder.
You can try the du command to see where the largest files are in your home directory. Running
```
du -h --max-depth=1
```
will show you the size of the dirs in your home folder, and the total usage of you home.

Hope this helps!

---

### Post by ryan76 on 2006-07-28
Cheers for that. 

I mounted the /dev/hda1 to /mnt. If I right-click and go Properties, it totals 19.3GB in the /mnt folder. If I click on folders in the /mnt folder it says at the bottom of the Nautilus screen 'Free space: 0 bytes'. I have deleted gigs and gigs of stuff so far. Trash folder has 4kb.

Why is it showing up as full when it isn't?

---

### Post by ifokkema on 2006-07-28
OK - that is 'funny'.
Could you please post the output of
```
du -h --max-depth=1 /mnt/
```

---

### Post by ryan76 on 2006-07-28
OK I think I see it in /mnt/var, which is weird because if i right-click in Properties in Nautilus that folder shows up as 81MB, but /mnt/var/archives is unreadable.

ubuntu@ubuntu:~$ sudo du -h --max-depth=1 /mnt/
48K     /mnt/lost+found
36M     /mnt/etc
44K     /mnt/media
48G     /mnt/var
4.0K    /mnt/debootstrap
147M    /mnt/lib
2.0G    /mnt/usr
5.3M    /mnt/bin
17M     /mnt/boot
112K    /mnt/dev
18G     /mnt/home
8.0K    /mnt/mnt
4.0K    /mnt/proc
804K    /mnt/root
9.2M    /mnt/sbin
12K     /mnt/tmp
4.0K    /mnt/sys
4.0K    /mnt/srv
4.0K    /mnt/opt
4.0K    /mnt/initrd
1.6G    /mnt/chroot
4.2M    /mnt/lib32
69G     /mnt/

cheers for your help

Edit: I found this thread
[http://www.ubuntuforums.org/showthread.php?t=101508&page=2](http://www.ubuntuforums.org/showthread.php?t=101508&page=2)

It seems the answer to my problem is to delete stuff from /var/archives but I can't get into it from Nautilus or the terminal.

---

### Post by ryan76 on 2006-07-29
Further digging reveals:

These large files

5773444 ubuntu-home.20060724.tar.gz
12888868 ubuntu-home.20060725.tar.gz
31266872 ubuntu-home.20060723.tar.gz


ubuntu@ubuntu:/$ sudo find -name ubuntu-hom*
./mnt/var/archives/ubuntu-home.20060721.tar.gz
./mnt/var/archives/ubuntu-home.20060723.tar.gz
./mnt/var/archives/ubuntu-home.20060724.tar.gz
./mnt/var/archives/ubuntu-home.20060725.tar.gz
ubuntu@ubuntu:/$ cd /mnt/var/archives/
bash: cd: /mnt/var/archives/: Permission denied
ubuntu@ubuntu:/$ sudo cd mnt/var/archives/
sudo: cd: command not found
ubuntu@ubuntu:/$

This might be a n00b question but why can't i sudo cd? 

argh all i need to do is delete these files.

---

### Post by ifokkema on 2006-07-29
> **ryan76 said:**
> Further digging reveals:

These large files

5773444 ubuntu-home.20060724.tar.gz
12888868 ubuntu-home.20060725.tar.gz
31266872 ubuntu-home.20060723.tar.gz
If these sizes are bytes, then they are not that big. But it's a start :)

> **ryan76 said:**
> This might be a n00b question but why can't i sudo cd?
I don't know exactly why, but I know it always does this.

> **ryan76 said:**
> argh all i need to do is delete these files.
```
sudo rm /mnt/var/archives/ubuntu-home*
```

Also, you might want to take a look if /mnt/var/log takes up a lot of space:
```
sudo du -h --max-depth=1 /mnt/var
```
or
```
sudo du -h --max-depth=1 /mnt/var/log
```

If, for some reason, your log files are flushed with messages, your disk space soon runs out as well.

---

### Post by ryan76 on 2006-07-29
Those numbers were in Kb not bytes! They were the culprits. 

Thanks heaps for everyone's input, I have deleted them and logged in. (space free: 52Gb!) What a learning experience! I found some other large files lurking hidden in my home folder too.

Having a celebratory beer and backing up!!!!

---

### Post by ifokkema on 2006-07-29
Good for you! Great you got it to work.
Having problems like these is (unfortunately?) the best way to learn things. Long-term Linux users are much more comfortable with the command line because it's what they had to use when having problems. Nowadays so many things can be done through the GUI.

Eitherway, the only thing left for you to do is find out how these files got there. Or else, you will be having this probleem soon again :)
It appears a process is backing up your home directory. Possibly a full backup every day.

---

### Post by mmb on 2006-08-03
I had the same problem in /var/archives (70 GB) with compressed .tar files. I consider after loocking at one of them that they are originated by an automated backup process. It seems to me strange because i usually use bacula for daily backup on another disk. I checked with Synaptic for some backup application and I found that the 'backup-manager' application was installed, quite sure for a personal mistake. At the moment I have removed this application and I'll check if space disk problem 'll end with this.
thanks for all past and future contribution.

---

### Post by ryan76 on 2006-08-06
Yes I also had backup-manager installed but I don't remember actually using it. It must be very self-motivated!

---

