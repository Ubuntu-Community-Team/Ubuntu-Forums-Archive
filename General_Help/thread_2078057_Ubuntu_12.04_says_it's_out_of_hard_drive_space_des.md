---
title: "Ubuntu 12.04 says it's out of hard drive space despite plenty of free gigabytes"
date: 2012-10-30
forum: General Help
---

### Post by vaguely_clear on 2012-10-30
I have a simple headless server running Ubuntu 12.04 (normal desktop, not server) with a very strange problem. I finally [got my vnc working]("http://ubuntuforums.org/showthread.php?t=2072078") following some trouble, which I'm suspecting might be related.

I've attached a screenshot of disk usage analyzer running on the server. As you can see, it thinks my home folder is taking up a ton of space (64 GB), but there's nothing listed in the folder to account for that.

If it helps, I have two hard drives in this machine. One is the main system drive, an 80 GB drive mounted at /. The other is a 1 TB drive mounted at /netdrive. This larger drive is used as an SMB share, which holds various media and backups from other machines. I am not even close to using all of this drive's space, either.

So, what's up? I've already run the following:
```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

But they don't seem to have had any effect.

---

### Post by Elfy on 2012-10-30
Try running this for home 

```
du -h --max-depth=2 /home
```

and this for root

```
sudo du -h --max-depth=1 /
```

---

### Post by vaguely_clear on 2012-10-30
> **Elfy said:**
> Try running this for home 

```
du -h --max-depth=2 /home
```

and this for root

```
sudo du -h --max-depth=1 /
```

I ran them both (see screenshot). They didn't reveal much more regarding file sizes, but there are some errors on the second command. Could that be related?

---

### Post by Elfy on 2012-10-30
>  but there are some errors on the second command. Could that be related?No - that's ok.

Have you emptied trash?

I don't know whether what's in /home for a server install - but is that ALL of the output from the first command?

---

### Post by Wim Sturkenboom on 2012-10-30
Please don't use screenshots. I'm sure that the output of the first command is truncated (only see the last part).

Redirect the output of the first command to a file and attach that instead of the screen dump (or, my preference) paste it here in code tags.
[noparse]```
paste content here
```[/noparse] wil give you
```
paste content here
```


Back to the problem
```

du -h --max-depth=1 /home/ian

```
Look for the largest directory and run
```

du -h --max-depth=1 /home/ian/largest_directory

```
That way you can drill down till you find the culprit.

---

### Post by vaguely_clear on 2012-10-30
Sorry, I should have used code blocks. I wasn't thinking very straight last night.

```

root@ian-Server:~# du -h --max-depth=2 /home

```

returns:

```

4.0K	/home/ian/Public
440K	/home/ian/.macromedia
1020K	/home/ian/.nx
12K	/home/ian/.mission-control
16K	/home/ian/.adobe
4.0K	/home/ian/Ubuntu One
76M	/home/ian/.mozilla
684K	/home/ian/.dvdcss
4.0K	/home/ian/.gvfs
6.4M	/home/ian/.local
40K	/home/ian/.pulse
36K	/home/ian/.pki
2.0M	/home/ian/.gconf
880K	/home/ian/.thumbnails
24K	/home/ian/.dbus
44M	/home/ian/.cache
120K	/home/ian/.kde
4.0K	/home/ian/Downloads
316K	/home/ian/.arista
4.0K	/home/ian/Pictures
19M	/home/ian/.config
908K	/home/ian/.gstreamer-0.10
4.0K	/home/ian/Videos
112K	/home/ian/.compiz-1
4.0K	/home/ian/Desktop
84K	/home/ian/.shotwell
34M	/home/ian/.xbmc
68K	/home/ian/.fontconfig
4.0K	/home/ian/Music
28K	/home/ian/.vnc
4.0K	/home/ian/Documents
1.1M	/home/ian/.cddbslave
4.0K	/home/ian/.gnome2_private
4.0K	/home/ian/Templates
40K	/home/ian/.gnome2
61G	/home/ian
61G	/home
root@ian-Server:~# 

```

and

```

root@ian-Server:~# sudo du -h --max-depth=1 /

```

returns:

```

8.8M	/bin
4.0K	/cdrom
4.0K	/srv
224M	/boot
315G	/netdrive
1.3M	/root
8.6M	/sbin
3.4G	/usr
0	/sys
469M	/var
16K	/lost+found
4.0K	/opt
4.0K	/selinux
4.0K	/media
1.5G	/lib
4.0K	/dev
du: cannot access `/proc/3739/task/3739/fd/4': No such file or directory
du: cannot access `/proc/3739/task/3739/fdinfo/4': No such file or directory
du: cannot access `/proc/3739/fd/4': No such file or directory
du: cannot access `/proc/3739/fdinfo/4': No such file or directory
0	/proc
4.0K	/lib64
4.0K	/mnt
14M	/etc
1016K	/run
8.0K	/tmp
61G	/home
381G	/
root@ian-Server:~# 

```

and

```

root@ian-Server:~# du -h --max-depth=1 /home/ian

```
(Isn't this the same depth as running du -h --max-depth=2 /home?)

returns:

```

4.0K	/home/ian/Public
440K	/home/ian/.macromedia
1020K	/home/ian/.nx
12K	/home/ian/.mission-control
16K	/home/ian/.adobe
4.0K	/home/ian/Ubuntu One
76M	/home/ian/.mozilla
684K	/home/ian/.dvdcss
4.0K	/home/ian/.gvfs
6.4M	/home/ian/.local
40K	/home/ian/.pulse
36K	/home/ian/.pki
2.0M	/home/ian/.gconf
880K	/home/ian/.thumbnails
24K	/home/ian/.dbus
44M	/home/ian/.cache
120K	/home/ian/.kde
4.0K	/home/ian/Downloads
316K	/home/ian/.arista
4.0K	/home/ian/Pictures
19M	/home/ian/.config
908K	/home/ian/.gstreamer-0.10
4.0K	/home/ian/Videos
112K	/home/ian/.compiz-1
4.0K	/home/ian/Desktop
84K	/home/ian/.shotwell
34M	/home/ian/.xbmc
68K	/home/ian/.fontconfig
4.0K	/home/ian/Music
40K	/home/ian/.vnc
4.0K	/home/ian/Documents
1.1M	/home/ian/.cddbslave
4.0K	/home/ian/.gnome2_private
4.0K	/home/ian/Templates
40K	/home/ian/.gnome2
61G	/home/ian
root@ian-Server:~# 

```

and the largest folder here seems to be .mozilla, though it's only 76M.

```

root@ian-Server:~# du -h --max-depth=1 /home/ian/.mozilla

```

returns:

```

4.0K	/home/ian/.mozilla/extensions
76M	/home/ian/.mozilla/firefox
76M	/home/ian/.mozilla
root@ian-Server:~# 

```

---

### Post by vaguely_clear on 2012-10-30
> **Elfy said:**
> No - that's ok.

Have you emptied trash?

I checked the trash in the gui, it was empty. I ran the following anyway just to be sure:

```
rm -rf ~/.local/share/Trash/
```


> I don't know whether what's in /home for a server install - but is that ALL of the output from the first command?

Actually, this is a normal desktop install (I'm not doing any heavy server stuff), and yes, that is actually all of the output; in the screenshot I cut off the initial command and the final prompt. Please see my previous post for a more sane text version, and accept my apologies for posting a screenshot. I was up way too late. :P

---

### Post by vaguely_clear on 2012-10-30
I tried playing with this new (to me) "du" command. I tried this, hoping to identify a folder with gigabytes of data inside:

```
du -h --max-depth=5 /home/ian | grep 'G'
```

Besides sub-folders with G in the name, the following was the only result:

```
61G	/home/ian
```

---

### Post by localhost8080 on 2012-10-30
try this:

```
du -a / | sort -n -r | head -n 10
```

that will give you the ten largest files in your system

[there are more and an explanation here: [http://jonathansblog.co.uk/how-to-find-the-ten-biggest-files-or-directories-in-linux](http://jonathansblog.co.uk/how-to-find-the-ten-biggest-files-or-directories-in-linux) ]


can you also post the results of a 

```
mount
```

with no args, just incase it has multiple small partitions

---

### Post by vaguely_clear on 2012-10-30
> **localhost8080 said:**
> try this:

```
du -a / | sort -n -r | head -n 10
```

that will give you the ten largest files in your system

Unfortunately, this doesn't work. It returns the following:

```
root@ian-Server:~# du -a / | sort -n -r | head -n 10
sort: write failed: /tmp/sorttFkyej: No space left on device
root@ian-Server:~# 

```

It's a vicious circle. :/

> can you also post the results of a 

```
mount
```

with no args, just incase it has multiple small partitions

Sure, here's what it returned:

```
root@ian-Server:~# mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
/dev/sda1 on /netdrive type ext4 (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
root@ian-Server:~# 

```

---

### Post by localhost8080 on 2012-10-30
hmmm, im a bit puzzled :|

you have an 'overflow' for your /tmp - that usually happens when you boot with a full drive, so your system effectively mounts a ram drive for your /tmp

it *could* be that you have loads of things in the dev/sdb1//tmp folder [but then the overflow drive is mounted, so you cant actually see it any more], but the output from the du looks like it is something in the /home folder :|

probably the best thing to do is to boot from a knoppix cd [or an ubuntu install dvd and mount your sdb1 and then do the du commands from there - hopefully that will give you more insight]

---

### Post by Wim Sturkenboom on 2012-10-31
Indeed puzzling. Did you run this in recovery mode? If not, try that (drop to root shell without networking) and run the commands again. You need a monitor and keyboard ;)

---

### Post by HiImTye on 2012-10-31
can you paste the output of
```
df -h
```

---

### Post by vaguely_clear on 2012-10-31
> **localhost8080 said:**
> probably the best thing to do is to boot from a knoppix cd [or an ubuntu install dvd and mount your sdb1 and then do the du commands from there - hopefully that will give you more insight]

> **Wim Sturkenboom said:**
> Indeed puzzling. Did you run this in recovery mode? If not, try that (drop to root shell without networking) and run the commands again. You need a monitor and keyboard ;)

Agreed, this should probably be my next course of action. I'll try recovery mode as soon as I can get a monitor hooked up.

---

### Post by vaguely_clear on 2012-10-31
> **HiImTye said:**
> can you paste the output of
```
df -h
```

This command returns the following:

```
root@ian-Server:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        70G   66G     0 100% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           791M  1.4M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  4.0K  2.0G   1% /run/shm
overflow        1.0M  8.0K 1016K   1% /tmp
/dev/sda1       917G  316G  556G  37% /netdrive
root@ian-Server:~# 

```

---

### Post by Slim Odds on 2012-10-31
> **vaguely_clear said:**
> This command returns the following:

```
root@ian-Server:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
[SIZE=4][COLOR=Red]/dev/sdb1        70G   66G     0 100% /[/COLOR][/SIZE]
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           791M  1.4M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  4.0K  2.0G   1% /run/shm
overflow        1.0M  8.0K 1016K   1% /tmp
/dev/sda1       917G  316G  556G  37% /netdrive
root@ian-Server:~# 

```
Your root partition is full. It doesn't matter how much storage you have on "/netdrive".
Since you don't have a separate /home partition all of your personal data is also using up root partition space. Remove some data from your /home

---

### Post by Elfy on 2012-10-31
> **Slim Odds said:**
> Your root partition is full. It doesn't matter how much storage you have on "/netdrive".
Since you don't have a separate /home partition all of your personal data is also using up root partition space. Remove some data from your /home

The issue here is 'where' this data is - have a look at post #6

I'm still wondering if it's a trash issue - root or user, or perhaps some files in / that shouldn't be there. I know I left some there - they don't show up in a du either for me.

---

### Post by Slim Odds on 2012-10-31
> **Elfy said:**
> The issue here is 'where' this data is - have a look at post #6

I'm still wondering if it's a trash issue - root or user, or perhaps some files in / that shouldn't be there. I know I left some there - they don't show up in a du either for me.
Yes, /home/ian is the big one using 61 GB of the 70 GB of that partition.

---

### Post by localhost8080 on 2012-10-31
> **Slim Odds said:**
> Yes, /home/ian is the big one using 61 GB of the 70 GB of that partition.

exactly, but there isnt anything there.....
well, not that we can obviously see...

---

### Post by Slim Odds on 2012-10-31
> **localhost8080 said:**
> exactly, but there isnt anything there.....
well, not that we can obviously see...

Try using 'find' with the '-size' parameter to look for large files. Something like this:```
find /home/ -size +1G
```That would look for any files greater than 1 GB in size. Use whatever value make sense for you.

You can also try this:```
sudo find /home/ian -maxdepth 1 -type d -name "*" -exec du -sk {} ";" | sort -nr
```

---

### Post by localhost8080 on 2012-10-31
he cant do that, because his drive is full, so the system mounts an overflow /tmp :|

I suggested 

```
du -a / | sort -n -r | head -n 10
```

to get the 10 largest files in the system, but the overflow tmp drive ran out of space!!

I think the best thing is to boot from a knoppix / ubuntu install disc and then try those commands from the recovery shell there - then we can get an idea as to what is munching all the space!

another option is to 

```
mv /home /netdrive && mount /netdrive/home /home
```

since there is plenty space on the netdrive :D

---

### Post by Slim Odds on 2012-10-31
> **localhost8080 said:**
> he cant do that, because his drive is full, so the system mounts an overflow /tmp :|

I suggested 

```
du -a / | sort -n -r | head -n 10
```to get the 10 largest files in the system, but the overflow tmp drive ran out of space!!

I think the best thing is to boot from a knoppix / ubuntu install disc and then try those commands from the recovery shell there - then we can get an idea as to what is munching all the space!

another option is to 

```
mv /home /netdrive && mount /netdrive/home /home
```since there is plenty space on the netdrive :D
He could do it from the Live CD.... just mount / somewhere else.

---

### Post by localhost8080 on 2012-10-31
> **Slim Odds said:**
> He could do it from the Live CD.... just mount / somewhere else.

:guitar:

lol, i didnt even think about that :P

---

### Post by vaguely_clear on 2012-10-31
> **Slim Odds said:**
> Try using 'find' with the '-size' parameter to look for large files. Something like this:```
find /home/ -size +1G
```That would look for any files greater than 1 GB in size. Use whatever value make sense for you.

Ooooh, lookie here:

```
root@ian-Server:~# find /home/ -size +50G
/home/ian/.xsession-errors
root@ian-Server:~# 
```

Slim Odds gets the theoretical gold star for this round. Thanks, Slim Odds!

Two files exist here: /home/ian/.xsession-errors and /home/ian/.xsession-errors.old

Is it safe for me to trash both of these? Curiosity suggests that I should open it, but I'm scared to open a file that is 60GB in size. I can't say I've ever done that before.

---

### Post by Slim Odds on 2012-10-31
> **vaguely_clear said:**
> Ooooh, lookie here:

```
root@ian-Server:~# find /home/ -size +50G
/home/ian/.xsession-errors
root@ian-Server:~# 
```Slim Odds gets the theoretical gold star for this round. Thanks, Slim Odds!

Two files exist here: /home/ian/.xsession-errors and /home/ian/.xsession-errors.old

Is it safe for me to trash both of these? Curiosity suggests that I should open it, but I'm scared to open a file that is 60GB in size. I can't say I've ever done that before.
You might want to move it to your other partition for further evaluation. It there is a persistent problem, it's going to grow again even if you delete it.

Glad that worked out for you!

---

### Post by vaguely_clear on 2012-10-31
Yeah, looks like it's a persistent problem:
[http://ubuntuforums.org/showthread.php?t=1517991&page=4]("http://ubuntuforums.org/showthread.php?t=1517991&page=4")

I followed the very last part of that thread and restarted the machine. Disk Usage Analyzer shows that things appear to be back to normal. Hopefully it won't be a bother anymore.

Thanks everyone for the help! Marking the thread as solved.

---

### Post by localhost8080 on 2012-10-31
glad you got it fixed!

you could just delete the files - if there are enough errors to create a 60GB file, then the files will be re-created instantly once they are deleted, but will be a much more manageable size!!!

---

