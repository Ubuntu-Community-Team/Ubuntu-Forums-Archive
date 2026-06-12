---
title: "Not Quite Understanding Mount Point/Terminal Commands"
date: 2016-11-26
forum: General Help
---

### Post by Quarkrad on 2016-11-26
Just completed a re-install with separate / and /home - / is on sda5 and /home is on sda6.  Gparted, fstab and Disks all confirm this and all agree re the UUID numbers.   I have read that if you want to find out what device a specific file/directory is found on you can use the command df -h /mnt.  When I launch the terminal and enter cd Documents my understanding is that I am looking at /home/Documents.  So ... I would expect that my Documents folder is on sda6 - however, if I launch the terminal and type cd Documents (hit Return) followed by df -h /mnt I get the following:

```
dad@dadubuntu:~$ cd Documents
dad@dadubuntu:~/Documents$ df -h /mnt
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        29G  5.2G   23G  19% /
dad@dadubuntu:~/Documents$ 
```

Is this telling me my Documents folder is on sda5?   What command do I type to confirm that my /home folders are attached to sda6?  Thanks.

---

### Post by oldfred on 2016-11-26
Also see what these say.
mount
cat /etc/fstab

If you created a separate /home but during Something Else install did not choose(change) or add a new /home partition so it is mounted during install, it would not be used. If a second install you must be sure not to check the format box or it will erase all data in /home.

---

### Post by mcduck on 2016-11-26
All "df -h" does is it lists any mounted file systems and the available free space on them. I suppose you *could* use that information to determine which device a specific directory is on, for exmaple if you view a directory in your GUI file manager and check for available space, and then compare it to devices & free space on the listed by "df

In the command you used the "/mnt" part didn't do anything. If you point "df" to a specific *device node* containing a file system, for example /dev/sda1, then it lists information for that file system. Using any other types of paths will just get ignored by "df".


...however in this specific case the "df" command did actually help. Since you can only see one device listed in the output, you know that there is nothing else mounted at the moment, therefore *everything* ins in /dev/sda5. It sounds like you created the partition you wanted to sue as home, but it's not actually mounted at the moment. Check your /etc/fstab file, you will likely need to add it there.

---

### Post by steeldriver on 2016-11-26
The command

```

df -h /mnt

```

will print information about the filesystem containing the directory (or file) /mnt

If you want to see information about the filesystem containing your home directory or Documents directory, you would need to do something like

```

df -h ~/Documents

```

See the df man page:

```

DESCRIPTION
       This  manual  page  documents  the  GNU version of df.  [B]df displays the
       amount of disk space available [COLOR=#0000ff]on the file system [/COLOR][COLOR=#0000ff]containing each  file
       name  argument[/COLOR].[/B]   If  no file name is given, the space available on all
       currently mounted file systems is shown.

```

---

### Post by Quarkrad on 2016-11-26
Thank you all - much appreciated.   I have been reading [http://unix.stackexchange.com/questions/128471/determine-what-device-a-directory-is-located-on](http://unix.stackexchange.com/questions/128471/determine-what-device-a-directory-is-located-on) (although it soon got very heavy) - it looks to me that my /home is indeed on sda6 as it should be (in Something else, during install, I chose sda5 for / and sda6 for /home and formatted both partitions - I have backup of my actual /home so can copy across).  I had the following output:

```
dad@dadubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           788M  9.4M  779M   2% /run
/dev/sda5        29G  5.2G   23G  19% /
tmpfs           3.9G  676K  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda2        96M   49M   48M  51% /boot/efi
/dev/sda6        96G  1.7G   90G   2% /mnt
tmpfs           788M   48K  788M   1% /run/user/1000
/dev/sdc1       1.9T  1.2T  644G  66% /media/dad/backup
dad@dadubuntu:~$ df -h /mnt
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        96G  1.7G   90G   2% /mnt
dad@dadubuntu:~$ 

```

What I did not appreciate was that when you have a separate /home (partition) it is in the mnt folder under route (guessing the correct terminology is /home is mounted under /mnt - not sure).

Also:

dad@dadubuntu:~$ df -h ~/Documents
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        96G  1.7G   90G   2% /home

---

### Post by oldfred on 2016-11-26
You do not have a separate /home, but a /home mounted under documents in your /home inside Documents. It looks more like a link.

I do use links, but avoid any system names to prevent confusion. If you have/had a backup of /home is that what you are really seening in /Documents?

---

