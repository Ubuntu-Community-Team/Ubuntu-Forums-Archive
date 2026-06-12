---
title: "Two home folders, system screwed, please help!!"
date: 2013-01-29
forum: General Help
---

### Post by henged on 2013-01-29
Kubuntu 12.10, KDE 4.95

I'm not sure what has happened, but somehow i have developed a problem in accessing the /home folder that has screwed my whole system...

i seem to have two /home folders in the 'places' section of Dolphin:
one directs to /home/username
the other to /root/

Since the early hours of this morning some programs that depend on config files in home/username are either not working or have default configuration .
other, however, (like firefox) seem unaffected....?

what can have caused this? how can is solve this?
Help gratefully received!!



EDIT:
well, i wondered if it might be to do with permissions etc. so i followed the guide [here]("http://ubuntuforums.org/showthread.php?t=976610") , basically:
```
sudo chown username /home/username/.dmrc chmod 644 /home/username/.dmrc sudo chown username /home/username      chmod 755 /home/username 
```
I can now access the /root folder (the shortcut Home in the 'places' section) without being root, but i'm not sure if this is correct.

the permission for the /home folder (when i right click properties) are listed as root: is this correct?

programs (eg vlc and libreoffice config) seem to be running ok now...
but i'd still appreciate advice/explanations etc.!
cheers

---

### Post by omeomi on 2013-01-29
> **henged said:**
> I can now access the /root folder (the shortcut Home in the 'places' section) without being root, but i'm not sure if this is correct.

This is not correct unless you are logged in as root or if you ran Dolphin as root (e.g. from terminal). I would say the last is most likely what happened. See what happens if you close Dolphin and open it again, can you still open /root ?

> **henged said:**
> the permission for the /home folder (when i right click properties) are listed as root: is this correct?

The permission for the /home folder itself should be root but the permission for /home/username should be your username. The output of this command:
```
ll /home
```
should give something like this:
```
root root [...] ./
root root [...] ../
root root [...] lost+found/
username username [...] username/ 
```
with [...] being timestamps and size information

---

### Post by Bucky Ball on 2013-01-29
[I]Thread moved to [B]General Help

Reason[/B][/I]**:** Not regarding desktop environments.

---

### Post by henged on 2013-01-30
Thanks for the reply, and sorry for posting in wrong section, i originally thought this was a kde issue...

ll /home gives:

```
$ ll /home
total 12
drwxr-xr-x  3 root root 4096 Oct 25 21:42 ./
drwxr-xr-x 28 root root 4096 Jan 29 10:51 ../
drwxr-xr-x 58 username username  4096 Jan 30 10:00 username/
lrwxrwxrwx  1 root root   44 Oct 25 21:38 .directory -> /etc/kubuntu-default-settings/directory-home

```

And if i close dolphin and run it **not** as root i can still access the /root folder, and /lost+found also.

Does this move us along any?

---

### Post by Bucky Ball on 2013-01-30
How about the output of:

```
sudo blkid
```

---

### Post by henged on 2013-01-30
thanks, 

sudo blkid gives: ```

/dev/sda1: UUID="2fd75162-3f8f-42ea-8c2d-62858015d23e" TYPE="ext4" 
/dev/sda3: LABEL="Data" UUID="d7dbd20a-9ef8-4b83-9aea-708a1598e299" TYPE="ext4" 
/dev/sda5: UUID="e85eb752-d65d-4a9c-82d0-9c7998b10db5" TYPE="swap" 
```

---

### Post by omeomi on 2013-01-30
Not sure how that would help here.

What is the output of this?
```
ll /
```

And then particular the line of /root

---

### Post by henged on 2013-01-30
```
ll /
total 144
drwxr-xr-x  28 root root  4096 Jan 29 10:51 ./
drwxr-xr-x  28 root root  4096 Jan 29 10:51 ../
drwxr-xr-x   2 root root  4096 Nov 28 11:46 bin/
drwxr-xr-x   4 root root  4096 Jan 20 08:39 boot/
drwxr-xr-x   2 root root  4096 Oct 25 21:41 cdrom/
drwxr-xr-x   2 root root  4096 Nov  1 08:31 .config/
drwxr-xr-x  17 root root  4280 Jan 30 14:45 dev/
drwxr-xr-x 151 root root 12288 Jan 29 17:20 etc/
drwxr-xr-x   3 root root  4096 Oct 25 21:42 home/
lrwxrwxrwx   1 root root    32 Jan 20 08:39 initrd.img -> boot/initrd.img-3.5.0-22-generic
lrwxrwxrwx   1 root root    33 Jan 20 08:38 initrd.img.old -> /boot/initrd.img-3.5.0-22-generic
drwxr-xr-x   3 root root  4096 Nov  1 23:24 .kde/
drwxr-xr-x  23 root root  4096 Nov 22 15:52 lib/
drwxr-xr-x   2 root root  4096 Dec 25 21:21 lib32/
drwxr-xr-x   2 root root  4096 Nov 22 15:52 lib64/
drwx------   2 root root 16384 Oct 25 21:38 lost+found/
drwxr-xr-x   4 root root  4096 Jan 27 22:15 media/
drwxr-xr-x   2 root root  4096 Oct  9 16:03 mnt/
drwxr-xr-x   3 root root  4096 Dec  5 10:30 opt/
dr-xr-xr-x 255 root root     0 Jan 29 17:20 proc/
drwxr-xr-x   3 root root  4096 Nov 20 22:50 .qgis/
drwxr-xr-x  11 root root  4096 Jan 28 00:33 root/
drwxr-xr-x  24 root root   820 Jan 30 21:00 run/
drwxr-xr-x   2 root root 12288 Jan  4 11:19 sbin/
drwxr-xr-x   2 root root  4096 Jun 11  2012 selinux/
drwxr-xr-x   2 root root  4096 Oct 17 16:59 srv/
dr-xr-xr-x  13 root root     0 Jan 29 17:20 sys/
drwxrwxrwt  55 root root 20480 Jan 30 21:00 tmp/                                                                                                                                                                                
drwxr-xr-x  11 root root  4096 Nov  4 18:03 usr/                                                                                                                                                                                
drwxr-xr-x  12 root root  4096 Jan 29 16:30 var/                                                                                                                                                                                
lrwxrwxrwx   1 root root    29 Jan 20 08:39 vmlinuz -> boot/vmlinuz-3.5.0-22-generic                                                                                                                                            
lrwxrwxrwx   1 root root    29 Jan 20 08:38 vmlinuz.old -> boot/vmlinuz-3.5.0-22-generic       

```

cheers

---

### Post by omeomi on 2013-01-31
Ah well this explains what is happening:
```
drwxr-xr-x  11 root root  4096 Jan 28 00:33 root/
```
Everyone has read permission for this folder. It is supposed to be this:
```
drwx------  11 root root  4096 Jan 28 00:33 root/
```

In order to do that you need to run this command:
```
sudo chmod 700 /root
```
That should solve it

---

### Post by henged on 2013-01-31
> **omeomi said:**
> Ah well this explains what is happening:
```
drwxr-xr-x  11 root root  4096 Jan 28 00:33 root/
```Everyone has read permission for this folder. It is supposed to be this:
```
drwx------  11 root root  4096 Jan 28 00:33 root/
```In order to do that you need to run this command:
```
sudo chmod 700 /root
```That should solve it
  
Thanks for all your help. I'm going (with some trepidation) to run the command and change the permissions.

But i still wonder what could have caused the permissions to be changed in the first place? Presumably this occurred on jan 28th at half-past midnight, when i was asleep....

And also, why was a new shortcut called 'Home' (that directs to /root) added to the places section of dolphin?

---

