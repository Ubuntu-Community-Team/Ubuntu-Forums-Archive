---
title: "[SOLVED] backing up to DVD"
date: 2008-06-21
forum: General Help
---

### Post by jerome1232 on 2008-06-21
I'm making the switch back to a 64 bit kernel, and I'm trying to back up my /home before making the switch. currently the root file system is encrypted, I'm not going to have an encrypted file system on this new install.

trying to back up my /home and back it up to DVD I ran this command from /
```
:/$sudo tar -cvjf - /home | sudo split -b 2G - homebck.tar.bz2 
```
which gives me several 2GB chunks of homebck.tar.bz2aa - homebck.tar.bz2ao
now for testing I wanted to recreate my file and make sure the archive was healthy.
```
:/$sudo cat homebck.tar.bz2* > homebck.tar.bz2
bash: homebck.tar.bz2: Permission denied

```

I have no idea why I'm getting permission denied... well I copied them to ~/backup, chowned all the files as me and tried it again.
```
:/$cp homebck.tar.bz2 ~/backup
:/$sudo chown jeremy:jeremy ~/backup/homebck.tar.bz2*
:/$cd ~/backup
:~/backup$cat homebck.tar.bz2* > homebck.tar.bz2
```
gives me a whole and healthy homebck.tar.bz2 file :) now why won't this work from / ?

current permissions in / are as follows:
```
:/$ ls -l
total 30155043
drwxr-xr-x   2 root root       4096 2008-06-10 08:28 bin
drwxr-xr-x   4 root root       3072 2008-06-16 12:56 boot
lrwxrwxrwx   1 root root         11 2008-04-23 05:39 cdrom -> media/cdrom
drwxr-xr-x  15 root root      14340 2008-06-20 21:46 dev
drwxr-xr-x 145 root root      12288 2008-06-20 17:09 etc
drwxr-xr-x   4 root root       4096 2008-05-31 04:31 home
-rw-r--r--   1 root root 2147483648 2008-06-20 20:38 homebck.tar.bz2aa
-rw-r--r--   1 root root 2147483648 2008-06-20 20:56 homebck.tar.bz2ab
-rw-r--r--   1 root root 2147483648 2008-06-20 21:15 homebck.tar.bz2ac
-rw-r--r--   1 root root 2147483648 2008-06-20 21:35 homebck.tar.bz2ad
-rw-r--r--   1 root root 2147483648 2008-06-20 21:53 homebck.tar.bz2ae
-rw-r--r--   1 root root 2147483648 2008-06-20 22:12 homebck.tar.bz2af
-rw-r--r--   1 root root 2147483648 2008-06-20 22:32 homebck.tar.bz2ag
-rw-r--r--   1 root root 2147483648 2008-06-20 22:57 homebck.tar.bz2ah
-rw-r--r--   1 root root 2147483648 2008-06-20 23:27 homebck.tar.bz2ai
-rw-r--r--   1 root root 2147483648 2008-06-20 23:58 homebck.tar.bz2aj
-rw-r--r--   1 root root 2147483648 2008-06-21 00:22 homebck.tar.bz2ak
-rw-r--r--   1 root root 2147483648 2008-06-21 00:45 homebck.tar.bz2al
-rw-r--r--   1 root root 2147483648 2008-06-21 01:06 homebck.tar.bz2am
-rw-r--r--   1 root root 2147483648 2008-06-21 01:26 homebck.tar.bz2an
-rw-r--r--   1 root root  783708356 2008-06-21 01:33 homebck.tar.bz2ao
drwxr-xr-x   2 root root       4096 2008-04-23 05:40 initrd
lrwxrwxrwx   1 root root         33 2008-06-16 12:55 initrd.img -> boot/initrd.img-2.6.24-19-generic
lrwxrwxrwx   1 root root         33 2008-06-15 18:02 initrd.img.old -> boot/initrd.img-2.6.24-18-virtual
drwxr-xr-x  19 root root       4096 2008-06-16 09:01 lib
drwx------   2 root root      16384 2008-04-23 05:39 lost+found
drwxr-xr-x   4 root root       4096 2008-06-20 17:09 media
drwxr-xr-x   2 root root       4096 2008-04-14 22:53 mnt
drwxr-xr-x   2 root root       4096 2008-04-23 05:40 opt
dr-xr-xr-x 175 root root          0 2008-06-20 17:08 proc
drwxr-xr-x  19 root root       4096 2008-06-20 21:04 root
drwxr-xr-x   2 root root      12288 2008-06-16 12:55 sbin
drwxr-xr-x   2 root root       4096 2008-04-23 05:40 srv
drwxr-xr-x  12 root root          0 2008-06-20 17:08 sys
drwxrwxrwt  16 root root       4096 2008-06-21 08:09 tmp
drwxr-xr-x  11 root root       4096 2008-06-19 18:34 usr
drwxr-xr-x  15 root root       4096 2008-04-23 05:59 var
lrwxrwxrwx   1 root root         30 2008-06-16 12:55 vmlinuz -> boot/vmlinuz-2.6.24-19-generic
lrwxrwxrwx   1 root root         30 2008-06-15 18:02 vmlinuz.old -> boot/vmlinuz-2.6.24-18-virtual

```

current permissions in the ~/backup folder are as follows: (I am user jeremy)
```
:~/backup$ ls -l
total 60309884
-rw-r--r-- 1 jeremy jeremy 30848479428 2008-06-21 09:17 homebck.tar.bz2
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:17 homebck.tar.bz2aa
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:19 homebck.tar.bz2ab
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:21 homebck.tar.bz2ac
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:23 homebck.tar.bz2ad
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:25 homebck.tar.bz2ae
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:27 homebck.tar.bz2af
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:28 homebck.tar.bz2ag
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:30 homebck.tar.bz2ah
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:32 homebck.tar.bz2ai
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:34 homebck.tar.bz2aj
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:36 homebck.tar.bz2ak
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:37 homebck.tar.bz2al
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:39 homebck.tar.bz2am
-rw-r--r-- 1 jeremy jeremy  2147483648 2008-06-21 08:41 homebck.tar.bz2an
-rw-r--r-- 1 jeremy jeremy   783708356 2008-06-21 08:42 homebck.tar.bz2ao
-rw------- 1 jeremy jeremy        2080 2008-04-27 10:30 mykey.tar.bz2

```

when I boot into my new install, after copying files to / would this command be proper syntax? 
```
:/$cat homebck.tar.bz2* > - | sudo tar -xvjf -
```
I want to test this usage out without overwriting my home directory, from the man file on tar I'm unsure how to specify and output folder for tar. so how could I run the above command on my current file system and have tar extract to ~/backup to see if all is well.

just being cautious this data contains allot of pictures that if lost, are gone forever. thanks in advance.

---

### Post by jerome1232 on 2008-06-21
Well it looks like this is working for me, it's still going so I'm going to grab a lunch, grow a beard, and maybe it'll be done by then
```
:/~backup$mkdir testing
:/~backup$tar -xvvjf homebck.tar.bz2 -C testing
```

at any rate no matter what I do I can't cat the files in my root folder.
I chowned them, ran cat with and without sudo, is there a usage of cat I'm missing? Also my big do it all in one line failed miserably on my testing copy, told me the archive was corrupt immediately, I think I'm just running the command wrong,

```
:~/backup$ cat homebck.tar.bz2* > - | sudo tar -xvvj -C ~/testing
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors

```

so looks like if nothing else i can copy my seperate files into my own home directory cat them, copy the tar back to root folder and run sudo tar -xvvjf homebck.tar.bz2, just seems like a retarded way to do it

---

### Post by jerome1232 on 2008-06-21
Well the archive does test out perfect, so back to man pages to look at commands, if any1 could give me any insight or suggestions on what I'm doing wrong would be great.

edit:

figured it scrolling down to the end of cat told me to info cat coreutil or something well i checked it out

```
cat homebck.tar.gz2 | sudo tar -xvvjf - -C testing
``` did it

---

