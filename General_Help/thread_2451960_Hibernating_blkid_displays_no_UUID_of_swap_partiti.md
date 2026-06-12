---
title: "Hibernating????? blkid displays no UUID of swap partition Ubuntu 18.04."
date: 2020-10-13
forum: General Help
---

### Post by thosecars822 on 2020-10-13
Hello

I have one computer with Ubuntu 18.04 in which the command blkid displays no swap partition. It only displays the UUID for one partition, the type of which is ext4.
I would like to be able to enable the hibernate function by means of the procedure explained on the following link:
[https://itectec.com/ubuntu/ubuntu-how-to-resume-ubuntu-18-04-after-hibernate/](https://itectec.com/ubuntu/ubuntu-how-to-resume-ubuntu-18-04-after-hibernate/)

I would like to know how I can get the UUID of the swap partition.

The comand "swapon --show" outputs the following:

NAME      TYPE SIZE   USED PRIO
/swapfile file   2G 160,8M   -2

And the command "blkid" ONLY outputs the UUID of the ext4 partition located in /dev/sda1.

Does that mean the computer does not have a swap partition?

How can I get to know the UUID of the swap partition that needs to get filled under /etc/default/grub to be able to enable the hibernate function?
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset resume=UUID=???????????????????????????????????????????????"

Thanks

---

### Post by CelticWarrior on 2020-10-13
Yes, it does mean you have a swapfile in lieu of a swap partition. It has been the Ubuntu default for years.

For hibernation you need a swap partition of at least the same amount as RAM.

---

### Post by GhX6GZMB on 2020-10-13
> **thosecars822 said:**
> 

The comand "swapon --show" outputs the following:

NAME      TYPE SIZE   USED PRIO
/swapfile file   2G 160,8M   -2

And the command "blkid" ONLY outputs the UUID of the ext4 partition located in /dev/sda1.

Does that mean the computer does not have a swap partition?


Your command shows a swapfile, not a swap partition. For Hibernate to work, the output should look something like this:

```
macro@macro-pc:~$ blkid
/dev/sda1: UUID="269ffc34-0c2a-4ef4-b794-85019d562e0d" TYPE="ext4" PARTUUID="7e408a68-01"
/dev/sda2: UUID="aac2fbd9-4194-436b-b8ae-65262e102311" TYPE="ext4" PARTUUID="7e408a68-02"
/dev/sda3: UUID="22928e29-fe9a-45ee-b043-666fd6520d7c" TYPE="swap" PARTUUID="7e408a68-03"
macro@macro-pc:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223,6G  0 disk 
&#9500;&#9472;sda1   8:1    0  29,3G  0 part /
&#9500;&#9472;sda2   8:2    0 188,3G  0 part /home
&#9492;&#9472;sda3   8:3    0     6G  0 part [SWAP]

```
You'll need to repartition your storage.

---

### Post by thosecars822 on 2020-10-16
I just created a swap partition but after running sudo systemctl hibernate, the system does not recover its previous state. 

My system looks like now as follows:
```

sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/sda1: UUID="02e1814e-f3a2-41f7-b7be-1f5a0ed7f277" TYPE="ext4" PARTUUID="f76b6d69-01"
/dev/sda2: LABEL="paraHibernar" UUID="ca93c303-fd4b-4a70-9ba0-f9af85e25e2e" TYPE="swap" PARTUUID="f76b6d69-02"

```


```

df -h
S.ficheros     Tamaño Usados  Disp Uso% Montado en
udev             1,5G      0  1,5G   0% /dev
tmpfs            303M   1,3M  302M   1% /run
/dev/sda1        141G    20G  114G  15% /
tmpfs            1,5G      0  1,5G   0% /dev/shm
tmpfs            5,0M   4,0K  5,0M   1% /run/lock
tmpfs            1,5G      0  1,5G   0% /sys/fs/cgroup
/dev/loop0        53M    53M     0 100% /snap/core18/1887
/dev/loop1        61M    61M     0 100% /snap/barrier/383
/dev/loop2        28M    28M     0 100% /snap/snapd/9610
tmpfs            303M    12K  303M   1% /run/user/1000

```

```

grep swap /etc/fstab
UUID=ca93c303-fd4b-4a70-9ba0-f9af85e25e2e  none            swap    sw              0       0
#/swapfile                                 none            swap    sw              0       0

```

```

cat /etc/default/grub
.....
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset resume=UUID=ca93c303-fd4b-4a70-9ba0-f9af85e25e2e"
....

```

```

cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sda2                               partition    5119996    0    -2

```

```

swapon --summary
Nombre del fichero                Tipo        Tamaño    Utilizado    Prioridad
/dev/sda2                                  partition    5119996    520    -2

```
But all this still does not work. 



The computer's RAM is 3GB and the swap partition has 5GB.

```

free -m
              total       usado       libre  compartido búfer/caché  disponible
Memoria:        3025         195        2323           2         506        2545
Swap:          4999           0        4999


```

Moreover, sometimes, not always, I see the following right after launching "sudo systemctl hibernate" and right before the computer shuts down:
"PM: not enough free memory PM: Error -12 creating hibernation image"

Anyway, even those times the computer does not display this problem right before shutting dowm, the computer does not recover its previous state later on after starting up again.

Do you have any idea about what I could be doing wrong?

Thanks in advance

---

### Post by GhX6GZMB on 2020-10-16
OK, so now you've created a swap partition and activated it using "mkswap" and "swapon".
You've also got the "resume" line in Grub, which is also fine. And hopefully you executed "sudo update-grub"
The swap partition line in my /etc/fstab looks like this:
```
UUID=ca93c303-fd4b-4a70-9ba0-f9af85e25e2e  none            swap    defaults              0       0
```

You're about half way to success. But there's much more to be done.

Create the file **/etc/initramfs-tools/conf.d/resume** with the content 
```
RESUME=UUID=ca93c303-fd4b-4a70-9ba0-f9af85e25e2e
```
run "sudo update-initramfs -u"

Next, you need to change the policies.
Create the file [B]/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
[/B]with this content:
```
 [Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes


 [Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes

```
you'll might also need to run **sudo apt install hibernate** although I think you did this already.

All done.

If you experience further problems, adding this line to grub might help:
```
GRUB_RECORDFAIL_TIMEOUT=$GRUB_TIMEOUT
```
(followed by sudo update-grub of course).

Cheers.

---

