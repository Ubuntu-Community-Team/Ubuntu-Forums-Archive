---
title: "Not enough disk space error message"
date: 2020-06-05
forum: General Help
---

### Post by Jonners59 on 2020-06-05
Dear all
I am getting a message thrown up when trying to use apps saying I do not have enough memory.  I get it in Libre and Evolution, and I am sure others are going to start doing the same.  The apps will not open properly now.  It is crazy as there is plenty of space for ubuntu and I store almost nothing in HOME.  According to gParted the directory is 97.73GiB and I have used 92.77GiB, leaving only 4.96GiB. USR and / are on a diffecent Harddrive and partitions and they have / = 45.4GiB and used 13.69GiB and USR is 40.75GiB and used 28.6GiB.

```
df -h
Filesystem                Size  Used Avail Use% Mounted on
udev                      7.8G     0  7.8G   0% /dev
tmpfs                     1.6G  3.4M  1.6G   1% /run
/dev/sdb2                  45G   13G   30G  31% /
/dev/sdb3                  40G   29G   10G  74% /usr
tmpfs                     7.9G  146M  7.7G   2% /dev/shm
tmpfs                     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/loop1                155M  155M     0 100% /snap/chromium/1143
/dev/loop0                 94M   94M     0 100% /snap/core/9066
/dev/loop4                 98M   98M     0 100% /snap/core/9289
/dev/loop5                 55M   55M     0 100% /snap/core18/1754
/dev/loop12               202M  202M     0 100% /snap/pixbuf-desktop/6
/dev/loop8                273M  273M     0 100% /snap/freecad/8
/dev/loop11                63M   63M     0 100% /snap/gtk-common-themes/1506
/dev/loop3                157M  157M     0 100% /snap/chromium/1165
/dev/loop6                 55M   55M     0 100% /snap/core18/1705
/dev/loop2                 77M   77M     0 100% /snap/clari3d-free-64/1
/dev/loop14               109M  109M     0 100% /snap/odrive-unofficial/2
/dev/loop10                61M   61M     0 100% /snap/magic-device-tool/299
/dev/loop9                191M  191M     0 100% /snap/kicad-snap/2
/dev/loop7                111M  111M     0 100% /snap/dino/1
/dev/loop17                38M   38M     0 100% /snap/thelounge/188
/dev/loop13                55M   55M     0 100% /snap/gtk-common-themes/1502
/dev/loop16               117M  117M     0 100% /snap/test-d5262bf/6
/dev/loop18               106M  106M     0 100% /snap/plexmediaserver/98
/dev/loop21                38M   38M     0 100% /snap/thelounge/191
/dev/loop19                12M   12M     0 100% /snap/shout/9
/dev/loop23               156M  156M     0 100% /snap/wavebox/193
/dev/loop20               156M  156M     0 100% /snap/wavebox/192
/dev/loop22               240M  240M     0 100% /snap/wps-office/1
/dev/loop15               106M  106M     0 100% /snap/plexmediaserver/95
/dev/sda1                  27G   54M   26G   1% /media/Backup
/dev/sdc1                 229G   60M  217G   1% /media/External
/dev/sda5                  96G   91G   58M 100% /home
/dev/sda3                 331G   76G  255G  23% /media/Documents
/dev/sdb1                 147G  131G   16G  90% /media/WindowsOS
//192.168.1.50/Documents  3.6T  804G  2.8T  22% /media/Server
tmpfs                     1.6G   32K  1.6G   1% /run/user/1000

```

[HTML]free -m
              total        used        free      shared  buff/cache   available
Mem:          15995        7009         302         227        8684        8428
Swap:         10144          35       10109
[/HTML] 

[HTML]vmstat -s
     16379308 K total memory
      7229516 K used memory
      8683964 K active memory
      4248012 K inactive memory
       226776 K free memory
      2084200 K buffer memory
      6838816 K swap cache
     10388476 K total swap
        36364 K used swap
     10352112 K free swap
       623628 non-nice user cpu ticks
        65317 nice user cpu ticks
       297909 system cpu ticks
      5179798 idle cpu ticks
       347702 IO-wait cpu ticks
            0 IRQ cpu ticks
       107504 softirq cpu ticks
            0 stolen cpu ticks
      7181569 pages paged in
     36545033 pages paged out
          221 pages swapped in
         8988 pages swapped out
     37862946 interrupts
    420283187 CPU context switches
   1591337180 boot time
        23615 forks[/HTML]
How do I correct this and how do I clean up.  I use```
 apt-get clean
``` and ```
apt-get autoremove
``` regularly

---

### Post by ActionParsnip on 2020-06-05
When do you see the message? At boot? When you run a particular command?......

---

### Post by Jonners59 on 2020-06-05
[ATTACH=CONFIG]286098[/ATTACH]

> **ActionParsnip said:**
> When do you see the message? At boot? When you run a particular command?......

Hiya, was just uploading a screenshot.  When working.  Evolution has started showing errors when trying to reply to messages and when in Lebra and typing it suddenly says there is an error, with the pop up I just shown and I can not use it anymore.

I note that I have a tiny amount of space left on HOME, but I store so little there, maybe a few GiB.  All my docs are stored on either a remote machine or in Documents which is on a separate partition.

---

### Post by TheFu on 2020-06-05
```
/dev/sda5                  96G   91G   **58M** 100% /home
```
Your HOME is full - that's a storage issue.  Some programs, like audacity will usually need lots of storage somewhere for work files. Only 58MB is free based on the post above.

Out of "Memory" usually points at RAM and virtual memory being unavailable.

I'd clean up the !!!!!91GB!!!!! in your HOME.  Use **du** to find the files.  There are lots of methods for that, but usually it is just a few large cached videos left hidden. Two commands:

```
$ du -sh ~/[0-Z]* |sort -h
$ du -sh ~/.[0-Z]* |sort -h
```


Also, if you don't want to have all that useless crap in the df output, use 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
That will only show real storage that matters. not the fake stuff.

---

### Post by Yellow Pasque on 2020-06-05
First off, your thread title is inaccurate. You are running out of disk space (not memory).

> I note that I have a tiny amount of space left on HOME, but I store so little there, maybe a few GiB.
Then the answer is to find out what's using the disk space. The GNOME version (and possibly others) of Ubuntu comes with a tool that makes it easy to see where your disk space is being used:
```
baobab
```

---

### Post by Jonners59 on 2020-06-05
> **TheFu said:**
> ```
/dev/sda5                  96G   91G   **58M** 100% /home
```
Your HOME is full - that's a storage issue.  Some programs, like audacity will usually need lots of storage somewhere for work files. Only 58MB is free based on the post above.

Out of "Memory" usually points at RAM and virtual memory being unavailable.

I'd clean up the !!!!!91GB!!!!! in your HOME.  Use **du** to find the files.  There are lots of methods for that, but usually it is just a few large cached videos left hidden. Two commands:

```
$ du -sh ~/[0-Z]* |sort -h
$ du -sh ~/[.]*[0-Z]* |sort -h
```


Also, if you don't want to have all that useless crap in the df output, use 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
That will only show real storage that matters. not the fake stuff.

Thank you...

So ```
0    /home/baroni/PlayOnLinux's virtual drives
4.0K    /home/baroni/GuiConfigTest.xml
4.0K    /home/baroni/VirtualBox VMs
20K    /home/baroni/2019-03-19-Scene.mrml
28K    /home/baroni/GNUstep
84K    /home/baroni/SlicerDICOMDatabase
6.4M    /home/baroni/MRHead.nrrd
751M    /home/baroni/Dropbox
1.7G    /home/baroni/Android
12G    /home/baroni/Desktop
```

Which is about 14GiB!

```
du -sh ~/[.]*[0-Z]* |sort -h
du: cannot access '/home/baroni/[.]*[0-Z]*': No such file or directory
```

```
df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem               Type     Size  Used Avail Use% Mounted on
/dev/sdb2                ext4      45G   14G   30G  32% /
/dev/sdb3                ext4      40G   29G   10G  74% /usr
/dev/sda1                ext4      27G   54M   26G   1% /media/Backup
/dev/sdc1                ext4     229G   60M  217G   1% /media/External
/dev/sda5                ext4      96G   89G  2.8G  98% /home
/dev/sda3                fuseblk  331G   72G  259G  22% /media/Documents
/dev/sdb1                fuseblk  147G  131G   16G  90% /media/WindowsOS
//192.168.1.50/Documents cifs     3.6T  804G  2.8T  22% /media/Server
```

Which doesn't help either?  PS:  I got the /home down a tad by deleting stuff in .conf

I still can't see why it is so full.

---

### Post by ActionParsnip on 2020-06-05
Try:

```

cd $HOME
du -ash *
du -hs .[^.]*

```

Will show hidden folders too. Probably web cache or some junk like that (or virtualbox). Let's see

---

### Post by Jonners59 on 2020-06-05
> **Yellow Pasque said:**
> First off, your thread title is inaccurate. You are running out of disk space (not memory).


Then the answer is to find out what's using the disk space. The GNOME version (and possibly others) of Ubuntu comes with a tool that makes it easy to see where your disk space is being used:
```
baobab
```

Yes, sorry, misleading.  You are absolutely correct.  Can it be changed?

Typical mine didn't have baobab, so just installed it.  Here are the results:

OK, drilling down it seems we have 
baroni/.confg/VirtualBox/Windows10 = 29.4GB  So I deleted that.
Desktop/Photos = 12Gb to file which I moved, though it isn't a huge amount, but every little byte helps.
baroni/.cache/evolution = 9.8Gb of which 8.5Gb comes from one account.  11.5Gb for the whole of cache.  I guess there is little I can do with that, unless I could delete cache, but would that upset Evolution?

And that's it.  Should work for now, but if there is more I could or should do would be appreciated.  Thank you

---

### Post by TheFu on 2020-06-05
Windows10 was a virtual machine. You've deleted it now.  Those VMs can get away from us.  You can put VMs from virtualbox almost anywhere you have storage, best if it is RAID1 or RAID10 to avoid corruption should a disk fail while any VM is running.  The location used is just the default for virtualbox.

12G of photos is pretty large unless you are really into photos. I have 80G from the family photos beginning in the 1930s, but most are mine since digital photograph became easy in 2006.

Evolution keeping 9.8G!  That just seems odd. Whether you can delete it or not depends on the email server(s) and how you get messages. Do you use POP3 or IMAP?  If pop3, then that area is likely the only copy.  More than 4G seems highly excessive to me, but my email server blocks large attachments to prevent email being used as a catch-all storage location. Email stores have been highly corruptable ... basically ... always. Get important information out of email storage ASAP - or at least split it up annually.  Then the corruption is limited to a single year.  I've been annually archiving mail since 1996 when I lost everything.  MS-Outlook was known to have an issue with PST files over 1GB in size. They way to solve that was to have annual archives.  [https://blog.jdpfu.com/2013/01/01/annual-digital-cleanup](https://blog.jdpfu.com/2013/01/01/annual-digital-cleanup)

There are tools that will monitor storage and alert you if it gets too small.  Also, did you notice how the storage shows 100% when 91GB was used but their was 96GB the size?  Most Unix file systems reserve 5% of the storage for use by root.  Root's HOME is usually tiny and in /root/, so it wouldn't be in /home when it is mounted under a different partition like you have.  It is reasonable to change that from a 5% reserved storage to 0% for non-OS partitions. After all, why waste 5% that nobody will ever use?  For ext4, the command is **tune2fs**, but there are some options to look up. Again, only do this for data partitions, not OS. Look for the "reserved" stuff.

It wouldn't hurt to look for huge files on every partition once a week.
```
find /home /var -type f -size +3G
```
Tweak the locations and size for your needs.  Automatically run it however you like.  I'd use **cron** since the output gets emailed to my email address, but that has to be setup via an MTA.  Also, **logwatch** is a daily system problem notification tool about unusual stuff, including storage. I have logwatch email a summary daily on each of my machines to my main administrative account.

---

### Post by TheFu on 2020-06-05
> **Jonners59 said:**
>  
```
du -sh ~/[.]*[0-Z]* |sort -h
du: cannot access '/home/baroni/[.]*[0-Z]*': No such file or directory
```


Sorry, thought I'd fixed it.  The command is: 
```
du -sh ~/.[0-Z]* |sort -h

```

That's a [ZERO-ZEE], which gets all numbers, lowercase and uppercase when bash is the shell. Very handy. The .[^.] by 
ActionParsnip is more inclusive for everything else, especially for non-English setups.  The ".[^.]" pattern says that it must begin with a "dot", but cannot have a "dot" immediately after. That is cleaner/better and I'll try remember to use it going forward.

> **Jonners59 said:**
>  
```
df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem               Type     Size  Used Avail Use% Mounted on
/dev/sdb2                ext4      45G   14G   30G  32% /
/dev/sdb3                ext4      40G   29G   10G  74% /usr
/dev/sda1                ext4      27G   54M   26G   1% /media/Backup
/dev/sdc1                ext4     229G   60M  217G   1% /media/External
/dev/sda5                ext4      96G   89G  2.8G  98% /home
/dev/sda3                fuseblk  331G   72G  259G  22% /media/Documents
/dev/sdb1                fuseblk  147G  131G   16G  90% /media/WindowsOS
//192.168.1.50/Documents cifs     3.6T  804G  2.8T  22% /media/Server
```

Which doesn't help either?  PS:  I got the /home down a tad by deleting stuff in .conf

I still can't see why it is so full.

The df command is just to remove all the cruft with non-real file systems and 25+ loop lines which don't reflect what is actually on SSD, NFS, spinning rust storage.  It is simply cleaner output AND shows the file system type used, which is almost much more useful than not having it. 

The tool that Yellow Pasque's recommended is probably more what most end-users on a desktop need. Most of my work is on servers, so I almost always want a shell-based solution. Servers don't have GUIs. Plus, if I provide the correct command + options, it is easier for all.  If the command is correct. Sorry about that. ;)

Love the multi-post wisdom here. Thanks folks!

---

### Post by Yellow Pasque on 2020-06-05
> **Jonners59 said:**
> Can (thread title) be changed?

I can't remember if you can do it or forum staff has to do it. Maybe if you edit the first post.

[QUOTE=TheFu]The tool that Yellow Pasque's recommended is probably more what most end-users on a desktop need.[/QUOTE]

Yeah, it's great, except when the user runs out of space on /usr and can't install it :\
Kubuntu/Lubuntu users might prefer filelight as it uses Qt5.
Also, for terminal, (or when there is very limited space), there is ncdu to simplify du commands and hunt for space hog files.

---

### Post by DuckHook on 2020-06-05
> **Yellow Pasque said:**
> I can't remember if you can do it or forum staff has to do it. Maybe if you edit the first post&#8230;
Titles changed.

Forum members can edit titles of their own posts, but not those of others.

---

### Post by Jonners59 on 2020-06-11
THANK YOU!!!!!!!!!!!  Happy bunny now.  Was a silly mistake.
Just about to put another up.  Hope they are as easy to resolve.  Take care.

> **TheFu said:**
> Sorry, thought I'd fixed it.  The command is: 
```
du -sh ~/.[0-Z]* |sort -h

```

That's a [ZERO-ZEE], which gets all numbers, lowercase and uppercase when bash is the shell. Very handy. The .[^.] by 
ActionParsnip is more inclusive for everything else, especially for non-English setups.  The ".[^.]" pattern says that it must begin with a "dot", but cannot have a "dot" immediately after. That is cleaner/better and I'll try remember to use it going forward.



The df command is just to remove all the cruft with non-real file systems and 25+ loop lines which don't reflect what is actually on SSD, NFS, spinning rust storage.  It is simply cleaner output AND shows the file system type used, which is almost much more useful than not having it. 

The tool that Yellow Pasque's recommended is probably more what most end-users on a desktop need. Most of my work is on servers, so I almost always want a shell-based solution. Servers don't have GUIs. Plus, if I provide the correct command + options, it is easier for all.  If the command is correct. Sorry about that. ;)

Love the multi-post wisdom here. Thanks, folks!

THANK YOU TheFu and Yellow Pasque
For some reason I am NOT getting notifications, so missed both your replies.  Very much appreciated.  I seem to be running fine now, though two new issues have cropped up since managing to get my PC to upgrade to 20.04, but that is for another blog.  I shall keep this in case it happens again or similar on this or another machine.  Some of your additional info seems I will need to take stock and think about  :-)  Re the VM's yes, on my server - it is actually just a PC, I need the GUI - I do just that.  I have a spare HD that I have all the VM partitions, and run a special Debian to run my IPPBX (3CX).  Works really well.


Thank you both and anyone else that contributed and helped me.  You are great.  :-)  Now for my next trick.

---

