---
title: "Root out of space"
date: 2013-08-15
forum: General Help
---

### Post by 7YdPAF3 on 2013-08-15
During a regular update I ran out of space on /
The problem is that I can't remove any packages or do autoremove.

```
root@laptop:/# df -hl
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       8,2G  7,8G     0 100% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            3,9G  4,0K  3,9G   1% /dev
tmpfs           3,9G   96K  3,9G   1% /tmp
tmpfs           790M  900K  789M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,9G  1,3M  3,9G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda6        20G   17G  1,9G  90% /home
```

I can't remove any packages as this message appears:

```
root@laptop:/# apt-get remove dosbox 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libwebkitgtk-1.0-0 : Depends: libjavascriptcoregtk-1.0-0 (= 2.0.3-1ubuntu1~build1) but 2.0.4-1ubuntu1~raring2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

If I do as instructed:

```
root@laptop:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libwebkitgtk-1.0-0
The following packages will be upgraded:
  libwebkitgtk-1.0-0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
30 not fully installed or removed.
Need to get 0 B/49,0 MB of archives.
After this operation, 627 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 214282 files and directories currently installed.)
Preparing to replace libwebkitgtk-1.0-0 2.0.3-1ubuntu1~build1 (using .../libwebkitgtk-1.0-0_2.0.4-1ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libwebkitgtk-1.0-0 ...
dpkg: error processing /var/cache/apt/archives/libwebkitgtk-1.0-0_2.0.4-1ubuntu1~raring2_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/libwebkitgtk-1.0.so.0.18.9' to '/usr/lib/libwebkitgtk-1.0.so.0.18.9.dpkg-new': failed to write (No space left on device)
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libwebkitgtk-1.0-0_2.0.4-1ubuntu1~raring2_amd64.deb
```
 
I tried doing 'apt-get autoclean' and 'apt-get clean', but they did not free any space. Autoremove gives this: 
 
```
root@laptop:/# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libwebkitgtk-1.0-0 : Depends: libjavascriptcoregtk-1.0-0 (= 2.0.3-1ubuntu1~build1) but 2.0.4-1ubuntu1~raring2 is installed
E: Unmet dependencies. Try using -f.
```

I tried already removing wallpapers and other stuff I found from /, but none helped. Is there a way to abort this update process or clear the apt-get so that I could remove unneeded packages?

I don't have old kernels but I do have some programs that I would like to remove. If I could that is.

---

### Post by varunendra on 2013-08-15
[s]Do you have older kernels that you can remove? Check with -
```
dpkg -l | grep linux-image
```[/s]

**EDIT:** Ugh! Noticed the last line in your post after posting mine :|

**PS:**
Oh, and Welcome to the forums ! :)

---

### Post by plucky on 2013-08-15
```
sudo apt-get clean
``` will clear out the .deb packages  in the /var/apt/archives/ directory and might give you enough space to run ```
sudo apt-get install -f
```

> I tried doing 'apt-get autoclean' and 'apt-get clean', but they did not free any space.


Whoops missed this. Have you tried emptying root Thrash?


> /dev/sda5       8,2G  7,8G     0 100% /

That seems a lot of space used in / .

My / system partition uses 4.4G.

Search for out of control log files or system backups.

Good Luck

---

### Post by 7YdPAF3 on 2013-08-15
/root is only 3.2M and no .Trash there

However /usr is 6.9G, it's contents:

```
root@laptop:/usr# ls -1 | xargs du -sh
308M    bin
1,8M    games
139M    include
3,4G    lib
4,0K    lib32
1,2G    local
20M     sbin
1,9G    share
107M    src
```

Obviously the /usr/lib is one of the largest directories. I don't see how I could manually delete any of this stuff to free some space. I have Netbeans and other programming stuff installed that have probably filled up the lib directory. I was unable to uninstall any more Netbeans plugins.

---

### Post by 7YdPAF3 on 2013-08-15
I was able to uninstall Netbeans as it was not installed via apt-get. /usr/local/netbeans-x.x.x had uninstall.sh that freed enough space on / for me to do 'apt-get -f install'. Now I can remove programs again.

This was really weird situation, which was hard to get out of. Luckily I had one large program (Netbeans) that I was able to uninstall. I don't know what else I could have done. The /usr/lib folder is still 3,3G and I don't quite understand why. I think it's easiest just to re-install Ubuntu, again. :(

I'll mark this as solved.

---

### Post by varunendra on 2013-08-15
> **7YdPAF3 said:**
> I think it's easiest just to re-install Ubuntu, again. :(

Unfortunately, I have to concur.

And obviously, make the root bigger now that you have a practical experience of the space usage with the programs you are going to install.
Good luck with the next installation.

---

