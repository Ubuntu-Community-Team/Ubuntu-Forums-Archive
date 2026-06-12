---
title: "autoremove hosed my system. Please help me recover..."
date: 2013-06-22
forum: General Help
---

### Post by nashibuntu on 2013-06-22
I'm on Raring, 64 bit. I noticed that when installing/updating, apt-get kept prompting me that I could do an autoremove. So, finally I did... but then suddenly basic commands like ls stopped working. I was forced to restart, but I can't boot up anymore. I get past the grub bootloader, but then it just stops with the caps-lock key flashing. So, I tried booting into recovery mode (using various kernels) - but I end up in kernel panic part way through the boot process. So, I have installed Raring to a USB key, and can access all my partitions and data (phew...)

I'd be grateful if someone could help me recover. Presumably there was some inconsistency/bug in apt which caused it too remove a core package that it shouldn't have.

My apt history.log says:

```
Start-Date: 2013-06-22  23:31:30
Commandline: apt-get autoremove
Remove: lib64readline6:i386 (6.2-9ubuntu1), libpython3-stdlib:i386 (3.3.1-0ubuntu1), libpython2.7-stdlib:i386 (2.7.4-2ubuntu3), libpython2.7:i386 (2.7.4-2ubuntu3), lib64ncurses5:i386 (5.9-10ubuntu4), libpython3.3-minimal:i386 (3.3.1-1ubuntu5), libreadline6:i386 (6.2-9ubuntu1), libc6-amd64:i386 (2.17-0ubuntu5), libpython2.7-minimal:i386 (2.7.4-2ubuntu3), lib64tinfo5:i386 (5.9-10ubuntu4), libpython3.3-stdlib:i386 (3.3.1-1ubuntu5)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2013-06-22  23:31:45
```

I found some [instructions for dealing with an update failure]("https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure") in the community documentation, but when I try to chroot my root partition in step 4 I get

```
sudo chroot /media/ubuntu/5c759a9b-9b46-4a85-8266-dcbbf2fe9185/
chroot: failed to run command ‘/bin/bash’: No such file or directory
```

so it appears that apt hosed my chroot or something like that. I also note that the following three links are broken in the /media/ubuntu/5c759a9b-9b46-4a85-8266-dcbbf2fe9185/lib64 directory:

```
$ ls -ltr
total 0
lrwxrwxrwx 1 root root 20 May  1 21:50 ld-lsb-x86-64.so.3 -> ld-linux-x86-64.so.2
lrwxrwxrwx 1 root root 20 May  1 21:50 ld-lsb-x86-64.so.2 -> ld-linux-x86-64.so.2
lrwxrwxrwx 1 root root 10 Jun 15 23:29 ld-linux-x86-64.so.2 -> ld-2.17.so
```

Any ideas about the best way to recover? Thank you!

---

### Post by nashibuntu on 2013-06-22
For info, here is the end of my dpkg.log, describing what happened during the autoremove:
```
2013-06-22 23:31:30 startup packages remove
2013-06-22 23:31:30 status installed lib64ncurses5:i386 5.9-10ubuntu4
2013-06-22 23:31:37 remove lib64ncurses5:i386 5.9-10ubuntu4 <none>
2013-06-22 23:31:37 status half-configured lib64ncurses5:i386 5.9-10ubuntu4
2013-06-22 23:31:37 status half-installed lib64ncurses5:i386 5.9-10ubuntu4
2013-06-22 23:31:37 status triggers-pending libc-bin:amd64 2.17-0ubuntu5
2013-06-22 23:31:37 status config-files lib64ncurses5:i386 5.9-10ubuntu4
2013-06-22 23:31:37 status config-files lib64ncurses5:i386 5.9-10ubuntu4
2013-06-22 23:31:37 status installed lib64readline6:i386 6.2-9ubuntu1
2013-06-22 23:31:38 remove lib64readline6:i386 6.2-9ubuntu1 <none>
2013-06-22 23:31:38 status half-configured lib64readline6:i386 6.2-9ubuntu1
2013-06-22 23:31:38 status half-installed lib64readline6:i386 6.2-9ubuntu1
2013-06-22 23:31:38 status config-files lib64readline6:i386 6.2-9ubuntu1
2013-06-22 23:31:38 status config-files lib64readline6:i386 6.2-9ubuntu1
2013-06-22 23:31:38 status installed lib64tinfo5:i386 5.9-10ubuntu4
2013-06-22 23:31:38 remove lib64tinfo5:i386 5.9-10ubuntu4 <none>
2013-06-22 23:31:38 status half-configured lib64tinfo5:i386 5.9-10ubuntu4
2013-06-22 23:31:38 status half-installed lib64tinfo5:i386 5.9-10ubuntu4
2013-06-22 23:31:39 status config-files lib64tinfo5:i386 5.9-10ubuntu4
2013-06-22 23:31:39 status config-files lib64tinfo5:i386 5.9-10ubuntu4
2013-06-22 23:31:39 status installed libc6-amd64:i386 2.17-0ubuntu5
2013-06-22 23:31:39 remove libc6-amd64:i386 2.17-0ubuntu5 <none>
2013-06-22 23:31:39 status half-configured libc6-amd64:i386 2.17-0ubuntu5
2013-06-22 23:31:39 status half-installed libc6-amd64:i386 2.17-0ubuntu5
2013-06-22 23:31:39 status installed libpython2.7:i386 2.7.4-2ubuntu3
2013-06-22 23:31:40 remove libpython2.7:i386 2.7.4-2ubuntu3 <none>
2013-06-22 23:31:40 status half-configured libpython2.7:i386 2.7.4-2ubuntu3
2013-06-22 23:31:40 status half-installed libpython2.7:i386 2.7.4-2ubuntu3
2013-06-22 23:31:40 status installed libpython2.7-stdlib:i386 2.7.4-2ubuntu3
2013-06-22 23:31:40 remove libpython2.7-stdlib:i386 2.7.4-2ubuntu3 <none>
2013-06-22 23:31:40 status half-configured libpython2.7-stdlib:i386 2.7.4-2ubuntu3
2013-06-22 23:31:40 status installed libpython2.7-stdlib:i386 2.7.4-2ubuntu3
2013-06-22 23:31:40 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:40 status installed libpython3-stdlib:i386 3.3.1-0ubuntu1
2013-06-22 23:31:40 remove libpython3-stdlib:i386 3.3.1-0ubuntu1 <none>
2013-06-22 23:31:40 status half-configured libpython3-stdlib:i386 3.3.1-0ubuntu1
2013-06-22 23:31:40 status half-installed libpython3-stdlib:i386 3.3.1-0ubuntu1
2013-06-22 23:31:41 status config-files libpython3-stdlib:i386 3.3.1-0ubuntu1
2013-06-22 23:31:41 status config-files libpython3-stdlib:i386 3.3.1-0ubuntu1
2013-06-22 23:31:41 status config-files libpython3-stdlib:i386 3.3.1-0ubuntu1
2013-06-22 23:31:41 status not-installed libpython3-stdlib:i386 <none>
2013-06-22 23:31:41 status installed libpython3.3-stdlib:i386 3.3.1-1ubuntu5
2013-06-22 23:31:41 remove libpython3.3-stdlib:i386 3.3.1-1ubuntu5 <none>
2013-06-22 23:31:41 status half-configured libpython3.3-stdlib:i386 3.3.1-1ubuntu5
2013-06-22 23:31:41 status installed libpython3.3-stdlib:i386 3.3.1-1ubuntu5
2013-06-22 23:31:41 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:41 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:41 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:41 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:41 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:41 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:41 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:42 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:42 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:42 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:42 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:42 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:42 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:42 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:42 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:42 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:42 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:42 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:42 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:42 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:42 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:43 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:43 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:43 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:43 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:43 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:43 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:43 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:43 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:43 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:43 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:43 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:44 status installed libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:44 remove libpython2.7-minimal:i386 2.7.4-2ubuntu3 <none>
2013-06-22 23:31:44 status half-configured libpython2.7-minimal:i386 2.7.4-2ubuntu3
2013-06-22 23:31:44 status installed libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:44 remove libpython3.3-minimal:i386 3.3.1-1ubuntu5 <none>
2013-06-22 23:31:44 status half-configured libpython3.3-minimal:i386 3.3.1-1ubuntu5
2013-06-22 23:31:44 status installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:44 remove libreadline6:i386 6.2-9ubuntu1 <none>
2013-06-22 23:31:44 status half-configured libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:44 status half-installed libreadline6:i386 6.2-9ubuntu1
2013-06-22 23:31:45 trigproc libc-bin:amd64 2.17-0ubuntu5 <none>
2013-06-22 23:31:45 status half-configured libc-bin:amd64 2.17-0ubuntu5
```

---

### Post by fantab on 2013-06-22
If you can still boot Ubuntu then run:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If there are any errors then post the output of above command here.

---

### Post by nashibuntu on 2013-06-23
Thanks fantab. To be clear, I have not been able to reboot my system. I have been able to boot a Live install via USB. However, I have not been able to chroot into the broken system. I have mounted all the partitions of the broken system at /mnt/temp/ like so:

```
/dev/sda5 on /mnt/temp type ext4 (rw)
/dev/sda1 on /mnt/temp/boot type ext4 (rw)
/dev on /mnt/temp/dev type none (rw,bind)
/dev/pts on /mnt/temp/dev/pts type none (rw,bind)
/proc on /mnt/temp/proc type none (rw,bind)
/sys on /mnt/temp/sys type none (rw,bind)
/dev/sda9 on /mnt/temp/home type ext4 (rw)
/dev/sda8 on /mnt/temp/tmp type ext4 (rw)
/dev/sda6 on /mnt/temp/usr type ext4 (rw)
```

but when I do

```
sudo chroot /mnt/temp
```

I get

```
chroot: failed to run command ‘/bin/bash’: No such file or directory
```

So, it appears that the autoremove that hosed my system must have uninstalled something vital for chroot, or must have broken some links vital for chroot, like the ones in the lib64 directory I mentioned in my original post. Since I can't run chroot, I cannot run apt-get on the broken system.

[I did read on stack overflow]("http://stackoverflow.com/questions/3954584/running-apt-get-for-another-partition-directory") that it could be possible to run apt-get on a different directory without requiring chroot. So I tried

```
sudo apt-get -o Dir=/mnt/temp/ update
```

but it still appears to be running apt-get on the live installation, rather than the broken system. So, I'm still stuck and looking for help!

---

### Post by nashibuntu on 2013-06-23
I have just found that someone else has also encountered [apparently the same (?) catastrophic bug on Raring]("http://ubuntuforums.org/showthread.php?t=2120448") (and has been trying similar solutions) and has reported it on the forums. I'll try the same solution and see what happens... (although I'd rather fix it without just blindly copying files over from the Live installation like suggested, so if anyone has any clues about how to get apt-get or chroot working, I'd be grateful...)

---

### Post by dino99 on 2013-06-23
I suppose you are a dist-upgrade fan since a while; but not a fan for cleaning the room, right ?
Maybe the best you can do is a fresh re-install (and drop all the borked mess).

[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by nashibuntu on 2013-06-23
> **dino99 said:**
> I suppose you are a dist-upgrade fan since a while; **but not a fan for cleaning the room**, right ?
(My emphasis.) Sorry dino99, I genuinely don't understand what you mean about not being a fan of 'cleaning the room'. Is that sarcasm or some useful advice about using Ubuntu that's lost on me? Please can you explain? Cheers.

---

### Post by nashibuntu on 2013-06-23
Okay. I'm making some progress I think. I fixed the broken link in /mnt/temp/lib64

```
cd /mnt/temp/lib64
sudo ln -s ../lib/x86_64-linux-gnu/ld-2.17.so ld-linux-x86-64.so.2
```

and set-up my resolv.conf to allow internet access from a chroot environment

```
cd /mnt/temp/etc
sudo mv resolv.conf resolv.conf.backup
sudo cp /etc/resolv.conf ./
```

... and now I can chroot again:

```
sudo chroot /mnt/temp
```

I manually downloaded [the raring amd64 libc6 package]("http://packages.ubuntu.com/raring/amd64/libc6/download") and installed it from chroot via

```
dpkg -i libc6_2.17-0ubuntu5_amd64.deb
(Reading database ... 320195 files and directories currently installed.)
Preparing to replace libc6:amd64 2.17-0ubuntu5 (using .../libc6_2.17-0ubuntu5_amd64.deb) ...
Unpacking replacement libc6:amd64 ...
Setting up libc6:amd64 (2.17-0ubuntu5) ...
```

Seems okay. apt-get update works fine. apt-get dist-upgrade gives me...

```

root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
```

So, doing what it tells me, I get...
```
root@ubuntu:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpython2.7-minimal:i386 libpython2.7-stdlib:i386 libpython3.3-minimal:i386 libpython3.3-stdlib:i386 libreadline6:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libc6-amd64:i386 libpython2.7:i386
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 134 kB of archives.
After this operation, 14.1 MB disk space will be freed.
Do you want to continue [Y/n]?
```

Do I really want to continue? Isn't it the removal of these packages which hosed my system last time? It looks like it's trying to remove the i386 versions of the packages - which is perhaps okay because I should have amd64 versions anyway?

So, I'm asking for advice on how to proceed to recover from this (without having to reinstall from scratch, if possible). Thank you.

---

### Post by fantab on 2013-06-23
See what happens when you continue.

---

### Post by nashibuntu on 2013-06-23
Okay. Here we go...

```
root@ubuntu:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpython2.7-minimal:i386 libpython2.7-stdlib:i386 libpython3.3-minimal:i386 libpython3.3-stdlib:i386 libreadline6:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libc6-amd64:i386 libpython2.7:i386
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 134 kB of archives.
After this operation, 14.1 MB disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/ raring/main libreadline6 i386 6.2-9ubuntu1 [134 kB]
Fetched 134 kB in 0s (305 kB/s)  
(Reading database ... 320194 files and directories currently installed.)
Removing libc6-amd64 ...
Removing libpython2.7:i386 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Setting up libpython3.3-minimal:i386 (3.3.1-1ubuntu5) ...
dpkg: error processing libreadline6:i386 (--configure):
 package libreadline6:i386 is not ready for configuration
 cannot configure (current status `half-installed')
Setting up libpython2.7-minimal:i386 (2.7.4-2ubuntu3) ...
Errors were encountered while processing:
 libreadline6:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dino99 on 2013-06-23
> **nashibuntu said:**
> (My emphasis.) Sorry dino99, I genuinely don't understand what you mean about not being a fan of 'cleaning the room'. Is that sarcasm or some useful advice about using Ubuntu that's lost on me? Please can you explain? Cheers.

indeed, no sarcasm(s) here; im only saying that your favorite ubuntu will thanks you if you pay attention to it: by "cleaning" i mean using : clean/autoclean/autoremove/gtkorphan/bleachbit, and avoid package(s) conflict(s) when upgrading (partial updates) or untrusted ppa(s), ...

---

### Post by nashibuntu on 2013-06-23
Some extra info in case it is of use: I was thinking back over what could have caused this in the first place. The first time I remember seeing the autoremove messages was just after I had uninstalled the libgv-php5 library (because I wasn't using it, yet it contained a symbol that was conflicting with the name of a function within some PHP software I was trying to run, provoking 'this is already defined' errors.) I suspect that there is [something wrong with the dependencies of this package]("http://packages.ubuntu.com/raring/libgv-php5") which has screwed up my system. I do note that it says it depends on both the i386 and amd64 versions of libc. I wonder whether re-installing the libgv-php5 package might help.

---

### Post by nashibuntu on 2013-06-23
> **dino99 said:**
> indeed, no sarcasm(s) here; im only saying that your favorite ubuntu will thanks you if you pay attention to it: by "cleaning" i mean using : clean/autoclean/autoremove/gtkorphan/bleachbit, and avoid package(s) conflict(s) when upgrading (partial updates) or untrusted ppa(s), ...

Ah, I see.
[LIST]
[*]I tried both apt-get clean and apt-get autoclean, then apt-get update ... it made no difference.
[*]apt-get autoremove was what provoked the problem in the first place.
[*]I don't know what the gtkorphan and bleachbit things are or it they would be useful in this instance. I'll investigate.
[/LIST]
Cheers.

---

### Post by nashibuntu on 2013-06-23
> **nashibuntu said:**
> I wonder whether re-installing the libgv-php5 package might help.

Answering my own question. Nope, this doesn't help at the moment:

```
root@ubuntu:/# apt-get install libgv-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpython2.7-stdlib:i386 : Depends: libreadline6:i386 (>= 6.0) but it is not going to be installed
 libpython3.3-stdlib:i386 : Depends: libreadline6:i386 (>= 6.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So, doing what it says just yields...

```
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpython2.7-minimal:i386 libpython2.7-stdlib:i386 libpython3.3-minimal:i386
  libpython3.3-stdlib:i386 libreadline6:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/134 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libreadline6:i386 (--configure):
 package libreadline6:i386 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libreadline6:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What to do now? This [guidance on how to resolve unmet dependencies]("http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies") suggests doing dpkg --configure -a then apt-get -f install again... but that doesn't change anything unfortunately.

---

### Post by nashibuntu on 2013-06-23
Okay... I think I am getting somewhere! I tried

```
root@ubuntu:/# apt-get -f install --reinstall libreadline6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpython2.7-minimal:i386 libpython2.7-stdlib:i386 libpython3.3-minimal:i386 libpython3.3-stdlib:i386 libreadline6:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 140 kB/274 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/](http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/) raring/main libreadline6 amd64 6.2-9ubuntu1 [140 kB]
Fetched 140 kB in 0s (517 kB/s)  
Selecting previously unselected package libreadline6:i386.
(Reading database ... 320195 files and directories currently installed.)
Preparing to replace libreadline6:i386 6.2-9ubuntu1 (using .../libreadline6_6.2-9ubuntu1_i386.deb) ...
Unpacking replacement libreadline6:i386 ...
Preparing to replace libreadline6:amd64 6.2-9ubuntu1 (using .../libreadline6_6.2-9ubuntu1_amd64.deb) ...
Unpacking replacement libreadline6:amd64 ...
Setting up libreadline6:amd64 (6.2-9ubuntu1) ...
Setting up libreadline6:i386 (6.2-9ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

... which seemed to sort our the problems with the readline6 package. Then

```
root@ubuntu:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpython2.7-minimal:i386 libpython2.7-stdlib:i386 libpython3.3-minimal:i386 libpython3.3-stdlib:i386 libreadline6:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Finally, following the instructions it gave me...

```
root@ubuntu:/# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libpython2.7-minimal:i386 libpython2.7-stdlib:i386 libpython3.3-minimal:i386 libpython3.3-stdlib:i386 libreadline6:i386
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 22.9 MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 320198 files and directories currently installed.)
Removing libpython2.7-stdlib:i386 ...
Removing libpython2.7-minimal:i386 ...
Removing libpython3.3-stdlib:i386 ...
Removing libpython3.3-minimal:i386 ...
Removing libreadline6:i386 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

apt-get update then upgrade then dist-upgrade tell me that "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded." - so I think the problem is resolved. Now just to reboot and see what happens...

---

### Post by nashibuntu on 2013-06-23
I can confirm that after restoring my resolv.conf, unmounting all the partitions I had mounted, and rebooting, my system seems to be running smoothly, so this problem has been solved.

However, it is not right that by following an instruction to autoremove some packages your system becomes unbootable. I think that the root cause was uninstallation of the libgv-php5 package, so I'll try to report a bug against that.

Update: [Bug reported on launchpad on graphviz package]("https://bugs.launchpad.net/ubuntu/+source/graphviz/+bug/1193858")

---

