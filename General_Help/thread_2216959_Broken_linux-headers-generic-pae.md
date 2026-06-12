---
title: "Broken linux-headers-generic-pae"
date: 2014-04-14
forum: General Help
---

### Post by calebjcook on 2014-04-14
hello,

i hope someone can give me a hand here. 

i manage a production server running 12.04.2 LTS. the server is behind a university firewall where nearly all of the ports are disabled. we have recently migrated our staff CMS from Teambox (version 3) to WordPress. without knowing a lot about Linux/Ubuntu, the best way to stay backed up offsite is to use a Wordpress backup plugin which allows full backups to sync over Dropbox on a schedule. 

but i can't install Dropbox because i run into a broken dependency warning. 

i've looked around on the net for solutions, but i'm unable to find one that is similar to mine with a solution.

i've tried 'sudo apt-get install -f' and a few other commands but they don't work.

i've opened synaptic and can find the broken dependencies and see that the linux-headers-generic-pae are broken.

i've tried to update the broken dependencies but get an error that no space is left. i have over 2GB free space

at this point, i'm very weary of doing something to destabilize the server. information is either hard to come by regarding this issue or i'm not using Google right. i see others having similar issues with this dependency but the solutions using a lot of commands and troubleshooting steps that i'm not familiar with or don't understand. 

my questions:

1) what is linux-headers-generic-pae? does working with it affect the stability of the OS?
2) is this a small problem or a big problem ... like can it wait until August when no one is using the server?
3) how can i fix the dependency?

thank you for any help, including links to some essential reading as i generally like to sort this stuff myself instead of asking for help.

:)

---

### Post by Bashing-om on 2014-04-14
calebjcook; Hi !

Probably easily addressed, solution well, maybe not, depends on what is causing the "no space left".
Many time that "no space left" will cause a new kernel not to install, and most often that is a result of the /boot partition full.
So let's look and find out why:
Terminal commands:
```

df -h
df -i
du -h --max-depth=1 | sort -hr
##and to look directly at 'root':
cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes.

We get some operating overhead, maybe that will make all the other problems go away.

Belatedly - Welcome to the forum, we do solutions .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Impavidus on 2014-04-15
A full /boot partition or you have run out of inodes – that's what I think of when I see linux-headers* mentioned. So, also run the command```
dpkg --list linux-headers*
```and we'll see whether you have a lot of old header packages installed. When you post terminal output, please do so in [noparse]```
code tags
```[/noparse].

The linux-headers-* packages usually don't affect the stability too much, but when broken they prevent installation of other updates. And a full disk is never a good idea. Your problem shouldn't be too difficult to solve.

---

### Post by calebjcook on 2014-04-17
thank you, Bashing-om and Impavidus. 

i hadn't set a subscription to my thread (fixed now). i have access to the server again tomorrow. i'll run the commands and report back then. 

cheers!

---

### Post by calebjcook on 2014-04-17
> **Bashing-om said:**
> calebjcook; Hi !

Probably easily addressed, solution well, maybe not, depends on what is causing the "no space left".
Many time that "no space left" will cause a new kernel not to install, and most often that is a result of the /boot partition full.
So let's look and find out why:
Terminal commands:
```

df -h
df -i
du -h --max-depth=1 | sort -hr
##and to look directly at 'root':
cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes.

We get some operating overhead, maybe that will make all the other problems go away.

Belatedly - Welcome to the forum, we do solutions .[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


**df -h**
```

Filesystem             Size  Used Avail Use% Mounted on
/dev/sda1              3.7G  3.1G  436M  88% /
udev                   979M   12K  979M   1% /dev
tmpfs                  396M  836K  395M   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                   990M  280K  989M   1% /run/shm
/dev/sda8              3.7G   73M  3.5G   3% /tmp
/dev/sda6              3.7G  649M  2.9G  19% /boot
/dev/sda11             9.2G  2.4G  6.4G  27% /home
/dev/mapper/tbsrv-srv  230G   23G  195G  11% /srv
/dev/sda7              5.5G  3.3G  2.0G  63% /usr
/dev/sda9              3.7G  974M  2.6G  28% /var
/dev/sda12              30G  810M   28G   3% /var/www

```

**df -i**
```

Filesystem              Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1               244320 121300   123020   50% /
udev                    214287    577   213710    1% /dev
tmpfs                   219533    513   219020    1% /run
none                    219533      3   219530    1% /run/lock
none                    219533      8   219525    1% /run/shm
/dev/sda8               244320     75   244245    1% /tmp
/dev/sda6               244320    393   243927    1% /boot
/dev/sda11              610800  43514   567286    8% /home
/dev/mapper/tbsrv-srv 15261696  52338 15209358    1% /srv
/dev/sda7               366480 359949     6531   99% /usr
/dev/sda9               244320   8549   235771    4% /var
/dev/sda12             1957888   4378  1953510    1% /var/www

```

**df -h -max-depth=1 | sort -hr**
```

udev                        979     1       979   1% /dev
tmpfs                       396     1       395   1% /run
sysfs                         0     0         0    - /sys
proc                          0     0         0    - /proc
none                        990     1       989   1% /run/shm
none                          5     0         5   0% /run/lock
none                          0     0         0    - /sys/kernel/security
none                          0     0         0    - /sys/kernel/debug
none                          0     0         0    - /sys/fs/fuse/connections
gvfs-fuse-daemon              0     0         0    - /home/calebjcook/.gvfs
Filesystem            1M-blocks  Used Available Use% Mounted on
/dev/sda9                  3755   974      2590  28% /var
/dev/sda8                  3755    73      3491   3% /tmp
/dev/sda7                  5632  3329      2017  63% /usr
/dev/sda6                  3755   649      2915  19% /boot
/dev/sda1                  3755  3128       436  88% /
/dev/sda12                30105   810     27765   3% /var/www
/dev/sda11                 9387  2378      6532  27% /home
devpts                        0     0         0    - /dev/pts
/dev/mapper/tbsrv-srv    234675 23504    199251  11% /srv
binfmt_misc                   0     0         0    - /proc/sys/fs/binfmt_misc

```

[B]sudo du -sx * | sort -n
[/B]```

du: cannot access `home/calebjcook/.gvfs': Permission denied
du: cannot access `proc/10880/task/10880/ns/net': No such file or directory
du: cannot access `proc/10880/task/10880/ns/uts': No such file or directory
du: cannot access `proc/10880/task/10880/ns/ipc': No such file or directory
du: cannot access `proc/10880/ns/net': No such file or directory
du: cannot access `proc/10880/ns/uts': No such file or directory
du: cannot access `proc/10880/ns/ipc': No such file or directory
du: cannot access `proc/11294/task/11294/ns/net': No such file or directory
du: cannot access `proc/11294/task/11294/ns/uts': No such file or directory
du: cannot access `proc/11294/task/11294/ns/ipc': No such file or directory
du: cannot access `proc/11294/ns/net': No such file or directory
du: cannot access `proc/11294/ns/uts': No such file or directory
du: cannot access `proc/11294/ns/ipc': No such file or directory
du: cannot access `proc/15755/task/15755/ns/net': No such file or directory
du: cannot access `proc/15755/task/15755/ns/uts': No such file or directory
du: cannot access `proc/15755/task/15755/ns/ipc': No such file or directory
du: cannot access `proc/15755/ns/net': No such file or directory
du: cannot access `proc/15755/ns/uts': No such file or directory
du: cannot access `proc/15755/ns/ipc': No such file or directory
du: cannot access `proc/15843/task/15843/fd/4': No such file or directory
du: cannot access `proc/15843/task/15843/fdinfo/4': No such file or directory
du: cannot access `proc/15843/fd/4': No such file or directory
du: cannot access `proc/15843/fdinfo/4': No such file or directory
du: cannot access `proc/24218/task/24218/ns/net': No such file or directory
du: cannot access `proc/24218/task/24218/ns/uts': No such file or directory
du: cannot access `proc/24218/task/24218/ns/ipc': No such file or directory
du: cannot access `proc/24218/ns/net': No such file or directory
du: cannot access `proc/24218/ns/uts': No such file or directory
du: cannot access `proc/24218/ns/ipc': No such file or directory

```

i had two goes and du produced the same errors.

---

### Post by calebjcook on 2014-04-17
> **Impavidus said:**
> A full /boot partition or you have run out of inodes – that's what I think of when I see linux-headers* mentioned. So, also run the command```
dpkg --list linux-headers*
```and we'll see whether you have a lot of old header packages installed. When you post terminal output, please do so in [noparse]```
code tags
```[/noparse].

The linux-headers-* packages usually don't affect the stability too much, but when broken they prevent installation of other updates. And a full disk is never a good idea. Your problem shouldn't be too difficult to solve.

[B]dpkg --list linux-headers

[/B]```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-headers  <none>         (no description available)

```

probably not what you expected?

---

### Post by Bashing-om on 2014-04-17
calebjcook; Welp.

Doesn't look real bad.

Here is the problem identified:
> 
/dev/sda7               366480 359949     6531   99% /usr


I do not know why "dpkg --list linux-headers" does not give a result (??).

Let's do
```

dpkg -l | grep linux-image
dpkg -l | grep linux-headers

```
to see what work we have to do. As seen, the directory '/usr' is out of inodes. The only quick solution to this situation is to remove files. Starting with the images and headers. Look there and remove all that you no longer have a need of. Got to release those inodes ! We will remove the kernels (those images AND headers) with the package manager !

The kernel (image headers) that must be kept is the one you are running on.
```

uname -r

``` and keep one other for general principals and a safety net.

--------------
'sudo du -sx * | sort -n' takes a bit of time to complete and the advisories about "/proc" may be ignored. "/proc" is a virtual file system and is constantly changing and as such 'du' can not get a handle on it. If one waits for the command to complete, well, it will complete.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by calebjcook on 2014-04-18
wow! thanks for the fast response. :)

**dpkg -l | grep linux-image**
```

ii  linux-image-2.6.32-28-generic-pae                           2.6.32-28.55                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-29-generic-pae                           2.6.32-29.58                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-30-generic-pae                           2.6.32-30.59                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-31-generic-pae                           2.6.32-31.61                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-32-generic-pae                           2.6.32-32.62                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-33-generic-pae                           2.6.32-33.72                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-34-generic-pae                           2.6.32-34.77                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-35-generic-pae                           2.6.32-35.78                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-36-generic-pae                           2.6.32-36.79                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-37-generic-pae                           2.6.32-37.81                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-38-generic-pae                           2.6.32-38.83                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-39-generic-pae                           2.6.32-39.86                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-40-generic-pae                           2.6.32-40.87                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-41-generic-pae                           2.6.32-41.94                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-42-generic-pae                           2.6.32-42.96                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-43-generic-pae                           2.6.32-43.97                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-44-generic-pae                           2.6.32-44.98                               Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-45-generic-pae                           2.6.32-45.104                              Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-46-generic-pae                           2.6.32-46.108                              Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-47-generic-pae                           2.6.32-47.109                              Linux kernel image for version 2.6.32 on x86
ii  linux-image-3.2.0-45-generic-pae                            3.2.0-45.70                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-generic-pae                            3.2.0-48.74                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-51-generic-pae                            3.2.0-51.77                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-52-generic-pae                            3.2.0-52.78                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic-pae                            3.2.0-53.81                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-54-generic-pae                            3.2.0-54.82                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-55-generic-pae                            3.2.0-55.85                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-56-generic-pae                            3.2.0-56.86                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-58-generic-pae                            3.2.0-58.88                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-60-generic-pae                            3.2.0-60.91                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                                     3.2.0.60.71                                Generic Linux kernel image

```



[B]dpkg -l | grep linux-headers
[/B]```

ii  linux-headers-2.6.32-31                                     2.6.32-31.61                               Header files related to Linux kernel version 2.6.32
ii  linux-headers-2.6.32-31-generic-pae                         2.6.32-31.61                               Linux kernel headers for version 2.6.32 on x86
ii  linux-headers-3.2.0-45                                      3.2.0-45.70                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-generic-pae                          3.2.0-45.70                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48                                      3.2.0-48.74                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic-pae                          3.2.0-48.74                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                                      3.2.0-51.77                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic-pae                          3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                                      3.2.0-52.78                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic-pae                          3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53                                      3.2.0-53.81                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic-pae                          3.2.0-53.81                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54                                      3.2.0-54.82                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic-pae                          3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55                                      3.2.0-55.85                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic-pae                          3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-56                                      3.2.0-56.86                                Header files related to Linux kernel version 3.2.0
iU  linux-headers-generic-pae                                   3.2.0.56.66                                Generic Linux kernel headers

```
[B]
uname -r
[/B]```

3.2.0-55-generic-pae

```

---

### Post by calebjcook on 2014-04-18
i gave [COLOR=#000000][FONT=Ubuntu Mono]sudo du -sx * | sort -n[/FONT][/COLOR] more time ...

```

0	initrd.img
0	initrd.img.old
0	proc
0	sys
0	vmlinuz
0	vmlinuz.old
4	cdrom
4	media
4	mnt
4	opt
4	selinux
12	dev
16	lost+found
836	run
1416	tmp
8556	bin
9316	sbin
10144	etc
46320	root
591176	boot
927968	var
2092368	home
3055360	lib
3265548	usr
23876252	srv

```

---

### Post by Impavidus on 2014-04-18
> **calebjcook said:**
> [B]dpkg --list linux-headers

[/B]```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-headers  <none>         (no description available)

```

probably not what you expected?
You missed the asterisk:```
dpkg --list linux-headers**[COLOR=#ff0000]*[/COLOR]**
```But your other dpkg commands already provided the information.

You have partitioned your drive in a complex way, but it shouldn't really hinder. Use```
sudo dpkg -P linux-image-<some version>
sudo dpkg -P linux-headers-<some version>
```to uninstall old kernel images and headers. Use all versions you reported a few posts up up to (including) 3.2.0-54.

---

### Post by calebjcook on 2014-04-20
i really appreciate the help so far. 

i've got the headers and images are removed, everything up to and including 3.2.0-54

but i still can't use sudo apt-get install -f or install Dropbox

when i try to fix the broken packages, i get:
```

dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-56-generic-pae; however:
  Package linux-headers-3.2.0-56-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.56.66); however:
  Version of linux-image-generic-pae on system is 3.2.0.60.71.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.56.66); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-56-generic-pae; however:
  Package linux-headers-3.2.0-56-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.56.66); however:
  Version of linux-image-generic-pae on system is 3.2.0.60.71.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.56.66); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic-pae
 linux-generic-pae

```

dpkg -l | grep linux-image:
```

ii  linux-image-3.2.0-55-generic-pae                            3.2.0-55.85                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-56-generic-pae                            3.2.0-56.86                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-58-generic-pae                            3.2.0-58.88                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-60-generic-pae                            3.2.0-60.91                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                                     3.2.0.60.71                                Generic Linux kernel image

```

dpkg -l | grep linux-header:
```

ii  linux-headers-3.2.0-55                                      3.2.0-55.85                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic-pae                          3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-56                                      3.2.0-56.86                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60                                      3.2.0-60.91                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic-pae                          3.2.0-60.91                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic-pae 

```

the install wants 3.2.0-55.66 but that's not on the system, which means broken pipe ... right?

how can i fix this?

---

### Post by Bashing-om on 2014-04-20
calebjcook; Hi;

Let's see if the generic approach works.

```

sudo apt-get install linux-generic linux-headers-generic linux-image-generic

```

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by calebjcook on 2014-04-20
> **Bashing-om said:**
> calebjcook; Hi;

Let's see if the generic approach works.

```

sudo apt-get install linux-generic linux-headers-generic linux-image-generic

```
[INDENT][INDENT]it could happen
[/INDENT]
[/INDENT]



:( no. same error

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.56.66) but 3.2.0.60.71 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-60-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-56-generic-pae but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.2.0-60-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2014-04-21
calebjcook; UnGood.

Let's poke at it a bit and see what returns.

```

sudo apt-get install linux-image-3.2.0.56.66-generic-pae

```

[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT]

---

### Post by calebjcook on 2014-04-21
> **Bashing-om said:**
> calebjcook; UnGood.

Let's poke at it a bit and see what returns.

```

sudo apt-get install linux-image-3.2.0.56.66-generic-pae

```[INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]



:neutral:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-3.2.0.56.66-generic-pae
E: Couldn't find any package by regex 'linux-image-3.2.0.56.66-generic-pae'

```

---

### Post by Bashing-om on 2014-04-21
calebjcook; Well shoot !

Let's get a better description of what I am hunting for:
```

apt-cache search linux-image

```
What does the Package manager think ?
```

apt-cache showpkg linux-headers

```

What we are going to do is get down to the bottom of the dependency chain, install, and work our way back up and out.

[INDENT][INDENT]as we struggle merrily on
[/INDENT][/INDENT]

---

### Post by calebjcook on 2014-04-21
two long lists comin' atchya! :)[B]

apt-cache search linux-image[/B]
```

alsa-base - ALSA driver configuration fileslinux-image - Generic Linux kernel image.
linux-image-3.2.0-23-generic - Linux kernel image for version 3.2.0 on 64 bit x86 SMP
linux-image-3.2.0-23-virtual - Linux kernel image for version 3.2.0 on 64 bit x86 Virtual Guests
linux-image-extra-3.2.0-23-virtual - Linux kernel image for version 3.2.0 on 64 bit x86 Virtual Guests
linux-image-extra-virtual - Linux kernel extra modules for virtual machines
linux-image-generic - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
linux-image-virtual - Linux kernel image for virtual machines
linux-virtual - Complete Linux kernel for virtual machines
linux-image-3.2.0-23-generic-pae - Linux kernel image for version 3.2.0 on 64 bit x86 SMP
linux-image-generic-pae - Generic Linux kernel image
linux-image-3.2.0-23-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-lowlatency - lowlatency Linux kernel image
linux-image-3.2.0-23-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-lowlatency-pae - lowlatency Linux kernel image
linux-image-3.2.0-24-generic - Linux kernel image for version 3.2.0 on 64 bit x86 SMP
linux-image-3.2.0-24-virtual - Linux kernel image for version 3.2.0 on 64 bit x86 Virtual Guests
linux-image-current-generic - Depends on the most recently released generic kernel image and headers.
linux-image-extra-3.2.0-24-virtual - Linux kernel image for version 3.2.0 on 64 bit x86 Virtual Guests
linux-image-generic-lts-quantal - Generic Linux kernel image
linux-image-generic-lts-raring - Generic Linux kernel image
linux-image-generic-lts-saucy - Generic Linux kernel image
linux-image-hwe-generic - Depends on the generic hardware enablement kernel image and headers.
linux-image-3.11.0-13-generic - Linux kernel image for version 3.11.0 on 32 bit x86 SMP
linux-image-3.11.0-14-generic - Linux kernel image for version 3.11.0 on 32 bit x86 SMP
linux-image-3.11.0-15-generic - Linux kernel image for version 3.11.0 on 32 bit x86 SMP
linux-image-3.11.0-17-generic - Linux kernel image for version 3.11.0 on 32 bit x86 SMP
linux-image-3.11.0-18-generic - Linux kernel image for version 3.11.0 on 32 bit x86 SMP
linux-image-3.11.0-19-generic - Linux kernel image for version 3.11.0 on 32 bit x86 SMP
linux-image-3.2.0-24-generic-pae - Linux kernel image for version 3.2.0 on 64 bit x86 SMP
linux-image-3.2.0-25-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-25-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-25-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-26-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-26-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-26-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-27-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-27-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-27-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-29-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-29-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-29-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-30-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-30-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-30-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-31-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-31-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-31-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-32-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-32-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-32-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-33-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-33-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-33-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-34-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-34-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-34-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-35-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-35-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-35-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-36-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-36-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-36-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-37-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-37-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-37-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-38-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-38-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-38-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-39-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-39-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-39-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-40-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-40-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-40-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-41-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-41-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-41-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-43-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-43-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-43-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-44-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-44-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-44-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-45-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-45-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-45-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-48-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-48-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-48-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-49-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-49-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-49-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-51-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-51-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-51-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-52-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-52-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-52-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-53-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-53-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-53-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-54-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-54-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-54-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-55-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-55-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-55-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-56-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-56-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-56-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-57-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-57-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-57-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-58-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-58-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-58-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-59-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-59-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-59-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-60-generic - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-60-generic-pae - Linux kernel image for version 3.2.0 on 32 bit x86 SMP
linux-image-3.2.0-60-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.5.0-18-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-19-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-21-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-22-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-23-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-24-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-25-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-26-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-27-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-28-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-30-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-31-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-32-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-34-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-36-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-37-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-39-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-40-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-41-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-42-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-43-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-44-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-45-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-46-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-47-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.5.0-48-generic - Linux kernel image for version 3.5.0 on 32 bit x86 SMP
linux-image-3.8.0-19-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-21-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-22-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-23-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-25-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-26-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-27-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-29-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-30-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-31-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-32-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-33-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-34-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-35-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-36-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-37-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-3.8.0-38-generic - Linux kernel image for version 3.8.0 on 32 bit x86 SMP
linux-image-extra-3.2.0-25-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-26-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-27-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-29-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-30-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-31-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-32-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-33-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-34-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-35-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-36-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-37-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-38-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-39-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-40-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-41-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-43-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-44-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-45-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-48-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-49-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-51-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-52-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-53-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-54-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-55-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-56-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-57-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-58-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-59-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-extra-3.2.0-60-virtual - Linux kernel image for version 3.2.0 on 32 bit x86 Virtual Guests
linux-image-3.2.0-33-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-35-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-36-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-37-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-38-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-39-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-40-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-41-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-44-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-48-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-49-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-51-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-52-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-53-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-54-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-55-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-56-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-57-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-58-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-59-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-60-lowlatency - Linux kernel image for version 3.2.0 on x86/x86_64
linux-image-3.2.0-33-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-35-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-36-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-37-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-38-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-39-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-40-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-41-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-44-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-48-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-49-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-51-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-52-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-53-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-54-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-55-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-56-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-57-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-58-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-59-lowlatency-pae - Linux kernel image for version 3.2.0 on x86
linux-image-3.2.0-60-lowlatency-pae - Linux kernel image for version 3.2.0 on x86

```

**apt-cache showpkg linux-headers**
```
Package: linux-headersVersions: 


Reverse Depends: 
  nvidia-173-updates,linux-headers
  nvidia-173,linux-headers
  sl-modem-source,linux-headers
  xtables-addons-dkms,linux-headers
  crystalhd-dkms,linux-headers
  blcr-dkms,linux-headers
  alsa-source,linux-headers
  nvidia-96,linux-headers
  sl-modem-source,linux-headers
  xtables-addons-dkms,linux-headers
  west-chamber-dkms,linux-headers
  oss4-dkms,linux-headers
  openswan-modules-source,linux-headers
  crystalhd-dkms,linux-headers
  blktap-dkms,linux-headers
  blcr-dkms,linux-headers
  alsa-source,linux-headers
  nvidia-current-updates,linux-headers
  nvidia-current,linux-headers
  nvidia-96-updates,linux-headers
  nvidia-96,linux-headers
  nvidia-173-updates,linux-headers
  nvidia-173,linux-headers
  fglrx-updates,linux-headers
  fglrx,linux-headers
  bcmwl-kernel-source,linux-headers
  dkms,linux-headers
Dependencies: 
Provides: 
Reverse Provides: 
linux-headers-3.2.0-24-virtual 3.2.0-24.38
linux-headers-3.2.0-24-generic-pae 3.2.0-24.38
linux-headers-3.2.0-24-generic 3.2.0-24.38
linux-headers-3.2.0-24 3.2.0-24.38
linux-headers-3.2.0-60-lowlatency-pae 3.2.0-60.62
linux-headers-3.2.0-60-lowlatency 3.2.0-60.62
linux-headers-3.2.0-59-lowlatency-pae 3.2.0-59.61
linux-headers-3.2.0-59-lowlatency 3.2.0-59.61
linux-headers-3.2.0-58-lowlatency-pae 3.2.0-58.60
linux-headers-3.2.0-58-lowlatency 3.2.0-58.60
linux-headers-3.2.0-57-lowlatency-pae 3.2.0-57.59
linux-headers-3.2.0-57-lowlatency 3.2.0-57.59
linux-headers-3.2.0-56-lowlatency-pae 3.2.0-56.58
linux-headers-3.2.0-56-lowlatency 3.2.0-56.58
linux-headers-3.2.0-55-lowlatency-pae 3.2.0-55.57
linux-headers-3.2.0-55-lowlatency 3.2.0-55.57
linux-headers-3.2.0-54-lowlatency-pae 3.2.0-54.56
linux-headers-3.2.0-54-lowlatency 3.2.0-54.56
linux-headers-3.2.0-53-lowlatency-pae 3.2.0-53.55
linux-headers-3.2.0-53-lowlatency 3.2.0-53.55
linux-headers-3.2.0-52-lowlatency-pae 3.2.0-52.54
linux-headers-3.2.0-52-lowlatency 3.2.0-52.54
linux-headers-3.2.0-51-lowlatency-pae 3.2.0-51.53
linux-headers-3.2.0-51-lowlatency 3.2.0-51.53
linux-headers-3.2.0-49-lowlatency-pae 3.2.0-49.51
linux-headers-3.2.0-49-lowlatency 3.2.0-49.51
linux-headers-3.2.0-48-lowlatency-pae 3.2.0-48.50
linux-headers-3.2.0-48-lowlatency 3.2.0-48.50
linux-headers-3.2.0-44-lowlatency-pae 3.2.0-44.48
linux-headers-3.2.0-44-lowlatency 3.2.0-44.48
linux-headers-3.2.0-41-lowlatency-pae 3.2.0-41.45
linux-headers-3.2.0-41-lowlatency 3.2.0-41.45
linux-headers-3.2.0-40-lowlatency-pae 3.2.0-40.43
linux-headers-3.2.0-40-lowlatency 3.2.0-40.43
linux-headers-3.2.0-39-lowlatency-pae 3.2.0-39.41
linux-headers-3.2.0-39-lowlatency 3.2.0-39.41
linux-headers-3.2.0-38-lowlatency-pae 3.2.0-38.40
linux-headers-3.2.0-38-lowlatency 3.2.0-38.40
linux-headers-3.2.0-37-lowlatency-pae 3.2.0-37.37
linux-headers-3.2.0-37-lowlatency 3.2.0-37.37
linux-headers-3.2.0-36-lowlatency-pae 3.2.0-36.36
linux-headers-3.2.0-36-lowlatency 3.2.0-36.36
linux-headers-3.2.0-35-lowlatency-pae 3.2.0-35.34
linux-headers-3.2.0-35-lowlatency 3.2.0-35.34
linux-headers-3.2.0-33-lowlatency-pae 3.2.0-33.33
linux-headers-3.2.0-33-lowlatency 3.2.0-33.33
linux-headers-3.8.0-38-generic 3.8.0-38.56~precise1
linux-headers-3.8.0-37-generic 3.8.0-37.53~precise1
linux-headers-3.8.0-36-generic 3.8.0-36.52~precise1
linux-headers-3.8.0-35-generic 3.8.0-35.52~precise1
linux-headers-3.8.0-34-generic 3.8.0-34.49~precise1
linux-headers-3.8.0-33-generic 3.8.0-33.48~precise1
linux-headers-3.8.0-32-generic 3.8.0-32.47~precise1
linux-headers-3.8.0-31-generic 3.8.0-31.46~precise1
linux-headers-3.8.0-30-generic 3.8.0-30.44~precise1
linux-headers-3.8.0-29-generic 3.8.0-29.42~precise1
linux-headers-3.8.0-27-generic 3.8.0-27.40~precise3
linux-headers-3.8.0-26-generic 3.8.0-26.38~precise2
linux-headers-3.8.0-25-generic 3.8.0-25.37~precise1
linux-headers-3.8.0-23-generic 3.8.0-23.34~precise1
linux-headers-3.8.0-22-generic 3.8.0-22.33~precise1
linux-headers-3.8.0-21-generic 3.8.0-21.32~precise1
linux-headers-3.8.0-19-generic 3.8.0-19.30~precise1
linux-headers-3.5.0-48-generic 3.5.0-48.72~precise1
linux-headers-3.5.0-47-generic 3.5.0-47.71~precise1
linux-headers-3.5.0-46-generic 3.5.0-46.70~precise1
linux-headers-3.5.0-45-generic 3.5.0-45.68~precise1
linux-headers-3.5.0-44-generic 3.5.0-44.67~precise1
linux-headers-3.5.0-43-generic 3.5.0-43.66~precise1
linux-headers-3.5.0-42-generic 3.5.0-42.65~precise1
linux-headers-3.5.0-41-generic 3.5.0-41.64~precise1
linux-headers-3.5.0-40-generic 3.5.0-40.62~precise1
linux-headers-3.2.0-60-virtual 3.2.0-60.91
linux-headers-3.2.0-60-generic-pae 3.2.0-60.91
linux-headers-3.2.0-60-generic 3.2.0-60.91
linux-headers-3.2.0-60 3.2.0-60.91
linux-headers-3.2.0-59-virtual 3.2.0-59.90
linux-headers-3.2.0-59-generic-pae 3.2.0-59.90
linux-headers-3.2.0-59-generic 3.2.0-59.90
linux-headers-3.2.0-59 3.2.0-59.90
linux-headers-3.2.0-58-virtual 3.2.0-58.88
linux-headers-3.2.0-58-generic-pae 3.2.0-58.88
linux-headers-3.2.0-58-generic 3.2.0-58.88
linux-headers-3.2.0-58 3.2.0-58.88
linux-headers-3.2.0-57-virtual 3.2.0-57.87
linux-headers-3.2.0-57-generic-pae 3.2.0-57.87
linux-headers-3.2.0-57-generic 3.2.0-57.87
linux-headers-3.2.0-57 3.2.0-57.87
linux-headers-3.2.0-56-virtual 3.2.0-56.86
linux-headers-3.2.0-56-generic-pae 3.2.0-56.86
linux-headers-3.2.0-56-generic 3.2.0-56.86
linux-headers-3.2.0-56 3.2.0-56.86
linux-headers-3.2.0-55-virtual 3.2.0-55.85
linux-headers-3.2.0-55-generic-pae 3.2.0-55.85
linux-headers-3.2.0-55-generic 3.2.0-55.85
linux-headers-3.2.0-55 3.2.0-55.85
linux-headers-3.2.0-54-virtual 3.2.0-54.82
linux-headers-3.2.0-54-generic-pae 3.2.0-54.82
linux-headers-3.2.0-54-generic 3.2.0-54.82
linux-headers-3.2.0-54 3.2.0-54.82
linux-headers-3.2.0-53-virtual 3.2.0-53.81
linux-headers-3.2.0-53-generic-pae 3.2.0-53.81
linux-headers-3.2.0-53-generic 3.2.0-53.81
linux-headers-3.2.0-53 3.2.0-53.81
linux-headers-3.2.0-52-virtual 3.2.0-52.78
linux-headers-3.2.0-52-generic-pae 3.2.0-52.78
linux-headers-3.2.0-52-generic 3.2.0-52.78
linux-headers-3.2.0-52 3.2.0-52.78
linux-headers-3.2.0-51-virtual 3.2.0-51.77
linux-headers-3.2.0-51-generic-pae 3.2.0-51.77
linux-headers-3.2.0-51-generic 3.2.0-51.77
linux-headers-3.2.0-51 3.2.0-51.77
linux-headers-3.2.0-49-virtual 3.2.0-49.75
linux-headers-3.2.0-49-generic-pae 3.2.0-49.75
linux-headers-3.2.0-49-generic 3.2.0-49.75
linux-headers-3.2.0-49 3.2.0-49.75
linux-headers-3.2.0-48-virtual 3.2.0-48.74
linux-headers-3.2.0-48-generic-pae 3.2.0-48.74
linux-headers-3.2.0-48-generic 3.2.0-48.74
linux-headers-3.2.0-48 3.2.0-48.74
linux-headers-3.2.0-45-virtual 3.2.0-45.70
linux-headers-3.2.0-45-generic-pae 3.2.0-45.70
linux-headers-3.2.0-45-generic 3.2.0-45.70
linux-headers-3.2.0-45 3.2.0-45.70
linux-headers-3.2.0-44-virtual 3.2.0-44.69
linux-headers-3.2.0-44-generic-pae 3.2.0-44.69
linux-headers-3.2.0-44-generic 3.2.0-44.69
linux-headers-3.2.0-44 3.2.0-44.69
linux-headers-3.2.0-43-virtual 3.2.0-43.68
linux-headers-3.2.0-43-generic-pae 3.2.0-43.68
linux-headers-3.2.0-43-generic 3.2.0-43.68
linux-headers-3.2.0-43 3.2.0-43.68
linux-headers-3.2.0-41-virtual 3.2.0-41.66
linux-headers-3.2.0-41-generic-pae 3.2.0-41.66
linux-headers-3.2.0-41-generic 3.2.0-41.66
linux-headers-3.2.0-41 3.2.0-41.66
linux-headers-3.2.0-40-virtual 3.2.0-40.64
linux-headers-3.2.0-40-generic-pae 3.2.0-40.64
linux-headers-3.2.0-40-generic 3.2.0-40.64
linux-headers-3.2.0-40 3.2.0-40.64
linux-headers-3.2.0-39-virtual 3.2.0-39.62
linux-headers-3.2.0-39-generic-pae 3.2.0-39.62
linux-headers-3.2.0-39-generic 3.2.0-39.62
linux-headers-3.2.0-39 3.2.0-39.62
linux-headers-3.2.0-38-virtual 3.2.0-38.61
linux-headers-3.2.0-38-generic-pae 3.2.0-38.61
linux-headers-3.2.0-38-generic 3.2.0-38.61
linux-headers-3.2.0-38 3.2.0-38.61
linux-headers-3.2.0-37-virtual 3.2.0-37.58
linux-headers-3.2.0-37-generic-pae 3.2.0-37.58
linux-headers-3.2.0-37-generic 3.2.0-37.58
linux-headers-3.2.0-37 3.2.0-37.58
linux-headers-3.2.0-36-virtual 3.2.0-36.57
linux-headers-3.2.0-36-generic-pae 3.2.0-36.57
linux-headers-3.2.0-36-generic 3.2.0-36.57
linux-headers-3.2.0-36 3.2.0-36.57
linux-headers-3.2.0-35-virtual 3.2.0-35.55
linux-headers-3.2.0-35-generic-pae 3.2.0-35.55
linux-headers-3.2.0-35-generic 3.2.0-35.55
linux-headers-3.2.0-35 3.2.0-35.55
linux-headers-3.2.0-34-virtual 3.2.0-34.53
linux-headers-3.2.0-34-generic-pae 3.2.0-34.53
linux-headers-3.2.0-34-generic 3.2.0-34.53
linux-headers-3.2.0-34 3.2.0-34.53
linux-headers-3.2.0-33-virtual 3.2.0-33.52
linux-headers-3.2.0-33-generic-pae 3.2.0-33.52
linux-headers-3.2.0-33-generic 3.2.0-33.52
linux-headers-3.2.0-33 3.2.0-33.52
linux-headers-3.2.0-32-virtual 3.2.0-32.51
linux-headers-3.2.0-32-generic-pae 3.2.0-32.51
linux-headers-3.2.0-32-generic 3.2.0-32.51
linux-headers-3.2.0-32 3.2.0-32.51
linux-headers-3.2.0-31-virtual 3.2.0-31.50
linux-headers-3.2.0-31-generic-pae 3.2.0-31.50
linux-headers-3.2.0-31-generic 3.2.0-31.50
linux-headers-3.2.0-31 3.2.0-31.50
linux-headers-3.2.0-30-virtual 3.2.0-30.48
linux-headers-3.2.0-30-generic-pae 3.2.0-30.48
linux-headers-3.2.0-30-generic 3.2.0-30.48
linux-headers-3.2.0-30 3.2.0-30.48
linux-headers-3.2.0-29-virtual 3.2.0-29.46
linux-headers-3.2.0-29-generic-pae 3.2.0-29.46
linux-headers-3.2.0-29-generic 3.2.0-29.46
linux-headers-3.2.0-29 3.2.0-29.46
linux-headers-3.2.0-27-virtual 3.2.0-27.43
linux-headers-3.2.0-27-generic-pae 3.2.0-27.43
linux-headers-3.2.0-27-generic 3.2.0-27.43
linux-headers-3.2.0-27 3.2.0-27.43
linux-headers-3.2.0-26-virtual 3.2.0-26.41
linux-headers-3.2.0-26-generic-pae 3.2.0-26.41
linux-headers-3.2.0-26-generic 3.2.0-26.41
linux-headers-3.2.0-26 3.2.0-26.41
linux-headers-3.2.0-25-virtual 3.2.0-25.40
linux-headers-3.2.0-25-generic-pae 3.2.0-25.40
linux-headers-3.2.0-25-generic 3.2.0-25.40
linux-headers-3.2.0-25 3.2.0-25.40
linux-headers-3.2.0-24-virtual 3.2.0-24.39
linux-headers-3.2.0-24-generic-pae 3.2.0-24.39
linux-headers-3.2.0-24-generic 3.2.0-24.39
linux-headers-3.2.0-24 3.2.0-24.39
linux-headers-3.2.0-23-lowlatency-pae 3.2.0-23.31
linux-headers-3.2.0-23-lowlatency 3.2.0-23.31
linux-headers-3.2.0-23-virtual 3.2.0-23.36
linux-headers-3.2.0-23-generic-pae 3.2.0-23.36
linux-headers-3.2.0-23-generic 3.2.0-23.36
linux-headers-3.2.0-23 3.2.0-23.36
```

---

### Post by Bashing-om on 2014-04-22
calebjcook; Well !

We know they are available.

Try:
```

sudo apt-get install linux-headers-3.2.0-56-generic-pae
sudo apt-get install -f

```

Maybe we also have to intervene for the .60 kernels also ? .. 

[INDENT]progress made slowly
[/INDENT]

---

### Post by calebjcook on 2014-04-23
> **Bashing-om said:**
> calebjcook; Well !

We know they are available.

Try:
```

sudo apt-get install linux-headers-3.2.0-56-generic-pae
sudo apt-get install -f

```

Maybe we also have to intervene for the .60 kernels also ? .. [INDENT]progress made slowly
[/INDENT]


sorry for the lull (day off :D )

i tried [B]sudo apt-get install linux-headers-3.2.0-56-generic-pae
[/B]```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.56.66) but 3.2.0.60.71 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

and **sudo apt-get install -f**
```

dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-56-generic-pae; however:
  Package linux-headers-3.2.0-56-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.56.66); however:
  Version of linux-image-generic-pae on system is 3.2.0.60.71.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.56.66); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-headers-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and because i'd like to think i know what i'm doing **sudo apt-get install linux-headers-3.2.0-60-generic-pae**
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-60-generic-pae is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.56.66) but 3.2.0.60.71 is to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-56-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

could something like **sudo apt-get install linux-headers-3.2.0-56-66-generic-pae**&#8203; work??

---

### Post by Bashing-om on 2014-04-24
calebjcook; Hey !

I also take time off, setting up to do a clean install(s) - 2 -  of 14.04, and trying to understand an issue of my own on my system, umph !
But as the worm turns:

I am not totally sure of what is going on, as earlier the Package Manager was hollering about the .60 kernel,  now it is hollering about the .56 image.

Let's see if we can give it what it wants: Give it a little bit of help.
```

sudo apt-get install linux-image-3.2.0-56-generic-pae

```

We gave it the headers, I had expected it to just pick up that image file. 

Do this and we see what the Package manage has to say now ?

---

### Post by calebjcook on 2014-04-25
> **Bashing-om said:**
> calebjcook; Hey !

I also take time off, setting up to do a clean install(s) - 2 -  of 14.04, and trying to understand an issue of my own on my system, umph !
But as the worm turns:

I am not totally sure of what is going on, as earlier the Package Manager was hollering about the .60 kernel,  now it is hollering about the .56 image.

Let's see if we can give it what it wants: Give it a little bit of help.
```

sudo apt-get install linux-image-3.2.0-56-generic-pae

```

We gave it the headers, I had expected it to just pick up that image file. 

Do this and we see what the Package manage has to say now ?

days off are important and best spent with family or a computer that isn't giving you trouble :grin:

[B]sudo apt-get install linux-image-3.2.0-56-generic-pae
[/B]```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-3.2.0-56-generic-pae is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.56.66) but 3.2.0.60.71 is to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-56-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

same same

er ... is it possible that i've mistyped a command?

---

### Post by Impavidus on 2014-04-25
Have been working on other threads but popping in again. Fresh ideas may help.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-60-generic-pae is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  **linux-generic-pae** : Depends: linux-image-generic-pae (= 3.2.0.56.66) but 3.2.0.60.71 is to be installed
  **linux-headers-generic-pae** : Depends: linux-headers-3.2.0-56-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
These two packages are outdated versions of metapackages. All that has to be done is get them updated to the latest version, which already matches the installed versions of its dependencies, or completely remove them to reinstall later. I was thinking of```
sudo dpkg --remove linux-generic-pae
sudo dpkg --remove linux-headers-generic-pae
sudo apt-get update
sudo apt-get install -f
sudo apt-get install linux-generic-pae
```(linux-headers-generic-pae, being a dependency of linux-generic-pae, should be installed automatically)
I don't think anything depends on linux-generic-pae. If some package does, I think it would be a metapackage, which is safe to remove temporarily.

This might be the right direction.

---

### Post by Bashing-om on 2014-04-25
calebjcook; Hello;

@ Impavidus; Thanks, I more than tend to agree .
Consider:

Removing linux-generic will do no harm at all. It is only a "meta-package" depending on linux-image-generic and linux-headers-generic. Those two are themselves meta-packages depending on the respective latest image/headers packages.

You can see this for yourself by issuing apt-cache show linux-generic, apt-cache show linux-image-generic, apt-cache show linux-image-generic-pae and apt-cache show linux-headers-generic. I bet the reflection is dependencies on old kernels.

The purpose of meta-packages is to pull-in the packages on which they depend, they have no functionality at all. On the other hand removing one will not remove it's dependencies - so no danger to the system.

After having fixed the original issue, calebjcook, you can of course install linux-generic again. - 
Which we will. ('sudo apt-get install linux-generic-pae').


I do expect this 
[INDENT][INDENT]to get us past this blockage
[/INDENT][/INDENT]

---

### Post by calebjcook on 2014-04-29
> These two packages are outdated versions of metapackages. All that has to be done is get them updated to the latest version, which already matches the installed versions of its dependencies, or completely remove them to reinstall later. I was thinking of

```
sudo dpkg --remove linux-generic-pae
sudo dpkg --remove linux-headers-generic-pae
sudo apt-get update
sudo apt-get install -f
sudo apt-get install linux-generic-pae
```(linux-headers-generic-pae, being a dependency of linux-generic-pae, should be installed automatically)
I don't think anything depends on linux-generic-pae. If some package does, I think it would be a metapackage, which is safe to remove temporarily.

This might be the right direction.

this has done it!

today i was able to fix this thing at last and have cURL and all the other good stuff working as it should. no more errors. 

thank you, [COLOR=#000000]Bashing-om for your persistence and [/COLOR][COLOR=#000000]Impavidus for not forgetting!

cheers to you both and have a great week,

c.


[/COLOR]

---

### Post by Impavidus on 2014-04-29
Great.

Could you mark the thread as solved? Click thread tools (above the first post of the page) &#8594; mark as solved.

---

### Post by Bashing-om on 2014-04-29
calebjcook & Impavidus :

+1, job well done.

@ calebjcook, Quite welcome, all we ask is pass it on .

[INDENT]ubuntu:
[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT]

---

