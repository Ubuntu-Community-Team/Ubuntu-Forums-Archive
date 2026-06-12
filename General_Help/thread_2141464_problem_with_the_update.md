---
title: "problem with the update"
date: 2013-05-02
forum: General Help
---

### Post by balagan on 2013-05-02
Hello everyone,

I'm a newbie here, so sorry for my ignorance..

I have a problem with my Ubuntu and I don't know what to do with that.
After the update not so long time ago I'm not able to install any more updates or programs.

When trying to fix the problem it sais that it is not possible, and I get this from the console:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 455381 files and directories currently installed.)
Unpacking linux-headers-3.2.0-41 (from .../linux-headers-3.2.0-41_3.2.0-41.66_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-41_3.2.0-41.66_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-41/drivers/gpu/stub/Kconfig.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-41/drivers/gpu/stub/Kconfig'): No space left on device
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-41-generic-pae (from .../linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-41-generic-pae/include/config/vxfs/fs.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-41-generic-pae/include/config/vxfs/fs.h'): No space left on device
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-41_3.2.0-41.66_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-40-generic-pae; however:
  Package linux-headers-3.2.0-40-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured

Please for help!

Thank you

---

### Post by ibjsb4 on 2013-05-02
> unable to create  `/usr/src/linux-headers-3.2.0-41/drivers/gpu/stub/Kconfig.dpkg-new'  (while processing  `./usr/src/linux-headers-3.2.0-41/drivers/gpu/stub/Kconfig'):[COLOR=#b22222] No space  left on device[/COLOR]
No apport report written because MaxReports is reached already

Looks like you need to clean out those old kernels.

[http://ubuntuforums.org/showthread.php?t=2141370&p=12630550#post12630550](http://ubuntuforums.org/showthread.php?t=2141370&p=12630550#post12630550)

---

### Post by balagan on 2013-05-02
thanks,

I've just tried to do that this way: [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

another error ocured. this is the terminal image:

ziom@ziom-D830:~$ uname -r
3.2.0-40-generic
ziom@ziom-D830:~$ dpkg -l | grep linux-image-
ii  linux-image-3.0.0-12-generic           3.0.0-12.20                             Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.2.0-32-generic           3.2.0-32.51                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic           3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic           3.2.0-34.53                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic           3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-generic           3.2.0-36.57                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic           3.2.0-37.58                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-generic           3.2.0-38.61                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic           3.2.0-39.62                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic           3.2.0-40.64                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.40.48                             Generic Linux kernel image
ziom@ziom-D830:~$ sudo apt-get autoremove linux-image-3.0.0-12-generic linux-image-3.2.0-32-generic  linux-image-3.2.0-33-generic linux-image-3.2.0-34-generic linux-image-3.2.0-35-generic linux-image-3.2.0-36-generic linux-image-3.2.0-37-generic linux-image-3.2.0-38-generic linux-image-3.2.0-39-generic
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Nale&#380;y uruchomi&#263; "apt-get -f install", aby naprawi&#263; poni&#380;sze problemy:
Nast&#281;puj&#261;ce pakiety maj&#261; niespe&#322;nione zale&#380;no&#347;ci:
 linux-headers-generic-pae : Wymaga: linux-headers-3.2.0-40-generic-pae ale nie zostanie zainstalowany
E: Niespe&#322;nione zale&#380;no&#347;ci. Prosz&#281; spróbowa&#263; wykona&#263; "apt-get -f install" bez pakietów (lub poda&#263; rozwi&#261;zanie).
ziom@ziom-D830:~$ apt-get -f install
E: Nie uda&#322;o si&#281; otworzy&#263; pliku blokady /var/lib/dpkg/lock - open (13: Brak dost&#281;pu)
E: Nie uda&#322;o si&#281; zablokowa&#263; katalogu administracyjnego (/var/lib/dpkg/), czy u&#380;yto uprawnie&#324; administratora?
ziom@ziom-D830:~$ 

sorry that it's in Polish,

it sais that it has some failed dependencies:  "linux-headers-generic-pae : needs: linux-headers-3.2.0-40-generic-pae but it will not be installed"
and after I typed in "apt-get -f install" it sais that it can't open the lock "/var/lib/dpkg/lock - open (13: access denyed)"

---

### Post by ibjsb4 on 2013-05-02
If you have a package manager open while trying to use apt-get, you will get that /var/lib/dpkg/lock message.  Only one package manager can be open at a time.  If thats not the case you can remove the lock.

```
sudo rm /var/lib/dpkg/lock
```

Then try your -f install.  You can also try

```
sudo apt-get clean && sudo apt-get dist-upgrade
```

---

### Post by aavirbhav on 2013-05-22
> **ibjsb4 said:**
> If you have a package manager open while trying to use apt-get, you will get that /var/lib/dpkg/lock message.  Only one package manager can be open at a time.  If thats not the case you can remove the lock.

```
sudo rm /var/lib/dpkg/lock
```

Then try your -f install.  You can also try

```
sudo apt-get clean && sudo apt-get dist-upgrade
```

Thanks...dear...it solve :D

---

