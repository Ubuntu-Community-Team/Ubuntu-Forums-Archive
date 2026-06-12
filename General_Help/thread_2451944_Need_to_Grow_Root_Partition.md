---
title: "Need to Grow Root Partition"
date: 2020-10-13
forum: General Help
---

### Post by jbh54enwiler on 2020-10-13
I have a dual-booted system running Kubuntu 20.04 and Windows 10.  My partitioning scheme is sloppy, to say the least.  Anyway, I tried to install application updates through Discover last week, and it said it couldn't due to "no disk space."  I looked on my hard drive and saw that my root partition, which I had allocated 20.49 GiB, according to KDE Partition Manager.  I had not anticipated that my root partition would be holding my application data, I always thought those files went into the /home directory.  Anyway, because of this, I need to make my root partition bigger.  

I have already made room by shrinking my Windows partition, but I still can't make the root partition for Kubuntu bigger because the Windows Recovery partition is standing between the free space I created and my root partition.  So I need move the Windows recovery partition up on my partition list, but I can't figure out how to get the recovery partition to move.  It won't let me drag and drop, so I'm guessing that it's more complicated than that.  Here's a screenshot of my partitions. 

 I was asked on another thread I was commenting about this issue in to give the output of a command.  This is what I got when I put it into Konsole. ```
jbh@jbh-HP-Pavilion-Laptop-14-ce2xxx:~$ uname -a; dpkg -l | grep linux-imageLinux jbh-HP-Pavilion-Laptop-14-ce2xxx 5.4.0-48-generic #52-Ubuntu SMP Thu Sep 10 10:58:49 UTC 2020 x86_64 x86_64 x86_64 GNU
/Linux
rc  linux-image-5.4.0-26-generic                  5.4.0-26.30                                 amd64        Signed kernel ima
ge generic
rc  linux-image-5.4.0-29-generic                  5.4.0-29.33                                 amd64        Signed kernel ima
ge generic
ii  linux-image-5.4.0-31-generic                  5.4.0-31.35                                 amd64        Signed kernel ima
ge generic
ii  linux-image-5.4.0-33-generic                  5.4.0-33.37                                 amd64        Signed kernel ima
ge generic
ii  linux-image-5.4.0-37-generic                  5.4.0-37.41                                 amd64        Signed kernel ima
ge generic
ii  linux-image-5.4.0-39-generic                  5.4.0-39.43                                 amd64        Signed kernel ima
ge generic
ii  linux-image-5.4.0-40-generic                  5.4.0-40.44                                 amd64        Signed kernel ima
ge generic
ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                                 amd64        Signed kernel ima
ge generic
ii  linux-image-5.4.0-45-generic                  5.4.0-45.49                                 amd64        Signed kernel ima
ge generic
ii  linux-image-5.4.0-47-generic                  5.4.0-47.51                                 amd64        Signed kernel ima
ge generic
ii  linux-image-5.4.0-48-generic                  5.4.0-48.52                                 amd64        Signed kernel ima
ge generic
ii  linux-image-generic                           5.4.0.48.51                                 amd64        Generic Linux ker
nel image

 
```

---

### Post by adelpozoman-f on 2020-10-13
You cant resize the partition while the system is on, so you need to start a kubuntu/ubuntu usb distro, then use g parted to resize linuxswap from 14 to 10 (should still be enough) and then grow /dev/sda5.
Remember to shrink linuxswap moving the left barrier, so you have new space at the left for /dev/sda5.

---

### Post by jbh54enwiler on 2020-10-13
That fixed it, thanks!  Though if my root partition keeps filling up I suppose I could get rid of the swap entirely, create a new swap in the blank space I have elsewhere, and make the root bigger that way?  Would that work?

---

### Post by ajgreeny on 2020-10-13
It may be a lot easier to remove some of your installed kernels of which you have a very long list.
```
ii  linux-image-5.4.0-31-generic 
ii  linux-image-5.4.0-33-generic 
ii  linux-image-5.4.0-37-generic
ii  linux-image-5.4.0-39-generic
ii  linux-image-5.4.0-40-generic
ii  linux-image-5.4.0-42-generic
ii  linux-image-5.4.0-45-generic
ii  linux-image-5.4.0-47-generic
ii  linux-image-5.4.0-48-generic
ii  linux-image-generic 
```
I don't think the usual way to remove these with ***sudo apt autoremove*** will work as there will be insufficient headroom so we may have to get down and dirty with ***dpkg -P*** commands which can work with very little space compared with apt.

First we need to know what kernel you are currently using, which should be 5.4.0-48.  Command uname -a will show us.
Assuming I'm correct let's start with command```
sudo dpkg -P linux-image{,-extra}-5.4.0-{33,37,39,40,42,45}-generic
```and see if that gets rid of the ones you don't need any more.
If you see any errors come back and show us and we can edit that command accordingly.

EDIT:
Too slow, but I still believe you should rid yourself of all those unneeded kernels which will be an ongoing problem if you leave them.
You may now, having made changes to your partitions, have room to run command ```
sudo apt autoremove -s
```just to show you what the command will remove when run without the **-s** switch, (simulate).
If it removes only what needs to be removed run it again without the -s switch.

---

### Post by jbh54enwiler on 2020-10-13
I got this output when I ran the first command:

```
[FONT=monospace][COLOR=#54FF54]**jbh@jbh-HP-Pavilion-Laptop-14-ce2xxx**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo dpkg -P linux-image{,-extra}-5.4.0-{33,37,39,40,42,45}-generic[/COLOR]
[sudo] password for jbh:  
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent removal of linux-image-5.4.0-33-generic:[/COLOR]
 linux-modules-extra-5.4.0-33-generic depends on linux-image-5.4.0-33-generic | linux-image-unsigned-5.4.0-33-generic; howev
er:
  Package linux-image-5.4.0-33-generic is to be removed.
  Package linux-image-unsigned-5.4.0-33-generic is not installed.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package linux-image-5.4.0-33-generic (--purge):[/COLOR]
 dependency problems - not removing
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent removal of linux-image-5.4.0-37-generic:[/COLOR]
 linux-modules-extra-5.4.0-37-generic depends on linux-image-5.4.0-37-generic | linux-image-unsigned-5.4.0-37-generic; howev
er:
  Package linux-image-5.4.0-37-generic is to be removed.
  Package linux-image-unsigned-5.4.0-37-generic is not installed.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package linux-image-5.4.0-37-generic (--purge):[/COLOR]
 dependency problems - not removing
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent removal of linux-image-5.4.0-39-generic:[/COLOR]
 linux-modules-extra-5.4.0-39-generic depends on linux-image-5.4.0-39-generic | linux-image-unsigned-5.4.0-39-generic; howev
er:
  Package linux-image-5.4.0-39-generic is to be removed.
  Package linux-image-unsigned-5.4.0-39-generic is not installed.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package linux-image-5.4.0-39-generic (--purge):[/COLOR]
 dependency problems - not removing
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent removal of linux-image-5.4.0-40-generic:[/COLOR]
 linux-modules-extra-5.4.0-40-generic depends on linux-image-5.4.0-40-generic | linux-image-unsigned-5.4.0-40-generic; howev
er:
  Package linux-image-5.4.0-40-generic is to be removed.
  Package linux-image-unsigned-5.4.0-40-generic is not installed.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package linux-image-5.4.0-40-generic (--purge):[/COLOR]
 dependency problems - not removing
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent removal of linux-image-5.4.0-42-generic:[/COLOR]
 linux-modules-extra-5.4.0-42-generic depends on linux-image-5.4.0-42-generic | linux-image-unsigned-5.4.0-42-generic; howev
er:
  Package linux-image-5.4.0-42-generic is to be removed.
  Package linux-image-unsigned-5.4.0-42-generic is not installed.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package linux-image-5.4.0-42-generic (--purge):[/COLOR]
 dependency problems - not removing
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent removal of linux-image-5.4.0-45-generic:[/COLOR]
 linux-modules-extra-5.4.0-45-generic depends on linux-image-5.4.0-45-generic | linux-image-unsigned-5.4.0-45-generic; howev
er:
  Package linux-image-5.4.0-45-generic is to be removed.
  Package linux-image-unsigned-5.4.0-45-generic is not installed.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package linux-image-5.4.0-45-generic (--purge):[/COLOR]
 dependency problems - not removing
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#FFFF54]**warning:**[/COLOR][COLOR=#000000] ignoring request to remove linux-image-extra-5.4.0-33-generic which isn't installed[/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#FFFF54]**warning:**[/COLOR][COLOR=#000000] ignoring request to remove linux-image-extra-5.4.0-37-generic which isn't installed[/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#FFFF54]**warning:**[/COLOR][COLOR=#000000] ignoring request to remove linux-image-extra-5.4.0-39-generic which isn't installed[/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#FFFF54]**warning:**[/COLOR][COLOR=#000000] ignoring request to remove linux-image-extra-5.4.0-40-generic which isn't installed[/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#FFFF54]**warning:**[/COLOR][COLOR=#000000] ignoring request to remove linux-image-extra-5.4.0-42-generic which isn't installed[/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#FFFF54]**warning:**[/COLOR][COLOR=#000000] ignoring request to remove linux-image-extra-5.4.0-45-generic which isn't installed[/COLOR]
Errors were encountered while processing:
 linux-image-5.4.0-33-generic
 linux-image-5.4.0-37-generic
 linux-image-5.4.0-39-generic
 linux-image-5.4.0-40-generic
 linux-image-5.4.0-42-generic
 linux-image-5.4.0-45-generic

[/FONT]
```

I also got this output when I ran autoremove:

```
[FONT=monospace][COLOR=#54FF54]**jbh@jbh-HP-Pavilion-Laptop-14-ce2xxx**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo apt autoremove -s[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be REMOVED:
  libllvm9 qtgstreamer-plugins-qt5
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Remv libllvm9 [1:9.0.1-12]
Remv qtgstreamer-plugins-qt5 [1.2.0-5]

[/FONT]
```

---

### Post by HermanAB on 2020-10-14
There are other ways to make space:
You can make a swap file and put it in the /home partition, then reclaim all /swap for /.
You can move the /usr (or any other) directory to /home to free up space on /.  Move the directory then put a link to it in /.

---

### Post by Impavidus on 2020-10-14
Then also remove linux-modules-extra-...:
```
sudo dpkg -P linux-{image,modules-extra}-5.4.0-{33,37,39,40,42,45}-generic
```

---

### Post by ajgreeny on 2020-10-14
Thanks Impavidus, that's  what I would also suggest and why I wanted to see the errors he got. Thanks for answering.

---

### Post by jbh54enwiler on 2020-10-14
That seems to have worked.  Thanks!

---

### Post by ajgreeny on 2020-10-14
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

