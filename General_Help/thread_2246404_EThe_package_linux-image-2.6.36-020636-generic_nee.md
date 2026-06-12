---
title: "E:The package linux-image-2.6.36-020636-generic needs to be reinstalled, but I can't"
date: 2014-09-30
forum: General Help
---

### Post by jpiserhard on 2014-09-30
Hi, I'm new on Ubuntu and I don't know too much about linux. I'm using the version 14.04 and I have some problems with my webcam microsoft lifecam vx-1000, the microphone doesn't working. So I search on google and find some tips, and try but the microphone still not working. So I went to sleep and shutdown my computer and in the other day I switched on my computer and appears a message: E:The package linux-image-2.6.36-020636-generic needs to be reinstalled, but I can't find a archive for it.
Since then I can't install or uninstall anything, my Ubuntu Software Centre don't work (he don't open anymore), and everything I try on terminal don't work because show the message: E:The package linux-image-2.6.36-020636-generic needs to be reinstalled, but I can't find a archive for it.
I've tried the GRUB and doesn't work too. Please, someone can help me? 


OBS: since I'm don't know too much, try to be the most clear you can.

---

### Post by matt_symes on 2014-09-30
Hi

> **jpiserhard said:**
> Hi, I'm new on Ubuntu and I don't know too much about linux. I'm using the version 14.04 and I have some problems with my webcam microsoft lifecam vx-1000, the microphone doesn't working. So I search on google and find some tips, and try but the microphone still not working. So I went to sleep and shutdown my computer and in the other day I switched on my computer and appears a message: E:The package linux-image-2.6.36-020636-generic needs to be reinstalled, but I can't find a archive for it.
Since then I can't install or uninstall anything, my Ubuntu Software Centre don't work (he don't open anymore), and everything I try on terminal don't work because show the message: E:The package linux-image-2.6.36-020636-generic needs to be reinstalled, but I can't find a archive for it.
I've tried the GRUB and doesn't work too. Please, someone can help me? 


OBS: since I'm don't know too much, try to be the most clear you can.

You really don't want to be following random instructions on the net if you don't know what they do. At an absolute minimum you want to make sure the instructions are up to date.

linux-image-2.6.36-020636-generic is an old kernel from the Ubuntu 10.10 (Maverick) days - IIRC. That is why it can't find the kernel in the archive for 14.04 (Trusty).

You want to purge this kernel.

Try this. Open a terminal and type

```
sudo apt-get purge linux-image-2.6.36-020636-generic
```

If that does not work because the kernel name is incorrect, post the results of this command into your next post.

```
dpkg -l | egrep "linux-image|linux-image-extra|linux-headers"
```

Someone can then talk you through removing the old kernel using the correct kernel name.

Kind regards

---

### Post by jpiserhard on 2014-09-30
> **matt_symes said:**
> Hi



You really don't want to be following random instructions on the net if you don't know what they do. At an absolute minimum you want to make sure the instructions are up to date.

linux-image-2.6.36-020636-generic is an old kernel from the Ubuntu 10.10 (Maverick) days - IIRC. That is why it can't find the kernel in the archive for 14.04 (Trusty).

You want to purge this kernel.

Try this. Open a terminal and type

```
sudo apt-get purge linux-image-2.6.36-020636-generic
```

If that does not work because the kernel name is incorrect, post the results of this command into your next post.

```
dpkg -l | egrep "linux-image|linux-image-extra|linux-headers"
```

Someone can then talk you through removing the old kernel using the correct kernel name.

Kind regards


The first code doesn't work, so here are the results of the second command:

joao@JOAO-PC:~$ dpkg -l | egrep "linux-image|linux-image-extra|linux-headers"
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                                     3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                             3.13.0-36.63                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.36.43                                        amd64        Generic Linux kernel headers
rHR linux-image-2.6.36-020636-generic                           2.6.36-020636.201010210905                          amd64        Linux kernel image for version 2.6.36 on x86/x86_64
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                               3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.36.43                                        amd64        Generic Linux kernel image

---

### Post by Bashing-om on 2014-09-30
jpiserhard; Hi !

I will nudge this along just a tad bit:
The error condition that we have :
> 
[color=red]rHR[/color] linux-image-2.6.36-020636-generic 2.6.36-020636.201010210905 amd64 Linux kernel image for version 2.6.36 on x86/x86_64

Where:
r = (r)emoved
H = (H)alf installed
R = (r)einstallation is required.

I take it that the package manager knows what it is talking about when it reports that it is "required" !

So does that mean in fact that the better course here is to down load and install from:
 [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/)

And then try and 'purge' it once it is fully installed ?

 @jpiserhard that said, others may have a much better alternative !

[INDENT][INDENT]the good news is
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jpiserhard on 2014-10-01
> **Bashing-om said:**
> jpiserhard; Hi !

I will nudge this along just a tad bit:
The error condition that we have :

Where:
r = (r)emoved
H = (H)alf installed
R = (r)einstallation is required.

I take it that the package manager knows what it is talking about when it reports that it is "required" !

So does that mean in fact that the better course here is to down load and install from:
 [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/)

And then try and 'purge' it once it is fully installed ?

 @jpiserhard that said, others may have a much better alternative !
[INDENT][INDENT]the good news is[INDENT][INDENT][INDENT]it is fixable
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


But my ubuntu software center are not working. He open and freeze on a white screen with a circle of loading and stay this way forever.

---

### Post by Bashing-om on 2014-10-01
jpiserhard; Hey;

That is alright that the "Software Center" is not available, I have in mind to use the terminal and "wget" those files (3 of them).
Once we have them on the system, we can 'dpkg -i' and install them.
Unless there is a pressing need to get this box back in service, I still want to get other's opinions on a better course of action. Messing about with old obsolete kernels is just not something I am real comfortable with. 

[INDENT][INDENT]it is possible
[/INDENT][/INDENT]

---

### Post by matt_symes on 2014-10-01
Hi

You could also try to remove the kernel using dpkg.

```
sudo dpkg -P linux-image-2.6.36-020636-generic
```

BTW: When you say "it did not work" then please post the output of any errors that the terminal displayed.

It will make life much easier to help you and may give us some clues as to why "it did not work".

Hey bashing-om. Hope you're well.

Kind regards

---

### Post by Bashing-om on 2014-10-01
@jpiserhard;

See the esteemed matt_symes advise ^^ !
I am most interested to see if the "dpkg -P" works around the package manager's requirement "R = (r)einstallation is required."

@ Matt; Doing well, proceeding on my merry way at my slow pace. Always a pleasure of mine to see you pop in here. It is great that you find that time.
I trust things are well in your world.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by jpiserhard on 2014-10-01
> **Bashing-om said:**
> jpiserhard; Hey;

That is alright that the "Software Center" is not available, I have in mind to use the terminal and "wget" those files (3 of them).
Once we have them on the system, we can 'dpkg -i' and install them.
Unless there is a pressing need to get this box back in service, I still want to get other's opinions on a better course of action. Messing about with old obsolete kernels is just not something I am real comfortable with. 
[INDENT][INDENT]it is possible
[/INDENT]
[/INDENT]


I'm sorry, but how could I do to install the files by the terminal?

---

### Post by jpiserhard on 2014-10-01
> **matt_symes said:**
> Hi

You could also try to remove the kernel using dpkg.

```
sudo dpkg -P linux-image-2.6.36-020636-generic
```

BTW: When you say "it did not work" then please post the output of any errors that the terminal displayed.

It will make life much easier to help you and may give us some clues as to why "it did not work".

Hey bashing-om. Hope you're well.

Kind regards

I tried remove the kernel using dpkg, but the result was:

joao@JOAO-PC:~$ sudo dpkg -P linux-image-2.6.36-020636-generic
dpkg: error processing package linux-image-2.6.36-020636-generic (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 linux-image-2.6.36-020636-generic


Kind regards,
João Pedro Haeser Iserhard

---

### Post by Bashing-om on 2014-10-01
jpiserhard; OK ;

Let's give this a try (!!) and see what happens.
Change directory to where we want to work from:
```

cd /var/cache/apt/archives

```
Now "wget" the files I think we need - and install then :
copy and paste:
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-headers-2.6.36-02063602-generic_2.6.36-02063602.201012101121_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-headers-2.6.36-02063602_2.6.36-02063602.201012101121_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-image-2.6.36-02063602-generic_2.6.36-02063602.201012101121_amd64.deb

sudo dpkg -i linux*.deb

```
Return to the /home directory as the Present Working Directory (pwd):
```

cd

```

If the install goes well. next is to purge what we just installed !

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by jpiserhard on 2014-10-01
> **Bashing-om said:**
> jpiserhard; OK ;

Let's give this a try (!!) and see what happens.
Change directory to where we want to work from:
```

cd /var/cache/apt/archives

```
Now "wget" the files I think we need - and install then :
copy and paste:
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-headers-2.6.36-02063602-generic_2.6.36-02063602.201012101121_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-headers-2.6.36-02063602_2.6.36-02063602.201012101121_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-image-2.6.36-02063602-generic_2.6.36-02063602.201012101121_amd64.deb

sudo dpkg -i linux*.deb

```
Return to the /home directory as the Present Working Directory (pwd):
```

cd

```

If the install goes well. next is to purge what we just installed ![INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]


The installation was successful, but how do I delete?

kind regards,
João Pedro Haeser Iserhard

---

### Post by Bashing-om on 2014-10-01
jpiserhard; Well !

OK, let's see if what was installed with wget, is the same same" 2.6.36-020636-generic ".
```

sudo dpkg -P linux-image-2.6.36-020636-generic
sudo dpkg -P linux-header-2.6.36-020636-generic
sudo dpkg -P linux-image-2.6.36-020636

```

advise on results,
[INDENT][INDENT]fingers are crossed
[/INDENT][/INDENT]

---

### Post by jpiserhard on 2014-10-01
> **Bashing-om said:**
> jpiserhard; Well !

OK, let's see if what was installed with wget, is the same same" 2.6.36-020636-generic ".
```

sudo dpkg -P linux-image-2.6.36-020636-generic
sudo dpkg -P linux-header-2.6.36-020636-generic
sudo dpkg -P linux-image-2.6.36-020636

```

advise on results,[INDENT][INDENT]fingers are crossed
[/INDENT]
[/INDENT]


Those are the results: 

joao@JOAO-PC:~$ sudo dpkg -P linux-image-2.6.36-020636-generic
[sudo] password for joao: 
dpkg: error processing package linux-image-2.6.36-020636-generic (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 linux-image-2.6.36-020636-generic

---

### Post by Bashing-om on 2014-10-01
jpiserhard; Shucks !

Obviously not the desired result. Is not the kernel we installed the kernel we want un-installed ?? let's look :
Post back - between code tags - to maintain readability, the output of terminal command:
```

dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Looking for a way to remove this problematic kernel !

[INDENT][INDENT]gotta be a way
[/INDENT][/INDENT]

---

### Post by jpiserhard on 2014-10-01
> **Bashing-om said:**
> jpiserhard; Shucks !

Obviously not the desired result. Is not the kernel we installed the kernel we want un-installed ?? let's look :
Post back - between code tags - to maintain readability, the output of terminal command:
```

dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Looking for a way to remove this problematic kernel ![INDENT][INDENT]gotta be a way
[/INDENT]
[/INDENT]


Ok, so the result was:

```
joao@JOAO-PC:~$ sudo dpkg -l | grep linux-[sudo] password for joao: 
ii  linux-firmware                                              1.127.7                                             all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.36.43                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-2.6.36-02063602                               2.6.36-02063602.201012101121                        all          Header files related to Linux kernel version 2.6.36
ii  linux-headers-2.6.36-02063602-generic                       2.6.36-02063602.201012101121                        amd64        Linux kernel headers for version 2.6.36 on x86/x86_64
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                                     3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                             3.13.0-36.63                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.36.43                                        amd64        Generic Linux kernel headers
pHR linux-image-2.6.36-020636-generic                           2.6.36-020636.201010210905                          amd64        Linux kernel image for version 2.6.36 on x86/x86_64
ii  linux-image-2.6.36-02063602-generic                         2.6.36-02063602.201012101121                        amd64        Linux kernel image for version 2.6.36 on x86/x86_64
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                               3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.36.43                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-36.63                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies



```

Thank for helping me.

---

### Post by jpiserhard on 2014-10-01
> **Bashing-om said:**
> jpiserhard; Shucks !

Obviously not the desired result. Is not the kernel we installed the kernel we want un-installed ?? let's look :
Post back - between code tags - to maintain readability, the output of terminal command:
```

dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Looking for a way to remove this problematic kernel ![INDENT][INDENT]gotta be a way
[/INDENT]
[/INDENT]


Ok, so the result was:

```
joao@JOAO-PC:~$ sudo dpkg -l | grep linux-[sudo] password for joao: 
ii  linux-firmware                                              1.127.7                                             all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.36.43                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-2.6.36-02063602                               2.6.36-02063602.201012101121                        all          Header files related to Linux kernel version 2.6.36
ii  linux-headers-2.6.36-02063602-generic                       2.6.36-02063602.201012101121                        amd64        Linux kernel headers for version 2.6.36 on x86/x86_64
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                                     3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                             3.13.0-36.63                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.36.43                                        amd64        Generic Linux kernel headers
pHR linux-image-2.6.36-020636-generic                           2.6.36-020636.201010210905                          amd64        Linux kernel image for version 2.6.36 on x86/x86_64
ii  linux-image-2.6.36-02063602-generic                         2.6.36-02063602.201012101121                        amd64        Linux kernel image for version 2.6.36 on x86/x86_64
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                               3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.36.43                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-36.63                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies



```

Thank you for helping me.

---

### Post by jpiserhard on 2014-10-01
> **Bashing-om said:**
> jpiserhard; Shucks !

Obviously not the desired result. Is not the kernel we installed the kernel we want un-installed ?? let's look :
Post back - between code tags - to maintain readability, the output of terminal command:
```

dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Looking for a way to remove this problematic kernel ![INDENT][INDENT]gotta be a way
[/INDENT]
[/INDENT]


Ok, so the result was:

```
joao@JOAO-PC:~$ sudo dpkg -l | grep linux-[sudo] password for joao: 
ii  linux-firmware                                              1.127.7                                             all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.36.43                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-2.6.36-02063602                               2.6.36-02063602.201012101121                        all          Header files related to Linux kernel version 2.6.36
ii  linux-headers-2.6.36-02063602-generic                       2.6.36-02063602.201012101121                        amd64        Linux kernel headers for version 2.6.36 on x86/x86_64
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                                     3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                             3.13.0-36.63                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.36.43                                        amd64        Generic Linux kernel headers
pHR linux-image-2.6.36-020636-generic                           2.6.36-020636.201010210905                          amd64        Linux kernel image for version 2.6.36 on x86/x86_64
ii  linux-image-2.6.36-02063602-generic                         2.6.36-02063602.201012101121                        amd64        Linux kernel image for version 2.6.36 on x86/x86_64
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                               3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.36.43                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-36.63                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies



```

---

### Post by Bashing-om on 2014-10-02
jpiserhard; UnGood,

Shucks, not the same versions !:
> 
pHR linux-image-2.6.36-020636-generic 
ii      linux-image-2.6.36-02063602-generic 


Back to seeing what I can do to find that where we can find that correct version to (re-)install.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by Elfy on 2014-10-02
```
sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.36-020636-generic
```

why are we trying to install old kernels in addition to old kernels we're trying to remove?

---

### Post by JKyleOKC on 2014-10-02
What happens if you try ```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-image-2.6.36-02063602-generic_2.6.36-020636.201012101121_amd64.deb
```instead? Note that I made the package name match what was in your last list with the "pHR" prefix. I expect this will probably return an error message that the package does not exist, but in the unlikely event that it does grab the file, then follow through Bashing-om's directions for installing and then purging it and let us know what happens.

---

### Post by JKyleOKC on 2014-10-02
> **Elfy said:**
> ```
sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.36-020636-generic
```

why are we trying to install old kernels in addition to old kernels we're trying to remove?
Because dpkg is insisting that it be reinstalled before it can be removed.

If there's a simpler way to get it out of the queue we'd all love to know about it!!! Is this what you've suggested? If so, many thanks and we've all picked up an additional tool...

---

### Post by Elfy on 2014-10-02
> **JKyleOKC said:**
> Because dpkg is insisting that it be reinstalled before it can be removed.

If there's a simpler way to get it out of the queue we'd all love to know about it!!!

the force remove reinstreq thingy has worked for me in the past

Edit - from what I can gather you should normally only see 2 letters as dpkg flags, the addition of the 3rd r signifies an error.

From the dpkg man pages

> Package flags
       reinst-required
              A package marked reinst-required is broken  and  requires  rein&#8208;
              stallation. These packages cannot be removed, unless forced with
              option --force-remove-reinstreq.

---

### Post by Bashing-om on 2014-10-02
> **Elfy said:**
> the force remove reinstreq thingy has worked for me in the past

Edit - from what I can gather you should normally only see 2 letters as dpkg flags, the addition of the 3rd r signifies an error.

From the dpkg man pages

@Elfy .. As I live and learn !
Sure worth a shot ! 

[INDENT][INDENT]thanks heaps
[/INDENT][/INDENT]

---

### Post by jpiserhard on 2014-10-02
> **JKyleOKC said:**
> What happens if you try ```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-image-2.6.36-02063602-generic_2.6.36-020636.201012101121_amd64.deb
```instead? Note that I made the package name match what was in your last list with the "pHR" prefix. I expect this will probably return an error message that the package does not exist, but in the unlikely event that it does grab the file, then follow through Bashing-om's directions for installing and then purging it and let us know what happens.

The attempt was valid, unfortunately this was the result

```
joao@JOAO-PC:~$ sudo wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-image-2.6.36-02063602-generic_2.6.36-020636.201012101121_amd64.deb
[sudo] password for joao: 
--2014-10-02 20:13:37--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/linux-image-2.6.36-02063602-generic_2.6.36-020636.201012101121_amd64.deb
Solving kernel.ubuntu.com (kernel.ubuntu.com)... failed: Name or service unkwown.
wget: could not resolve host address &#8220;kernel.ubuntu.com&#8221;
```

---

### Post by matt_symes on 2014-10-02
Hi

Looks like it's not going too well. 

I would be interested to know why the kernel failed to install in the first place. Is it because it is an old kernel ? Can you shed any lighnt on why it did not install ?

Reinstalling the same (2.6.36) kernel on 14.04 may just leave you the same position - an inconsistent kernel package - you are in now and may not fix your problem anyway.

If all else fails, we could try a manual purge of the kernel from your system.

At a minimum, this would entail deleting the kernel, initramfs, map and other files from /boot. 
Removing the offending package reference from dpkg's status file. 
Removing any modules it installed under /lib/modules. 
Removing any firmware packages installed under /lib/firmware.
Removing and dkms packages it may have built.

As you can boot the system, i assume it's not booting into that 2.6.36 kernel so grub may not need to be updated.

In preparation for this eventuality, can you post the output of these commands.

```
uname -a
```
```
zgrep linux-image-2.6.36-020636-generic /var/log/dpkg*
```
```
ls /boot/*2.6.36*
```
```
ls -d /lib/modules/*2.6.36*
```
```
ls -d /lib/firmware/*2.6.36*
```
```
ls -d /var/lib/dkms/*/*
```

Please post all the output from the above between code tags.

You have posted so little information on what you did to create the problem (not even a link to the tutorial you followed), I'm not even sure how you installed the kernel. wget and dpkg ? Some unusual PPA and apt ? 


Anyway, backup you existing data if you want to try a manual purge and post back the output from the comands above as it may break your system.

I may not be about tomorrow so others will help you. Get them to look through this next advice as it's very late here and i need a second opinion as i'm tired.

You'll be looking at something like this to remove the reference from dpkg's status file.

```
sudo sed -i '/Package: linux-image-2.6.36-020636-generic/,/^$/!d' /var/lib/dpkg/status
```

To delete the kernel files something like this.

```
sudo rm -r /boot/*2.6.36* /lib/modules/*2.6.36* /lib/firmware/2.6.36
```

Check to see if dkms has built any modules.
Check to see if grub needs recreating (i doubt this but as i said, it's late here).

Kind regards

---

### Post by jpiserhard on 2014-10-03
> **matt_symes said:**
> Hi

Looks like it's not going too well. 

I would be interested to know why the kernel failed to install in the first place. Is it because it is an old kernel ? Can you shed any lighnt on why it did not install ?

Reinstalling the same (2.6.36) kernel on 14.04 may just leave you the same position - an inconsistent kernel package - you are in now and may not fix your problem anyway.

If all else fails, we could try a manual purge of the kernel from your system.

At a minimum, this would entail deleting the kernel, initramfs, map and other files from /boot. 
Removing the offending package reference from dpkg's status file. 
Removing any modules it installed under /lib/modules. 
Removing any firmware packages installed under /lib/firmware.
Removing and dkms packages it may have built.

As you can boot the system, i assume it's not booting into that 2.6.36 kernel so grub may not need to be updated.

In preparation for this eventuality, can you post the output of these commands.

```
uname -a
```
```
zgrep linux-image-2.6.36-020636-generic /var/log/dpkg*
```
```
ls /boot/*2.6.36*
```
```
ls -d /lib/modules/*2.6.36*
```
```
ls -d /lib/firmware/*2.6.36*
```
```
ls -d /var/lib/dkms/*/*
```

Please post all the output from the above between code tags.

You have posted so little information on what you did to create the problem (not even a link to the tutorial you followed), I'm not even sure how you installed the kernel. wget and dpkg ? Some unusual PPA and apt ? 


Anyway, backup you existing data if you want to try a manual purge and post back the output from the comands above as it may break your system.

I may not be about tomorrow so others will help you. Get them to look through this next advice as it's very late here and i need a second opinion as i'm tired.

You'll be looking at something like this to remove the reference from dpkg's status file.

```
sudo sed -i '/Package: linux-image-2.6.36-020636-generic/,/^$/!d' /var/lib/dpkg/status
```

To delete the kernel files something like this.

```
sudo rm -r /boot/*2.6.36* /lib/modules/*2.6.36* /lib/firmware/2.6.36
```

Check to see if dkms has built any modules.
Check to see if grub needs recreating (i doubt this but as i said, it's late here).

Kind regards

Here are the results:
```
joao@JOAO-PC:~$ uname -a
Linux JOAO-PC 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

```
joao@JOAO-PC:~$ zgrep linux-image-2.6.36-020636-generic /var/log/dpkg*
/var/log/dpkg.log:2014-10-01 14:45:11 status half-installed linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log:2014-10-01 14:49:30 status half-installed linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log:2014-10-01 21:59:45 status half-installed linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log:2014-10-01 22:01:30 status half-installed linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log:2014-10-01 22:02:12 status half-installed linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:10:13 install linux-image-2.6.36-020636-generic:amd64 <none> 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:10:13 status half-installed linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:10:27 status unpacked linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:10:27 status unpacked linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:10:27 configure linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:10:27 status unpacked linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:10:27 status half-configured linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:10:47 status installed linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:12:21 upgrade linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:12:21 status half-configured linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:12:22 status unpacked linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-28 20:12:23 status half-installed linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
/var/log/dpkg.log.1:2014-09-29 18:59:27 status half-installed linux-image-2.6.36-020636-generic:amd64 2.6.36-020636.201010210905
```

```
joao@JOAO-PC:~$ ls /boot/*2.6.36*
/boot/abi-2.6.36-02063602-generic         /boot/config-2.6.36-020636-generic.dpkg-tmp  /boot/System.map-2.6.36-020636-generic.dpkg-tmp
/boot/abi-2.6.36-020636-generic           /boot/initrd.img-2.6.36-02063602-generic     /boot/vmlinuz-2.6.36-02063602-generic
/boot/abi-2.6.36-020636-generic.dpkg-tmp  /boot/initrd.img-2.6.36-020636-generic       /boot/vmlinuz-2.6.36-020636-generic
/boot/config-2.6.36-02063602-generic      /boot/System.map-2.6.36-02063602-generic     /boot/vmlinuz-2.6.36-020636-generic.dpkg-tmp
/boot/config-2.6.36-020636-generic        /boot/System.map-2.6.36-020636-generic
```

```
joao@JOAO-PC:~$ ls -d /lib/modules/*2.6.36*
/lib/modules/2.6.36-02063602-generic  /lib/modules/2.6.36-020636-generic
```

```
joao@JOAO-PC:~$ ls -d /lib/firmware/*2.6.36*
/lib/firmware/2.6.36-02063602-generic  /lib/firmware/2.6.36-020636-generic
```

```
joao@JOAO-PC:~$ ls -d /var/lib/dkms/*/*
ls: can not acess /var/lib/dkms/*/*: File or directory not found
```

So, I installed the Kernel as the answer to this [question]("http://askubuntu.com/questions/3557/how-can-i-get-my-microsoft-lifecam-vx-1000-webcam-microphone-to-work"), I installed according to option 1.

Could you please explain more about the manual purge? How do I do the backup of my existing data? what archives should I save? 

Sorry for troubling you guys and I appreciate so much your help.

---

### Post by Elfy on 2014-10-03
unsubscribing

---

### Post by matt_symes on 2014-10-03
Hi

Righttty. Now i see what you were trying to do. I want to point some things out.

AskUbuntu is generally a good site to get information however the advice you were following was from a question posted in 2010. 

Things in the Linux world move fast an solutions from 2010 can, but not always, be wildly out of date. A judgment call and further research are usually required to see if the answer is still valid under the system you are trying to configure or fix.

The advice itself looks solid and states....

> According to the GSPCA, this fix will be included in kernel 2.6.36 and  newer. So until Ubuntu uses kernel 2.6.36 or newer, you will need to  install the updated drivers yourself.

I have not verified the answer myself however with 4 up votes and a +50 bounty given for the answer i would suggest the answer is most lightly correct although i would still want to verify the fix myself before applying it on any system i run.

The point is the advice states that kernel 2.6.36 and newer will contain the fix however you are already on a far newer kernel that should already contain the fix (3.xx). You did not need to install any kernels at all. The advice in your case is redundant and only applied to Maverick installations with a kernel version less than 2.6.36 and Ubuntu distribution previous to maverick. As all these versions (apart from 10.04 server) are EOL, the advice, although pertinent at the time, is now totally irrelevant unless, for what ever reason, you are still running a distribution that old.  

The kernel you installed is an old mainline kernel that may not contain all the Ubuntu sauce required to run correctly, let alone install itself and run all its configuration scripts.

> Could you please explain more about the manual purge?

Anytime you install anything on your system using the package manager a number of predefined things happen. Files get placed in certain locations on your hard drive, the package managers status gets updated, configuration files within the packages themselves get called to perform extra configuration. These steps can be manually reversed by typing commands into the terminal.

The kernel is the single most complex set of packages you can install on your system. Not only are files placed on your hard drive and the package manager's status updated but the configuration files called by the packages perform a host of other operations and these include, but are not limited to, building modules from source code using the dkms framework - on this laptop the bcmwl drive is compiled so i can have usable wireless -, depmod is called to create the kernel module dependency files, an initramfs file is created to help boot the system and grub is called to update grub to boot the new kernel. It is possible to reverse all these steps. I have done it myself.

I asked for a second opinion about my advice for a number of reasons, not least because manually removing a kernel can go wrong.

You see ...

> How do I do the backup of my existing data? what archives should I save?

... that really worries me as that is a pretty basic question to ask when you are about to manually purge a kernel.

> **Elfy said:**
> unsubscribing

I admire and respect Elfy greatly. He's a good old bean and i suspect this is his way of advising me on whether he feels i should be proffering this solution in the first place.

You see the advice on AskUbuntu you initially followed contained within it some unstated presumptions. Besides advising the installation of a mainline kernel which in itself could be considered an unusual solution, it also presumed knowledge of how to pin the kernel so that standard updates would not remove the kernel as the boot kernel. It also presumed knowledge of how to remove that pinning when the kernel with the fix became available and how to identify when that kernel was available. At the time, this was necessary.

If i was to outline how to manually remove the kernel then i could be offering advice that someone in the future may blindly follow (not understanding my unstated presumptions) as manually purging any package, let alone the kernel, is most definitely a very unusual operation and is only ever performed as a last resort. 

This, and not the actual removal of the kernel, is what i suspect is making Elfy uneasy and on reflection, after sipping my morning coffee, it troubles me as well.

Ubuntu was always designed to be an easy to use Linux distribution. It achieved that in spades. Manually removing packages goes against that ethos.

In the same way that you can get into the bowels of a Windows box to fix a surprising number of problems, you can also under Linux. However, i wonder if the Ubuntu Forums is the place to be exploring these solutions.

Kind regards

---

### Post by matt_symes on 2014-10-03
Hi

Anyway, now we have a better handle on what you were trying to achieve let's see if we can reinstall the kernel and see what errors it throws back at us.

But first: I assumed you did but, after reading the entire thread i'm not sure; did you try Elfy's command ?

Open a terminal and type

```
sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.36-020636-generic
```

If you have not already, try the above command as it should work unless you had a situation like i had when i had to manually purge a kernel.

Anyway, assuming you have run the above command and it did not work, open a terminal and copy and paste this into it.

```
cd ~ && mkdir tmp && cd $_ && wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_amd64.deb
```

It will move you to your home folder, create a directory call tmp, move into that directory and download the 64bit version of the kernel into that folder using wget.

We will then have a copy of the deb and can try some commands to see if we can successfully reinstall the kernel to later remove it and, more importantly, we should be able to see why it's failing to install if it will not reinstall.

Kind regards

---

### Post by jpiserhard on 2014-10-03
> **matt_symes said:**
> Hi

Anyway, now we have a better handle on what you were trying to achieve let's see if we can reinstall the kernel and see what errors it throws back at us.

But first: I assumed you did but, after reading the entire thread i'm not sure; did you try Elfy's command ?

Open a terminal and type

```
sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.36-020636-generic
```

If you have not already, try the above command as it should work unless you had a situation like i had when i had to manually purge a kernel.

Anyway, assuming you have run the above command and it did not work, open a terminal and copy and paste this into it.

```
cd ~ && mkdir tmp && cd $_ && wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_amd64.deb
```

It will move you to your home folder, create a directory call tmp, move into that directory and download the 64bit version of the kernel into that folder using wget.

We will then have a copy of the deb and can try some commands to see if we can successfully reinstall the kernel to later remove it and, more importantly, we should be able to see why it's failing to install if it will not reinstall.

Kind regards

Hi, I confess that I was very distracted when I installed this Kernel too old. I never used Linux in my entire life, so I go taking this big mistake as a big lesson. About the Elfys's command, I completely forgot to run the command. So I put the command and that was the result: 

```
joao@JOAO-PC:~$ sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.36-020636-generic[sudo] password for joao: 
dpkg: warning: problem to overcome because --force is active:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
(Reading database ... 286752 files and directories currently installed.)
Removing linux-image-2.6.36-020636-generic (2.6.36-020636.201010210905) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.36-020636-generic /boot/vmlinuz-2.6.36-020636-generic
update-initramfs: Deleting /boot/initrd.img-2.6.36-020636-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.36-020636-generic /boot/vmlinuz-2.6.36-020636-generic
Generating grub configuration file ...
Attention: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found image initrd: /boot/initrd.img-3.13.0-36-generic
Found image linux: /boot/vmlinuz-3.13.0-35-generic
Found image initrd: /boot/initrd.img-3.13.0-35-generic
Found image linux: /boot/vmlinuz-3.13.0-24-generic
Found image initrd: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-2.6.36-02063602-generic
Found image initrd: /boot/initrd.img-2.6.36-02063602-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
completed
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]

```

Kind regards,
João Pedro Haeser Iserhard

---

### Post by matt_symes on 2014-10-03
Hi

That looks much better and your system is not as half as damaged as i though it was.

Anyway, to make sure your system is working correctly, let's follow the advice from the last dpkg command you ran.

Open a terminal and run this command

```
sudo update-grub
```

Then type 

```
sudo apt-get update && sudo apt-get upgrade
```

The above commands should not return any errors.

Finally can you post the output of the commands below so we can check your kernel and initramfs symlinks.

```
ls -l /vmlinuz* /initrd.img
```

Kind regards

---

### Post by jpiserhard on 2014-10-03
> **matt_symes said:**
> Hi

That looks much better and your system is not as half as damaged as i though it was.

Anyway, to make sure your system is working correctly, let's follow the advice from the last dpkg command you ran.

Open a terminal and run this command

```
sudo update-grub
```

Then type 

```
sudo apt-get update && sudo apt-get upgrade
```

The above commands should not return any errors.

Finally can you post the output of the commands below so we can check your kernel and initramfs symlinks.

```
ls -l /vmlinuz* /initrd.img
```

Kind regards

Now I already can enter on ubuntu software center and the warning on the top (the red ball with a white risk in the center) is gone. So here are the results:
```
joao@JOAO-PC:~$ ls -l /vmlinuz* /initrd.imglrwxrwxrwx 1 root root 40 Out  1 20:15 /initrd.img -> /boot/initrd.img-2.6.36-02063602-generic
lrwxrwxrwx 1 root root 36 Out  1 20:15 /vmlinuz -> boot/vmlinuz-2.6.36-02063602-generic
```

Thank you so much guys!

---

### Post by Bashing-om on 2014-10-04
jpiserhard; Ummphh;

Do not consider, myself, that we are done here - yet .
Looks like you are booting:
> 
lrwxrwxrwx 1 root root 36 Out  1 20:15 /vmlinuz -> boot/vmlinuz-2.6.36-02063602-generic


Rather than the latest kernel:
> 
Found linux image: /boot/vmlinuz-3.13.0-36-generic

That is installed.

As 'update-initramfs:' has been called, I can not explain why you are set to boot with that old kernel:

@ Matt, can you shed some light on this ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by matt_symes on 2014-10-04
Hi Bashing-om

> **Bashing-om said:**
> jpiserhard; Ummphh;

Do not consider, myself, that we are done here - yet .
Looks like you are booting:


Rather than the latest kernel:

That is installed.

As 'update-initramfs:' has been called, I can not explain why you are set to boot with that old kernel:

@ Matt, can you shed some light on this ?
[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


When you call update-grub, one of the things it can do is to look through the kernels installed in /boot and add them to the file /boot/grub/grub.cfg in the order they were created in that directory from the newest to the oldest.

This is how you get the newest kernel to appear first in the grub menu for Ubuntu.

Grub uses this file (/boot/grub/grub.cfg) generate to the grub menu.

If you want the more details, from the command line...

```
info grub-mkconfig
```

...as update-grub is just a three line script that calls grub-mkconfig.

I believe it's the process of installing a kernel that creates the symlinks to point to the new kernel (one of the scripts does this, i believe) although i would have to check to be sure.

The symlinks are not required by grub to boot into the default,newest,last,user-selected kernel.

One example of where the symlinks are useful is when you're on a boot loaders rescue prompt - grubs prompt included - as you only need to know the partition and you know that /vmlinuz will point to the newest kernel and /vmlinux.old will point to the previous kernel. 

There are other uses for them and i'll leave that you for to think about :).

So they are not vital but they are useful. They will be updated when a new kernel is installed anyway.

Kind regards

---

### Post by Bashing-om on 2014-10-04
@ Matt;

Thanks, It is always a process of learning, I Had "assumed" that "update initramfs"  did the same function as "update-grub". Will put my mind to work on this !
(make time to read the scripts !)

Looking forward to this thread working out.

[INDENT][INDENT]what you do not know
[INDENT][INDENT][INDENT]can hurt deeply
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jpiserhard on 2014-10-04
> **matt_symes said:**
> Hi Bashing-om



When you call update-grub, one of the things it can do is to look through the kernels installed in /boot and add them to the file /boot/grub/grub.cfg in the order they were created in that directory from the newest to the oldest.

This is how you get the newest kernel to appear first in the grub menu for Ubuntu.

Grub uses this file (/boot/grub/grub.cfg) generate to the grub menu.

If you want the more details, from the command line...

```
info grub-mkconfig
```

...as update-grub is just a three line script that calls grub-mkconfig.

I believe it's the process of installing a kernel that creates the symlinks to point to the new kernel (one of the scripts does this, i believe) although i would have to check to be sure.

The symlinks are not required by grub to boot into the default,newest,last,user-selected kernel.

One example of where the symlinks are useful is when you're on a boot loaders rescue prompt - grubs prompt included - as you only need to know the partition and you know that /vmlinuz will point to the newest kernel and /vmlinux.old will point to the previous kernel. 

There are other uses for them and i'll leave that you for to think about :).

So they are not vital but they are useful. They will be updated when a new kernel is installed anyway.

Kind regards

So, I don't understand too much about your talking with Bashing-om but, you can say if my ubuntu is completely fixed or is missing something?

Kind regards,
João Pedro Haeser Iserhard

---

### Post by matt_symes on 2014-10-04
Hi

> **jpiserhard said:**
> So, I don't understand too much about your talking with Bashing-om but, you can say if my ubuntu is completely fixed or is missing something?

Kind regards,
João Pedro Haeser Iserhard

There is something that is not quite configured correctly. I don't think it will cause you any major problems but i may have missed something so let's fix it for you.

Open a terminal and type these four commands.

```

sudo rm /vmlinuz
sudo rm /initrd.img
sudo ln -s /boot/vmlinuz-3.13.0-36-generic /vmlinuz
sudo ln -s /boot/initrd.img-3.13.0-36-generic /initrd.img
```

That should fix it but to double check, post back the output this command after running the above.

```
ls -l /vmlinuz* /initrd.img*
```

Kind regards

---

### Post by jpiserhard on 2014-10-04
> **matt_symes said:**
> Hi



There is something that is not quite configured correctly. I don't think it will cause you any major problems but i may have missed something so let's fix it for you.

Open a terminal and type these four commands.

```

sudo rm /vmlinuz
sudo rm /initrd.img
sudo ln -s /boot/vmlinuz-3.13.0-36-generic /vmlinuz
sudo ln -s /boot/initrd.img-3.13.0-36-generic /initrd.img
```

That should fix it but to double check, post back the output this command after running the above.

```
ls -l /vmlinuz* /initrd.img*
```

Kind regards

So I typed the four commands and that was the result:
```
joao@JOAO-PC:~$ sudo rm /vmlinuz[sudo] password for joao: 
rm: can not remove “/vmlinuz”: File or directory not found
joao@JOAO-PC:~$ sudo rm /initrd.img
joao@JOAO-PC:~$ sudo ln -s /boot/vmlinuz-3.13.0-36-generic /vmlinuzsudo ln -s /boot/initrd.img-3.13.0-36-generic /initrd.img
ln: the target “/initrd.img” is not a directory
joao@JOAO-PC:~$ sudo ln -s /boot/initrd.img-3.13.0-36-generic /initrd.img


```

The second and fourth command had no answer. Is that normal?

```
joao@JOAO-PC:~$ ls -l /vmlinuz* /initrd.img*
ls: can not acess /vmlinuz*: File or directory not found
lrwxrwxrwx 1 root root 34 Out  4 20:33 /initrd.img -> /boot/initrd.img-3.13.0-36-generic

```

Kind regards,
João Pedro Haeser Iserhard

---

### Post by Bashing-om on 2014-10-05
jpiserhard; Hello !

I do not know, presently, what to make of this situation, as:
> 
lrwxrwxrwx 1 root root 36 Out 1 20:15 /vmlinuz -> boot/vmlinuz-2.6.36-02063602-generic

That file did exist !
And now it does not ?

Let's take a closer look at what is: Post back the outputs:
```

ls -al /
ls -al /boot

``` and we see what there is here to work with.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]otherTimes I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jpiserhard on 2014-10-05
> **Bashing-om said:**
> jpiserhard; Hello !

I do not know, presently, what to make of this situation, as:

That file did exist !
And now it does not ?

Let's take a closer look at what is: Post back the outputs:
```

ls -al /
ls -al /boot

``` and we see what there is here to work with.
[INDENT][INDENT]sometimes I wonder[INDENT][INDENT][INDENT][INDENT]otherTimes I just do not know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hello, Bashing-om
Here are the outputs:
```
joao@JOAO-PC:~$ ls -al /total 104
drwxr-xr-x  23 root root  4096 Oct  4 20:33 .
drwxr-xr-x  23 root root  4096 Oct  4 20:33 ..
drwxr-xr-x   2 root root  4096 Oct  4 10:05 bin
drwxr-xr-x   3 root root  4096 Oct  4 10:06 boot
drwxrwxr-x   2 root root  4096 Sep 19 18:27 cdrom
drwxr-xr-x  17 root root  4220 Oct  4 20:24 dev
drwxr-xr-x 149 root root 12288 Oct  5 16:35 etc
drwxr-xr-x   3 root root  4096 Sep 19 18:29 home
lrwxrwxrwx   1 root root    34 Oct  4 20:33 initrd.img -> /boot/initrd.img-3.13.0-36-generic
drwxr-xr-x  24 root root  4096 Sep 19 20:45 lib
drwxr-xr-x   2 root root  4096 Sep 19 18:54 lib64
drwx------   2 root root 16384 Sep 19 18:21 lost+found
drwxr-xr-x   3 root root  4096 Sep 19 18:46 media
drwxr-xr-x   2 root root  4096 Apr 10 19:12 mnt
drwxr-xr-x   4 root root  4096 Sep 23 15:22 opt
dr-xr-xr-x 199 root root     0 Oct  4 20:24 proc
drwx------   9 root root  4096 Sep 20 21:07 root
drwxr-xr-x  24 root root   780 Oct  5 07:48 run
drwxr-xr-x   2 root root 12288 Oct  4 10:03 sbin
drwxr-xr-x   2 root root  4096 Apr 16 22:21 srv
dr-xr-xr-x  13 root root     0 Oct  4 20:24 sys
drwxrwxrwt   8 root root  4096 Oct  5 19:17 tmp
drwxr-xr-x  10 root root  4096 Apr 16 22:21 usr
drwxr-xr-x  13 root root  4096 Apr 16 22:29 var
joao@JOAO-PC:~$ ls -al /boot
total 108156
drwxr-xr-x  3 root root     4096 Oct  4 10:06 .
drwxr-xr-x 23 root root     4096 Oct  4 20:33 ..
-rw-r--r--  1 root root   703226 Dec 10  2010 abi-2.6.36-02063602-generic
-rw-r--r--  1 root root  1158016 May  2 21:30 abi-3.13.0-24-generic
-rw-r--r--  1 root root  1163858 Aug 14 23:56 abi-3.13.0-35-generic
-rw-r--r--  1 root root  1163858 Sep  3 19:24 abi-3.13.0-36-generic
-rw-r--r--  1 root root   121036 Dec 10  2010 config-2.6.36-02063602-generic
-rw-r--r--  1 root root   165510 May  2 21:30 config-3.13.0-24-generic
-rw-r--r--  1 root root   165652 Aug 14 23:56 config-3.13.0-35-generic
-rw-r--r--  1 root root   165671 Sep  3 19:24 config-3.13.0-36-generic
drwxr-xr-x  5 root root     4096 Oct  3 17:41 grub
-rw-r--r--  1 root root 13452164 Oct  1 20:15 initrd.img-2.6.36-02063602-generic
-rw-r--r--  1 root root 19091214 Sep 19 19:11 initrd.img-3.13.0-24-generic
-rw-r--r--  1 root root 19155019 Sep 19 19:13 initrd.img-3.13.0-35-generic
-rw-r--r--  1 root root 19168987 Oct  4 10:06 initrd.img-3.13.0-36-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-r--r--  1 root root  2567931 Dec 10  2010 System.map-2.6.36-02063602-generic
-rw-------  1 root root  3372643 May  2 21:30 System.map-3.13.0-24-generic
-rw-------  1 root root  3386444 Aug 14 23:56 System.map-3.13.0-35-generic
-rw-------  1 root root  3386479 Sep  3 19:24 System.map-3.13.0-36-generic
-rw-r--r--  1 root root  4383536 Dec 10  2010 vmlinuz-2.6.36-02063602-generic
-rw-------  1 root root  5776416 May  2 21:30 vmlinuz-3.13.0-24-generic
-rw-------  1 root root  5806368 Aug 14 23:56 vmlinuz-3.13.0-35-generic
-rw-------  1 root root  5806848 Sep  3 19:24 vmlinuz-3.13.0-36-generic

```
Kind regards,

---

### Post by matt_symes on 2014-10-05
Hi

That's rather odd.

First things first, let's run fsck on your root directory just to be sure.

Open a terminal and type (not copy and paste)

```
sudo touch /forcefsck
```

Reboot your PC and let it perform the filing system check.

Now a question: Did you type or copy and paste the commands from my last post into the terminal ?

Kind regards

---

### Post by Bashing-om on 2014-10-05
jpiserhard; Well, 


See Matt's last !

I also have in mind to explore why the command failed.

How about when we see the results of Mattt's methology;
Try again:

```

sudo ln -s /boot/vmlinuz-3.13.0-36-generic /vmlinuz
ls -al /vmlinuz

```
And re-establish the symlink, as "-rw-------  1 root root  5806848 Sep  3 19:24 vmlinuz-3.13.0-36-generic" exists.

I hope I am not misleading or taking away.
[INDENT][INDENT]rhyme and reason
[INDENT][INDENT][INDENT][INDENT]reason prevails
[/INDENT][/INDENT][/INDENT][/INDENT] [/INDENT][/INDENT]

---

### Post by jpiserhard on 2014-10-05
> **matt_symes said:**
> Hi

That's rather odd.

First things first, let's run fsck on your root directory just to be sure.

Open a terminal and type (not copy and paste)

```
sudo touch /forcefsck
```

Reboot your PC and let it perform the filing system check.

Now a question: Did you type or copy and paste the commands from my last post into the terminal ?

Kind regards

Ok, the system check is complete. I copied and pasted the commands from your last post into the terminal, is that a problem? 


Kind regards

---

### Post by matt_symes on 2014-10-05
Hi

Try typing in the last command as highlighted as Bashing-om's last post.

Maybe something went wrong with the copy and paste.

Double check the command before hitting the enter key.

Kind regards

---

### Post by jpiserhard on 2014-10-05
> **matt_symes said:**
> Hi

Try typing in the last command as highlighted as Bashing-om's last post.

Maybe something went wrong with the copy and paste.

Double check the command before hitting the enter key.

Kind regards

I typed the commands of Bashing-om and these were the results: 

```
joao@JOAO-PC:~$ sudo ln -s /boot/vmlinuz-3.13.0-36-generic /vmlinuz[sudo] password for joao: 
joao@JOAO-PC:~$ ls -al /vmlinuz
lrwxrwxrwx 1 root root 31 Oct  5 22:54 /vmlinuz -> /boot/vmlinuz-3.13.0-36-generic

```

Kind regards

---

### Post by matt_symes on 2014-10-05
Hi

That looks better. 

Not sure what went wrong but either the filing system check or typing the command directly seems to have fixed it.

Enjoy.

Kind regards

---

### Post by jpiserhard on 2014-10-06
> **matt_symes said:**
> Hi

That looks better. 

Not sure what went wrong but either the filing system check or typing the command directly seems to have fixed it.

Enjoy.

Kind regards

Thank you for helped me on the last days. 


Kind regards

---

