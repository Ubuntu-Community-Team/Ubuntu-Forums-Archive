---
title: "[SOLVED] missing space on hard disk"
date: 2007-08-07
forum: General Help
---

### Post by martin_m79 on 2007-08-07
Hi all,

This is my first post here and I start with a problem which I just cant solve on my own.
I read all similar treads, but couldnt find a solution for me. 

My system is Ubuntu Server 6.06 and I dont know where is all my diskspace on / went.
I just a have basic installation, with some additional stuff like Samba but this shouldnt occupy 63Gig.

The system runs for quite a while now, never had any problem. I am copying a MS SQL database every night to / - this doesnt work anymore because I ran out of space now. Furthermore I got setup a cronjob which rsyncs some stuff to /mnt/snapshotdisk in a rotation. Maybe this caused something go wrong?

My / is on a Linux Software Raid mirror - md0.

First of all, the output of mount:
```

/dev/md0 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hda1 on /home type ext2 (rw)
/dev/hda2 on /data type ext2 (rw)
/dev/sdc1 on /mnt/snapshotdisk type ext3 (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

```


... and this is the output of df -h
You can see that I only have 5.3GB left on / :confused:
```

/dev/md0               72G   63G  5.3G  93% /
varrun                506M  488K  505M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/hda1              28G  8.8G   18G  34% /home
/dev/hda2             248G  193G   43G  83% /data
/dev/sdc1              74G   43G   28G  61% /mnt/snapshotdisk 

```

Next one: sudo du -h --max-depth=1 in / gives me the following:
```

48K     ./lost+found
417M    ./var
9.8M    ./etc
8.0K    ./media
76M     ./lib
950M    ./usr
3.1M    ./bin
9.5M    ./boot
228K    ./dev
8.8G    ./home
43G     ./mnt
898M    ./proc
2.1M    ./root
8.2M    ./sbin
32K     ./tmp
0       ./sys
4.0K    ./srv
472M    ./opt
4.0K    ./initrd
11M     ./tftpboot
68K     ./userdata
193G    ./data
17G     ./backups
4.0K    ./tempsuche
264G    . 

```

I dont see anything unusual, no big logfiles in /var..., neither can I find big files or a trash in root or something.

Can someone please try and help me...I appreciate any kind of help.
and please let me know if you need additional information...

Thanks a lot in advance

best regards
Martin

---

### Post by fjgaude on 2007-08-07
What does your /root/.Trash file show?  and/or /<user>/.Trash?

The deleted stuff has to be somewhere, eh?

frank

---

### Post by martin_m79 on 2007-08-07
The strange thing is - I dont see the .Trash.

Example:
```

root@general:~# ls -al
total 108
drwxr-xr-x 14 root root 4096 2007-07-13 17:54 .
drwxr-xr-x 26 root root 4096 2007-08-06 18:58 ..
drwx------  2 root root 4096 2007-05-14 15:01 .aptitude
-rw-------  1 root root 5627 2007-07-13 19:23 .bash_history
-rw-r--r--  1 root root 2227 2005-10-13 08:04 .bashrc
drwx------  5 root root 4096 2007-05-16 13:45 .cache
drwx------  5 root root 4096 2007-05-15 11:24 .config
drwx------  2 root root 4096 2007-05-15 11:24 Desktop
drwx------  2 root root 4096 2007-05-17 16:06 .gconf
drwx------  2 root root 4096 2007-05-17 16:06 .gconfd
drwx------  3 root root 4096 2007-05-16 14:23 .gnome2
drwx------  2 root root 4096 2007-05-15 11:24 .gnome2_private
-rw-------  1 root root  964 2007-05-17 15:36 .ICEauthority
-rw-------  1 root root   35 2007-05-17 16:35 .lesshst
drwxr-xr-x  3 root root 4096 2007-05-15 11:24 .local
drwxr-xr-x  3 root root 4096 2007-05-24 12:42 .mc
drwx------  3 root root 4096 2007-05-16 13:30 .mozilla
-rw-r--r--  1 root root  141 2005-10-13 08:04 .profile
-rw-------  1 root root   52 2007-05-16 12:39 .serverauth.5032
-rw-------  1 root root  156 2007-05-16 14:17 .serverauth.5204
drwx------  3 root root 4096 2007-05-17 16:02 .synaptic
-rw-------  1 root root 1205 2007-07-13 17:54 .viminfo
-rw-------  1 root root  152 2007-05-16 12:39 .Xauthority
-rw-------  1 root root 8690 2007-05-17 16:06 .xsession-errors
root@general:~#

```

Thanks for the reply.

best regards

---

### Post by fjgaude on 2007-08-07
Yes, that is strange... I've looked into my trash hidden folders and even though I have nothing in either they still show in an ls -a.

We have to think about this... the lost bytes have to be hiding somewhere. Try deleting a short file and see if you can find a /.Trash somewhere.

frank

---

### Post by martin_m79 on 2007-08-07
What can I do....?

Now I remember that I "imported" the users from another linux system by copying the /etc/passwd and /etc/group file to Ubuntu. The old system was a Mandrake. Maybe this caused the problem with the Trash which I cant find now?

Lets assume this is the problem. Where does Ubuntu store the trash if there is no ".Trash"?

Shouldnt "du -h --max-depth=1" show me the big files anyhow?

I really dont want to reinstall...It must be possible to find out what is occupying the space...

Thanks for the help so far

Best regards
Martin Miethe

---

### Post by fjgaude on 2007-08-07
Okay, the big lost deleted files are in /dev/md0, eh?

Was /dev/md0 mounted, when you did the sudo du -h --max-depth=1?

I think the lost files are in the /root/.Trash or some other Trash, but since /dev/md0 likely has no OS, it is just data, right? You have to be in the right partition to find the .Trash file or files.

Poke around... I can't think of much more. <smile>

frank

---

### Post by milosz.galazka on 2007-08-07
Hello, maybe you should run fsck to check this filesystem.

```
sudo du -hx --summarize /
```
shows 63 Gb used too?

---

### Post by martin_m79 on 2007-08-07
/dev/md0 holds the system and is mounted as / and is therefore always mounted.

Again: I did not lose any files, I just dont know where all my space went on /

:(

Thanks and greetings

Martin

---

### Post by meierfra on 2007-08-07
Give "baobab" a try. Its a nice graphical disk usage analyzer.

---

### Post by fjgaude on 2007-08-07
Also on Gnome there is a program under Applications/Accessories/Disk Usage Analyzer that might show something interesting, a clue to what you seek.

frank

---

### Post by meierfra on 2007-08-07
> **fjgaude said:**
> Also on Gnome there is a program under Applications/Accessories/Disk Usage Analyzer that might show something interesting, a clue to what you seek.

frank

that is baobab

---

### Post by martin_m79 on 2007-08-07
the post from milosz.galazka brings up something interesting, I think!

```

sudo du -hx --summarize /

```

gives me a
```

19G /

```

Still not sure what this exactly means, but it looks like there are only 19G used on /
This would be a realistic value.

The x switch skips directories on other filesystems.

But I still dont get it...why does df -h tell me 63G?

Thanks so far to all for the replies.

Greetings
Martin

---

### Post by pmg on 2007-08-08
Has the system been rebooted recently?  If not, one possibilty is the missing space is being used by open/deleted files.  If a file is open and then deleted from the filesystem, it's data blocks are still on disk, so they shows up as in use in **df**, but since it's not in any direcotry **du** doesn't see it.

---

### Post by martin_m79 on 2007-08-08
Yes I rebooted recently and unfortunately this does not fix the problem.

Since 
```

sudo du -hx --summarize /

```

shows the correct value, I thought this would be a real good hint for someone who knows more than me - I am still stuck on this.

best regards
martin

---

### Post by fjgaude on 2007-08-08
Have you tried deleting a small file and finding where /.Trash is?

The difference between the two reports, 19G vs 63G, has to be because one shows the files that are truly deleted and the other doesn't (released but recoverable). Do both a delete a file while in root and not.

frank

---

### Post by martin_m79 on 2007-08-08
No, cannot find the trash :-(

Ok, df -h says I got 5.3GB left, du -hx says 19GB occupied.
Then I copied two big files (approx. 1GB together) to the root partition.

After that I checked:

```

df -h

```
says 4.4 GB

```

du -hx --summarize /

```
says 20G

Ok, this is what one would expect.

Now I deleted the big files and checked again and both, df and du show me the same value before copying the 2 big files to /.

```

df -h

```
says 5.3 GB

```

du -hx --summarize /

```
says 19G

This means df and du show me the same and not "truly deleted" and "deleted but recoverable", right?

greetings
martin

---

### Post by martin_m79 on 2007-08-08
Ok, my problem does not seem to be the trash since everything gets deleted right away.

Nothing in the trash, no big logfiles...nothing... the output of du proofs this again:

```

mmiethe@general:/$ sudo du -h --max-depth=1
Password:
48K     ./lost+found
410M    ./var
9.8M    ./etc
8.0K    ./media
76M     ./lib
950M    ./usr
3.1M    ./bin
9.5M    ./boot
228K    ./dev
9.3G    ./home
42G     ./mnt
900M    ./proc
2.1M    ./root
8.2M    ./sbin
56K     ./tmp
0       ./sys
4.0K    ./srv
472M    ./opt
4.0K    ./initrd
11M     ./tftpboot
68K     ./userdata
194G    ./data
17G     ./backups
264G    .

```

If I sum up all dirs in the root partition PLUS the /mnt I get the value of 63GB, which df -h shows me.

It seem that df adds the size of /mnt to the root partition!
Why???

Again the output of "df":
```

mmiethe@general:/mnt$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               72G   63G  5.3G  93% /
varrun                506M  488K  505M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/hda1              28G  9.3G   17G  36% /home
/dev/hda2             248G  194G   42G  83% /data
/dev/sdc1              74G   42G   29G  60% /mnt/snapshotdisk
mmiethe@general:/mnt$

```

Here you see that /mnt/snapshotdisk occupies 42GB. The strange thing is that those value also gets
added to /
This shouldnt be like this...?

Greetings

---

### Post by fjgaude on 2007-08-08
Maybe, but I'm not sure... you have to be able to empty or recover-file from a /.Trash directory to really know.

Can you add a trash can using the "Add to Panel" feature in Gnome? If so, see if you can find anything in it after deleting a file.

Boy, this is truly getting to be a mystery.

frank

---

### Post by martin_m79 on 2007-08-08
This is ubuntu server version.... 

Ok I recently installed XFCE, never use it. I dont find a option to add a trash can there.

thanks and greetings
martin

---

### Post by martin_m79 on 2007-08-08
Ok, I solved it.

Really stupid problem.

I had like 42 GB files in /mnt/snapshotdisk, like physically.

I dont know why, I screwd this up one day and ran my rsync script without having the snapshotdisk
phyiscally mounted so everything went to the / disk.

Then I mounted the disk and the content got covered by the mountpoint....

Well..no comment 

Thanks for the effort

greetings
martin

---

### Post by fjgaude on 2007-08-08
Wow, at least the issue is solved. You can now use the [SOLVED] button in the Tread Tools  menu. And all will know it was operator error all along. <smile>

Still I would personally like to know why you cannot find a Trash Can anywhere... 

frank

---

