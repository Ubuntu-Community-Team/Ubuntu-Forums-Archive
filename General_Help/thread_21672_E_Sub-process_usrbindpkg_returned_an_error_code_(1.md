---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2005-03-23
forum: General Help
---

### Post by Alessio on 2005-03-23
During the dist-upgrade

```
Configuro linux-image-2.6.10-5-386 (2.6.10-29) ...
mkcramfs: ROM image write failed (wrote 3551232 of 4403200 bytes): No space left on device?
Failed to create initrd image.
dpkg: errore processando linux-image-2.6.10-5-386 (--configure):
....
 linux-image-2.6.10-5-386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ubuntu_demon on 2005-03-23
[QUOTE=Alessio]During the dist-upgrade

```
Configuro linux-image-2.6.10-5-386 (2.6.10-29) ...
mkcramfs: ROM image write failed (wrote 3551232 of 4403200 bytes): No space left on device?
Failed to create initrd image.
dpkg: errore processando linux-image-2.6.10-5-386 (--configure):
....
 linux-image-2.6.10-5-386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```[/QUOTE]
 So your harddrive is full. 
maybe apt-get clean will free enough space Try :
sudo apt-get clean
sudo apt-get distt-upgrade

---

### Post by Alessio on 2005-03-27
[QUOTE=demon666_nl]So your harddrive is full. 
maybe apt-get clean will free enough space Try :
sudo apt-get clean
sudo apt-get distt-upgrade[/QUOTE]
 Full?? 2,7 gb of free space :(

---

### Post by Alessio on 2005-03-27
[QUOTE=demon666_nl]So your harddrive is full. 
maybe apt-get clean will free enough space Try :
sudo apt-get clean
sudo apt-get distt-upgrade[/QUOTE]
 oooohh, the boot partition is full!
```

alessio@Ubuntu:~ $ df
Filesystem        blocchi di   1K   Usati Disponib. Uso% Montato su
/dev/hda6              8707616   5119872   3145412  62% /
tmpfs                   258272         0    258272   0% /dev/shm
/dev/hda5                45781     45756         0 100% /boot
/dev                   8707616   5119872   3145412  62% /.dev
none                      5120      2836      2284  56% /dev

```
what can i do?

---

### Post by ubuntu_demon on 2005-03-27
[QUOTE=Alessio]oooohh, the boot partition is full!
```

alessio@Ubuntu:~ $ df
Filesystem        blocchi di   1K   Usati Disponib. Uso% Montato su
/dev/hda6              8707616   5119872   3145412  62% /
tmpfs                   258272         0    258272   0% /dev/shm
/dev/hda5                45781     45756         0 100% /boot
/dev                   8707616   5119872   3145412  62% /.dev
none                      5120      2836      2284  56% /dev

```
what can i do?[/QUOTE]
 If you have more than 1 kernel installed try removing (using synaptic or apt-get) all kernels but the newest. After that do the dist-upgrade once more.

If it doesn't work boot from a livecd and resize your /boot partition into at leest 100 mb.

---

### Post by akak8ty on 2007-02-05
**Windows was created to keep away stupid people from UNIX??**

Perhaps you understand  vaffancullo?

If all the users have the same issue, who is stupido?

---

### Post by Ninja13at on 2007-03-20
I have the same error but my harddrives aren't full. 
kenny@kenny-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb1             36875340  23502432  11499732  68% /
varrun                 1038104       176   1037928   1% /var/run
varlock                1038104         4   1038100   1% /var/lock
procbususb               10240       116     10124   2% /proc/bus/usb
udev                     10240       116     10124   2% /dev
devshm                 1038104         0   1038104   0% /dev/shm
lrm                    1038104     18132   1019972   2% /lib/modules/2.6.17-11-386/volatile
/dev/sda1            312571192 260703732  51867460  84% /media/windows
kenny@kenny-desktop:~$

---

### Post by maphilli14 on 2008-03-30
I've gotten this may times during or just after a sudo apt-get upgrade

doing this usually helps

cd /var/cache/apt/archives
sudo rm -rf *
mkdir partial

sudo apt-get update (perhaps 2x)
sudo apt-get upgrade

voila!

HTH,

Mike

---

### Post by jazz612 on 2008-04-17
i got the following output

E: Sub-process /usr/bin/dpkg returned an error code (1)
mama@ubuntu:~$ cd /var/cache/apt/archives
mama@ubuntu:/var/cache/apt/archives$ sudo rm -rf *
[sudo] password for mama:
mama@ubuntu:/var/cache/apt/archives$ mkdir partial
mkdir: cannot create directory `partial': Permission denied
mama@ubuntu:/var/cache/apt/archives$ sudo rm -rf *
mama@ubuntu:/var/cache/apt/archives$ mkdir partial
mkdir: cannot create directory `partial': Permission denied
mama@ubuntu:/var/cache/apt/archives$

---

### Post by ikki_72 on 2008-05-30
you forgot to put **sudo** before **mkdir partial**
just because maphilli14 forgot, you don't have to (no offense maphilli14).
why? because directory **archive/** belongs to super user so you have to use sudo (**s**uper **u**ser **do**) to make a directory under it

unfortunately, method above didn't work for me.

---

### Post by ikki_72 on 2008-05-30
> **akak8ty said:**
> **Windows was created to keep away stupid people from UNIX??**

Perhaps you understand  vaffancullo?

If all the users have the same issue, who is stupido?

i think he/she was referring to a forum mod in ubuntu-it.org

---

### Post by ikki_72 on 2008-05-30
my solution to this problem:
i remove the package that gave me the error

---

