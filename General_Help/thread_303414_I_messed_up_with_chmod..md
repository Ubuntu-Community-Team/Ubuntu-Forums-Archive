---
title: "I messed up with chmod."
date: 2006-11-20
forum: General Help
---

### Post by eldaria on 2006-11-20
Ok so I have a folder in my root called /stuff with a whole bunch of subfolders.
I wanted to give everyone full access to this folder as it is shared on an nfs share.

So thinking that I was insid this folder wanteing to change all the subfolders I type:

sudo chmod -R 777 *

After a few seconds I realize I was not in the /stuff folder but in /

I quickly hit ctrl-c, and fears the damage I have done.
 ls -l shows that it had gone through a couple of folders.

```

drwxrwxrwx   2 root root  2552 2006-11-12 00:34 bin
drwxrwxrwx   4 root root  1024 2006-11-12 00:34 boot
lrwxrwxrwx   1 root root    11 2006-11-12 00:18 cdrom -> media/cdrom
drwxrwxrwx  17 root root 14980 2006-11-20 12:51 dev
drwxrwxrwx  71 root root  4688 2006-11-20 13:17 etc
drwxrwxrwx   7 root root   160 2006-11-12 01:56 home
drwxr-xr-x   2 root root    48 2006-11-12 00:20 initrd
lrwxrwxrwx   1 root root    38 2006-11-12 00:35 initrd.img -> boot/initrd.img-2.6.15-27-amd64-server
lrwxrwxrwx   1 root root    38 2006-11-12 00:22 initrd.img.old -> boot/initrd.img-2.6.15-26-amd64-server
lrwxrwxrwx   1 root root    24 2006-11-14 00:35 keep -> /home/blevinse/tmp/keep/
drwxr-xr-x  15 root root  4256 2006-11-20 00:26 lib
drwxr-xr-x   2 root root  2048 2006-11-20 00:26 lib32
lrwxrwxrwx   1 root root     3 2006-11-12 00:20 lib64 -> lib
drwxr-xr-x   5 root root   168 2006-11-12 00:18 media
drwxr-xr-x   2 root root    48 2006-08-03 12:59 mnt
drwxr-xr-x  17 root root   424 2006-11-20 01:10 newz
drwxr-xr-x   2 root root    48 2006-11-12 00:20 opt
dr-xr-xr-x 151 root root     0 2006-11-19 00:27 proc
drwxr-xr-x   5 root root   368 2006-11-15 11:31 root
drwxr-xr-x   2 root root  5760 2006-11-20 02:12 sbin
drwxr-xr-x   2 root root    48 2006-11-12 00:20 srv
drwxr-xr-x  10 root root     0 2006-11-19 00:27 sys
drwxrwxrwt   6 root root  1080 2006-11-20 13:58 tmp
drwxr-xr-x  13 root root   336 2006-11-20 00:29 usr
drwxr-xr-x  16 root root   368 2006-11-12 01:31 var
lrwxrwxrwx   1 root root    35 2006-11-12 00:35 vmlinuz -> boot/vmlinuz-2.6.15-27-amd64-server
lrwxrwxrwx   1 root root    35 2006-11-12 00:22 vmlinuz.old -> boot/vmlinuz-2.6.15-26-amd64-server

```

As you can see it got to the loose files in root and the /bin /boot /dev /etc and /home

So is there anyway of restoring the default permission? or could someone list me what the permissions should be so that I can manually restore them?

---

### Post by eldaria on 2006-11-20
Ok it seems to be a bit more messy than I thought.

I was not able to sudo anymore, it tells me that /etc/sudoers is 0777 but should be 0440.

So I thought I would reboot into single mode to fix it from there, first of all I did not have rights to perfrom a reboot.
So had to do it the hard way with the reset button.

Now It won't boot at all, not even in emergency mode.

Well now I Had to go to work, I have a backup of /etc on a floppy disk, this is done every 1 hour so it should be recent.

But how can i get in to fix this?
I guess I can use the Boot disk in some way, but how do I use the boot disk to get into rescue mode?

The System is Ubuntu Server Dapper 64bit.

---

### Post by Gaweph on 2006-11-20
I would suggest using the live cd.  This should boot you into the live ubuntu, from there you should be able to mount your ubuntu drive and change the permissions back to what they are supposed to be.

GoodLuck!

---

### Post by SlCKB0Y on 2006-11-20
Ok,

To all those people who just love to do everyday things as root, and then say.......but whats wrong with doing it that way. This is whats wrong with doing it that way.

Do this as user, on a folder you have ownership of, then change permissions as user. 

Have fun.

---

### Post by eldaria on 2006-11-20
Well I'm happy I was not looking to remove the folder. ;-)

Funny thing is that I'm looking on setting up a backup, where I will sync all folders to another drive on a rotational backup, the floppy backup was first step just to have a backup of /etc at least.

The script I want to use is the Backup.pl from [www.linux-backup.net](www.linux-backup.net)
I'm just not sure on how to use it.

The only system I have right now is a raid 1, mirror of the most important stuff, but as most people know a mirror is not a backup. :-)

Will try tonight to restore it using the live CD.

---

### Post by bettlebrox on 2006-11-20
It's not just the directory permissions in / that will be messed up, but also just about every file & directory on the system. My advise would be to backup your /home and reinstall the system.

Also, 777 is just dangerous, it can mean that anyone who get's access to your system (included hackers) will be able to create, change, & overwrite any file with those permissions. Your best choice in cases where users need access, is to use 775 and have the users & files in the same group.

At work on an AIX system we had a guy change the ownership of all the files on the sytem to belong to him. He only noticed when the things started to break and then denied responsibility ... 

It took us (not him) about 2 days to get everything fixed. If he had done a chmod 777 we might have been able to recover everything using backup tapes, otherwise we would have just re-installed, which with AIX would probably take a day (unlike most Linuxes).

---

### Post by eldaria on 2006-11-20
Well I saw my misstake rather fast, so it did not get a chance on going that far, only the first folders (/bin /boot /dev /etc /home), and the loose files in Root.
Luckily there are a lot of files in /home so I had time to stop it before it did to much damage. :-)

And reinstalling the system will take too much work, it is a server with lots of customization, I rather go trhogh the folders to set the permissions manually.

So I booted into a rescue system and are now copying the permissions from my desktop.

So far I've done /bin and /boot and working on /home

Is there an way of reconstructing /dev since this is individual per system right?

---

