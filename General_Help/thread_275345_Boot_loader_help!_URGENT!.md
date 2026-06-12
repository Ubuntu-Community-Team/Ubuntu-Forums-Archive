---
title: "Boot loader help! URGENT!"
date: 2006-10-11
forum: General Help
---

### Post by wizzkid on 2006-10-11
Hi Guys,

I need help on my grub boot partition, because its running out of space.

Here's my partition information

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              14G  4.2G  9.6G  31% /
varrun                   371M  116K  371M   1% /var/run
varlock                  371M  4.0K  371M   1% /var/lock
udev                      371M  140K  371M   1% /dev
devshm                 371M     0  371M   0% /dev/shm
lrm                         371M   19M  353M   5% /lib/modules/2.6.15-27-386/volatile
/dev/hda3              45M   41M  1.7M  97% /boot
/dev/hda5              20G  6.0G   14G  31% /home
/dev/hda7              21G  9.3G   12G  45% /media/data

As you can see my /dev/hda3 is already in 97% used. when I view the content of /boot there's files that I am not sure of safe to delete.  You can view it here [http://www.leeph.net/pastebin/boot.png](http://www.leeph.net/pastebin/boot.png)

Please help! :)

---

### Post by apjone on 2006-10-11
it is recomended you make ur grub part 80 mb, just move the older file versions to a seperate partition, or burn them to disc.they are not strictly needed , and i only keep 2 versions + the single users mode( Troubleshooting).

---

### Post by apjone on 2006-10-11
remember to remove any changes from the menu.lst

---

### Post by jimbren on 2006-10-11
I've never messed around much with my boot partition, but I think you can delete most of the files in here.  You should be able to delete the files that comprise your older kernel versions, so long as you go into your grub.1st file and also delete the corresponding lines for those kernel versions.

Make sure you backup the entire partition to CD first, just to be on the safe side.

---

### Post by jimbren on 2006-10-11
in my post i wrote grub.1st--should be menu.1st.

jimbo

---

### Post by darrenm on 2006-10-11
sudo apt-get autoremove should remove some old images.

---

### Post by anaconda on 2006-10-11
> **jimbren said:**
> in my post i wrote grub.1st--should be menu.1st.

Actually it is menu.lst (as in .LST not .1ST)

And you can delete the old unused kernels to free some space.

(I have just used rm, but I heard, that it is better to remove them properly with apt-get or synaptic..)

---

### Post by epennings on 2006-10-11
you can probably remove any files which contain the following :

```
2.6.15-23
2.6.15-25
2.6.15-26
```

I assume you use the 2.16.15-27 kernel. Check with :

```
uname -r
```

I usually remove old kernels with synaptics, search for packages that have  the old version numbers in their name and completely remove them.

---

### Post by wizzkid on 2006-10-11
wizz@linux-laptop:~$ sudo apt-get autoremove
E: Invalid operation autoremove

how can I partition my grub to 80? :) what is the safest way to do?

Thanks.

---

### Post by epennings on 2006-10-11
You dont have to make your boot partition bigger, I use 32mb for /boot and it always work fine. Just remove the old kernels you dont use any more (see my above post)

---

### Post by wizzkid on 2006-10-11
Hi!

Yes, I am using 2.6.15-27

Is it safe to remove these version? 
2.6.15-23
2.6.15-25
2.6.15-26

I completely remove them already. Im just worried that it might affect on my other application? does it?

Thanks.

---

### Post by epennings on 2006-10-11
It doesnt affect your system, those old kernels were just wasting valuable space :D

In some cases it might be usefull to keep an old kernel, for example if a new kernel is broken/bugged.

My advice is to delete old kernels one week after you installed and succesfully used it.

---

### Post by wizzkid on 2006-10-11
thanks a lot for suggestions :-) 

I already delete the old kernels, which gives me back free spaces. thanks :)

---

### Post by darrenm on 2006-10-11
> **wizzkid said:**
> wizz@linux-laptop:~$ sudo apt-get autoremove

Strange. Works fine on mine:
```

darrenm@darrenm-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fglrx-control
The following packages will be REMOVED
  fglrx-control
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 5276kB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

