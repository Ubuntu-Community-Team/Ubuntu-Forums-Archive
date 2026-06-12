---
title: "Deleted /var/backups"
date: 2016-09-15
forum: General Help
---

### Post by ivanali on 2016-09-15
Hello.

After installing some applications using apt-get, my terminal started complaining with this message: bash: cannot create temp file for here-document: No space left on device

After attempting to get rid of this (also because Firefox wouldn't let me download any files because there was "no free space available") somewhere in this forum I read that files in /var/backups might be causing this. I was so carefree I decided to delete the files inside this folder assuming they were just a backup of my original files. Unfortunately, it looks like I have lost all my files in /home (I have /home mounted somewhere else as well).

Is there any way to recover my files?

Thank you,
Iván

---

### Post by DuckHook on 2016-09-15
Welcome to the forums, ivanali.

Although it is not a good idea to delete system files when you aren't sure what they are for, deleting files in /var/backups alone will not destroy your /home directory.

[LIST=1]
[*]Do you have backups of your data?
[*]Do you have access to another Linux computer?
[*]Can you use the computer at all (for example, are you posting from that computer now)?
[*]How do you know that /home is gone?
[/LIST]
If /home is truly gone, then you had to have deleted a lot more than just the /var/backups directory. If so, then make sure that you don't use the computer at all. Instead, follow the instructions in the following link to recover your data:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

In particular, pay attention to utilities like photorec.

From your description, it sounds like you just ran out of disk space. The key to solving such a problem is not to delete system files, but to offload data files or get a larger HDD. If you are actually currently using the computer, post back the results of:```
df -h
```This will show the amount of free space still available on your HDD.

---

### Post by ivanali on 2016-09-15
Hi DuckHook.

I am currently using that computer, and posting from it as well. 
I did copy most of my personal files in my computer to an external HDD about 5 months ago.
I do have access to another computer running Ubuntu 15.10
When using ls at ~, no folders that used to be there as being shown.
My computer still complains about no free disk space.

Here's the output of the df -h command:

```
ivan@Ivan:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           771M  9.5M  761M   2% /run
/dev/sda8        40G   38G     0 100% /
tmpfs           3.8G  8.8M  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.8G     0  3.8G   0% /sys/fs/cgroup
/dev/sda10      346G  4.8G  324G   2% /home
/dev/sda1       496M   53M  444M  11% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           771M   68K  771M   1% /run/user/1000


```

Thank you,
Iván

---

### Post by DuckHook on 2016-09-15
Your root directory (/) is completely full. But your /home directory is fine (and safe). You probably cannot look up ~ because your / is full. Try instead:```
ls -la /home
``` System shows that you installed your / directory on sda8 with 40 GB of space, which should be ample, unless you have tons of apps loaded. Please post results of:```
du -h --max-depth=1 | sort -hr
```

---

### Post by DuckHook on 2016-09-15
Rats. Forgot to instruct you to navigate to / first. Therefore:```
cd /
``````
sudo du -h --max-depth=1 | sort -hr
```

---

### Post by ivanali on 2016-09-15
```
ivan@Ivan:/$ sudo du -h --max-depth=1 | sort -hr
[sudo] password for ivan: 
du: cannot access &#8216;./proc/3670/task/3670/fd/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/3670/task/3670/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/3670/fd/3&#8217;: No such file or directory
du: cannot access &#8216;./proc/3670/fdinfo/3&#8217;: No such file or directory
du: cannot access &#8216;./run/user/1000/gvfs&#8217;: Permission denied
22G    .
12G    ./usr
4.7G    ./home
4.0G    ./var
573M    ./lib
436M    ./opt
162M    ./boot
17M    ./etc
14M    ./bin
13M    ./sbin
9.6M    ./run
4.0M    ./lib32
3.1M    ./root
300K    ./dev
52K    ./tmp
44K    ./media
16K    ./lost+found
4.0K    ./srv
4.0K    ./mnt
4.0K    ./lib64
4.0K    ./cdrom
0    ./sys
0    ./proc

```
When using ls -la /home, I can see the hidden files I previously had, but Documents, Pictures, Videos and another visible folder that was there are gone (Desktop and Documents were created again, empty)

Iván

---

### Post by DuckHook on 2016-09-15
While in / do:```
ls -laF
```

---

### Post by ivanali on 2016-09-15
output:
```
ivan@Ivan:/$ ls -laF
total 120
drwxr-xr-x  24 root root  4096 sep 15 15:34 ./
drwxr-xr-x  24 root root  4096 sep 15 15:34 ../
drwxr-xr-x   2 root root  4096 may 13 11:35 bin/
drwxr-xr-x   4 root root  4096 ago 16 15:33 boot/
drwxrwxr-x   2 root root  4096 dic  3  2015 cdrom/
drwxr-xr-x  19 root root  4600 sep 15 18:45 dev/
drwxr-xr-x 162 root root 12288 sep 15 15:34 etc/
drwxr-xr-x   4 root root  4096 dic  3  2015 home/
lrwxrwxrwx   1 root root    32 jul 15 11:31 initrd.img -> boot/initrd.img-4.2.0-42-generic
lrwxrwxrwx   1 root root    32 jul  6 10:22 initrd.img.old -> boot/initrd.img-4.2.0-41-generic
drwxr-xr-x  25 root root  4096 jun 18 15:35 lib/
drwxr-xr-x   2 root root  4096 jun 18 15:35 lib32/
drwxr-xr-x   2 root root  4096 jun 18 15:35 lib64/
drwx------   2 root root 16384 dic  3  2015 lost+found/
drwxr-xr-x  12 root root  4096 may 12 16:44 media/
drwxr-xr-x   2 root root  4096 oct 19  2015 mnt/
drwxr-xr-x   7 root root  4096 abr 14 13:01 opt/
dr-xr-xr-x 228 root root     0 sep 15 13:45 proc/
drwx------   8 root root  4096 jul 18 10:56 root/
drwxr-xr-x  30 root root   900 sep 15 20:22 run/
drwxr-xr-x   2 root root 12288 jun 18 15:36 sbin/
drwxr-xr-x   2 root root  4096 oct 21  2015 srv/
dr-xr-xr-x  13 root root     0 sep 15 13:45 sys/
drwxrwxrwt  10 root root  4096 sep 15 20:17 tmp/
drwxr-xr-x  14 root root  4096 ago 12 09:18 usr/
drwxr-xr-x  12 root root  4096 sep 15 18:42 var/
lrwxrwxrwx   1 root root    29 jul 15 11:31 vmlinuz -> boot/vmlinuz-4.2.0-42-generic
lrwxrwxrwx   1 root root    29 jul  6 10:22 vmlinuz.old -> boot/vmlinuz-4.2.0-41-generic
-rw-rw-r--   1 ivan ivan  8891 ene 25  2016 z.sh
```

---

### Post by DuckHook on 2016-09-15
> **ivanali said:**
> When using ls -la /home, I can see the hidden files I previously had, but Documents, Pictures, Videos and another visible folder that was there are gone (Desktop and Documents were created again, empty)This is very puzzling. One command (df) shows your root file system at 38 GB and therefore all free space used up. The other (du) shows only 22GB so should still have space.

At this point, before doing anything further, it is important to preserve whatever info we can of your /home.

Stop using this computer. You may have to take out the HDD, attach it to your spare computer and, using that OS (so you don't potentially corrupt this HDD further), do diagnostics on the HDD. It's too bad that your other box is still running 15.10 which is now out of support. But let's deal with one problem at a time.

---

### Post by DuckHook on 2016-09-15
Also, try bringing your current box to a full shutdown, wait two minutes, then reboot. See if your /home folders come back up.

---

### Post by steeldriver on 2016-09-15
Perhaps /dev/sda10 has been unmounted from /home for some period - and the "missing" files are what is taking up the extra space on / ?

---

### Post by ivanali on 2016-09-15
I have another partition running Windows 10.

Would it be safe to create, from Windows 10, a new partition with Ubuntu 16.04 and then do diagnostics?

Iván

---

### Post by DuckHook on 2016-09-15
> **ivanali said:**
> I have another partition running Windows 10.

Would it be safe to create, from Windows 10, a new partition with Ubuntu 16.04 and then do diagnostics?

IvánBest not to create anything further on this HDD. If things are truly missing, you don't want to overwrite files.

> **steeldriver said:**
> Perhaps /dev/sda10 has been unmounted from /home for some period - and the "missing" files are what is taking up the extra space on / ?Ah. I see. That is impressive indirect thinking.

@OP What steeldriver is suggesting is that at some point, your /home was not hived off to another partition, but simply under / in sda8. There, it accumulated files and filled up some of sda8. When you subsequently offloaded /home to sda10, the old files became orphaned but continue to take up space on the partition, reducing its capacity from 40 GB to 22 GB. Does this description of events ring any bells?

---

### Post by ivanali on 2016-09-15
Actually, I followed this guide just after the backup from 5 months ago: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
That was because my partition was almost full, and I somehow wanted to extend it. That was the safest solution I found so I followed it.

I have been noticing that the old partition has been accumulating files (and that would explain why Ubuntu started to complain about lack of free space, even though I had a bigger partition for /home

Any clues?

---

### Post by DuckHook on 2016-09-15
Aha!

So you did move /home only in the recent past. I suspect that steeldriver nailed it. If his surmise proves to be the solution, you owe him a cookie.

Let's see if you have orphaned /home files. To do so, we must unhitch your new /home directory from / temporarily. Do you have a LiveUSB/DVD that you can use to boot up with if things go badly?

---

### Post by ivanali on 2016-09-15
I am getting a LiveUSB ready.

What steps do I follow to unhitch my /home directory?

Ivàn

---

### Post by DuckHook on 2016-09-15
[LIST=1]
[*]Make sure the LiveUSB actually works (prove that you can boot with it).
[*]Create a directory in /mnt for your /home that is currently in sda10:```
sudo mkdir /mnt/home_temp
```
[*]Open your fstab file with:```
sudo nano /etc/fstab
```
[*]Find the line that says:```
UUID=8fd03e8a-28dd-4e31-9423-62ea729d1baf /home           ext4    defaults        0       2
```&#8230;and change:```
/home
```&#8230;to```
/mnt/home_temp
```Note: your UUID will differ from the one in my example because I just used one of mine.
[*]Save the file and exit nano. It is very important that this is done correctly, so:```
cat /etc/fstab
```&#8230;and make sure everything is correct.
[*]Reboot.
[/LIST]


If reboot is successful, you should be using your old /home of five months ago (which I suspect was never deleted) and your new /home will be found in /mnt/home_temp.

Let's see if you can proceed to that point before further instructions.

If you cannot reboot, use the LiveUSB to get back to this thread for further instructions. DO NOT boot into Windows to try to fix things. Windows text editors will muck up your Linux system files and really get you into a mess.

---

### Post by DuckHook on 2016-09-15
I should note that steps 2 to 6 are done using your regular OS; *not* the LiveUSB. That is only for safety if you need to recover.

I am closing up shop here soon, so cannot take you through the next steps tonight. Before leaving, I will try to outline the remaining steps.

---

### Post by DuckHook on 2016-09-16
[LIST=1]
[*]If steeldriver's conjecture is accurate and you now have both a /home and a /mnt/home_temp, do:```
df -h
``````
sudo blkid
```
[*]Find the UUID for sda8 (the partition of your root directory). Write the UUID down.
[*]These next two steps may be unnecessary because you have stated that you made a backup of your data five months ago for your original /home move. However, if you want to wear both belts and suspenders, it's not a bad idea to backup now as follows:
[*]Create a new directory under ```
/mnt/home_temp
```…say, ```
/mnt/home_temp/old_home
```
[*]For safety, copy all files from /home into /mnt/home_temp/old_home. You can do so through the command line or even by using Nautilus. Open two Nautilus instances: one for /home and another for /mnt/home_temp/old_home and just drag and drop. Satisfy yourself that both directories are identical and complete with all subdirectories and files present.
[*]Now you can reverse the changes made to fstab.```
sudo nano /etc/fstab
```Change:```
/mnt/home_temp
```…back to just:```
/home
```
[*]Again, assuming our conjecture is accurate, this next step is the one you missed on your initial efforts and is the cause of your present pain: you must *delete* all the data in your old /home. This part is critical so an explanation is in order. If you fail to delete the data in your old /home, it does not just go away when your new /home is mapped over it. Instead, it exists in a sort of data limbo, taking up HDD space but completely inaccessible: neither visible nor deletable after you reboot. However, it is impossible to delete a directory like /home that is always currently in use and that loads automatically at boot. So getting rid of it involves that LiveUSB that you created.
[*]Boot into your LiveUSB. Bring up a terminal and do:```
blkid
```If nothing shows, use *sudo*. In a LiveUSB environment, the password for sudo is blank (just press <Enter>).
[*]Using the UUID you wrote down earlier, find the matching device name. *It may not be sda8* in the LiveUSB session. This is why we have to go to the trouble of matching the UUIDs and not just go by device names. Note this device name (if it is still sda8, then great).
[*]Open a terminal and do:```
sudo mount -t ext4 /dev/sd?? /mnt
```…where sd?? is replaced by the device number you just noted. If successful, you have just mounted the root partition of your OS onto the /mnt directory of your LiveUSB session. To test, do:```
ls -laF /mnt
```You should see your Ubuntu root directory structure.
[*]These next instructions *must* be done accurately. A mistake could wipe out your OS. Change your working directory to the old /home directory with:```
cd /mnt/home
```Double check that you are in the right directory with:```
pwd
```It should return:```
/mnt/home
```*Make sure it is **not** just*:```
/mnt
```To triple-check, do```
ls -laF
```…it should only show your /home data, not the root directory tree.
[*]Now for the nuclear bomb of commands… take a deep breath and:```
sudo rm -rf *.*
```This will delete everything (and I mean everything) in the current working directory. It will not stop to ask if you are sure, it will not pause for second thoughts, it will not even alert you as to its progress: it just nukes everything without cracking a smile.
[*]Congratulations. You have emptied your old /home directory. You can now shutdown, take out the LiveUSB stick and boot back up into your Ubuntu OS. Because you carefully followed every step and changed the fstab file in step 6 already, you should have your new /home mapped over your old (and now empty) one.
[/LIST]


Do a final:```
df -h
``` and it should show your root partition with 22GB of usage and 18GB more to go.

As for restoring the /var/backups files that you deleted, you can start a separate thread. I'm too tired to go into that tonight.

---

### Post by ivanali on 2016-09-16
Hi.

It worked as expected. I have the very same files from 5 months ago. What's next?
EDIT: I didn't see your last post. I will follow them. I will be posting my results asap.

Thank you

---

### Post by DuckHook on 2016-09-16
Signing off for the night. I won't be following up for another 18 hrs, but since we are now on the right track, the last set of instructions should get you straightened out.

For what it's worth, my instructions may be rather extensive, but they are just mechanical procedures that most anyone can figure out with enough time. It was steeldriver's insight that was truly the solution to this. Amazing intuition. Were it not for his uncanny insight, we might have spent days chasing ghosts and not solving anything. If you ever run into him, buy the man a beer.

---

### Post by ivanali on 2016-09-16
Hey!

I followed the steps, but the output to df -h shows nothing changed at all.

```
bash: cannot create temp file for here-document: No space left on device
ivan@Ivan:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           771M  9.6M  761M   2% /run
/dev/sda8        40G   39G     0 100% /
tmpfs           3.8G  164K  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.8G     0  3.8G   0% /sys/fs/cgroup
/dev/sdb1       4.1G  1.4G  2.7G  35% /media/usb0
/dev/sdc1        30G  172M   30G   1% /media/usb1
/dev/sda10      346G  4.8G  324G   2% /home
/dev/sda1       496M   53M  444M  11% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           771M  4.0K  771M   1% /run/user/119
tmpfs           771M   60K  771M   1% /run/user/1000


```

I suspect it had to do with the rm command. After executing ls, the ivan folder inside home at /mnt was still there, with all of its files and directories. Should I try ```
sudo rm -rf *
``` inside /mnt/home instead? (a bit scared to try not without your approval just yet)

Iván

---

### Post by DuckHook on 2016-09-16
> **ivanali said:**
> Hey!

I followed the steps, but the output to df -h shows nothing changed at all.

```
bash: cannot create temp file for here-document: No space left on device
ivan@Ivan:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           771M  9.6M  761M   2% /run
/dev/sda8        40G   39G     0 100% /
tmpfs           3.8G  164K  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.8G     0  3.8G   0% /sys/fs/cgroup
/dev/sdb1       4.1G  1.4G  2.7G  35% /media/usb0
/dev/sdc1        30G  172M   30G   1% /media/usb1
/dev/sda10      346G  4.8G  324G   2% /home
/dev/sda1       496M   53M  444M  11% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           771M  4.0K  771M   1% /run/user/119
tmpfs           771M   60K  771M   1% /run/user/1000


```

I suspect it had to do with the rm command. After executing ls, the ivan folder inside home at /mnt was still there, with all of its files and directories. Should I try ```
sudo rm -rf *
``` inside /mnt/home instead? (a bit scared to try not without your approval just yet)

Iván yes try that. The /home directory must be empty.

---

### Post by ivanali on 2016-09-16
Now it's gone

```
ivan@Ivan:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           771M  9.6M  761M   2% /run
/dev/sda8        40G   19G   19G  51% /
tmpfs           3.8G  164K  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.8G     0  3.8G   0% /sys/fs/cgroup
/dev/sdb1       4.1G  1.4G  2.7G  35% /media/usb0
/dev/sda10      346G  4.8G  324G   2% /home
/dev/sdc1        30G  172M   30G   1% /media/usb1
/dev/sda1       496M   53M  444M  11% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           771M  4.0K  771M   1% /run/user/119
tmpfs           771M   72K  771M   1% /run/user/1000


```

Thank you so far. What's next on restoring the files inside /var/backups?

Iván

---

### Post by DuckHook on 2016-09-16
> **ivanali said:**
> …What's next on restoring the files inside /var/backups?

> **DuckHook said:**
> …follow the instructions in the following link to recover your data:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

In particular, pay attention to utilities like photorec.

> **ivanali said:**
> …the output to df -h shows nothing changed at all.

```
bash: cannot create temp file for here-document: **No space left on device**…
```Frankly, I have no expectation that you can recover anything at all. When your partition filled up due to continuing usage of the OS, I have no doubt that it overwrote the files you deleted. They are permanently gone now. You can try the recovery methods in my link, but do not expect success.

At this point, if your installation continues to function, you should just assume that the files in that directory are not critical to system operations and just wave them goodbye.

Other posters may have a strategy for recovering those files, but I don't have any further ideas.

---

