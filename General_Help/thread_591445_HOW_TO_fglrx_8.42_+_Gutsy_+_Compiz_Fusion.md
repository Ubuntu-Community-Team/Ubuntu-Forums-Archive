---
title: "HOW TO: fglrx 8.42 + Gutsy + Compiz Fusion"
date: 2007-10-25
forum: General Help
---

### Post by DestroyMicroshaft on 2007-10-25
Hello everyone, I have a little guide I cooked up, which is basically a modified version of Forlongs guide. I had some trouble getting this all to work, so I decided I would try to help others who may have had some of the problems I was encountering, like a white screen, low graphics, exct. This guide was intended for a fresh install of Gutsy on a 32 bit system, and will work, Ill post the pix to verify my properly working installation. I gotta say that Ive had great success using this driver, glxgears = 5000fps, compiz fusion = 300+fps, nice and smooth 3d & 2d, some video playback trouble, but I found temporarily disabling compiz fusion fixed that problem. So anyways, I hope this helps some of you out.




1. Remove the old driver (if present)

      Go to System &#8594; Administration &#8594; Restricted Drivers Manager and choose disable.

      Or remove it yourself:

      sudo apt-get remove xorg-driver-fglrx




2. Blacklist old fglrx module:

      sudo gedit /etc/default/linux-restricted-modules-common

      And insert fglrx - it should look like this then:

      DISABLED_MODULES="fglrx"





3.  Reboot now. 




4. Download the driver installer to your home folder

      [http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run)




5. Install necessary packages (to make Debian packages out of the driver, you will need you gutsy installation disc for this.)

      sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic




6. Create .deb packages

      bash ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy




7. Install .deb packages

      sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb xorg-driver-fglrx_8.42.3-1_i386.deb



8. Compile kernel module

      sudo m-a prepare,update

      sudo m-a build,install fglrx-kernel

      sudo depmod




9. Time for the initial configuration of fglrx.
   
      sudo aticonfig --initial --force  
 
      sudo aticonfig --overlay-type=Xv
     
      


10. Configure the driver (If needed, which it wont be on a fresh install)

      sudo gedit /etc/X11/xorg.conf


      Make sure "fglrx" is set for the Driver in the Section "Device".

      And if present, remove:

      Section "Extensions"

              Option        "Composite"        "0"     # or "Disable"

      EndSection

      As well as

      Section "ServerFlags"

              Option        "AIGLX"            "off"

      EndSection



11. Now you need to modify your Whitelist for Compiz Fusion

     sudo gedit /etc/xdg/compiz/compiz-manager


     Once that opens up add this under the last line: 

     WHITELIST="nvidia intel ati radeon i810 fglrx"



12. CONGRATZ!! You should be gold now, lol, as a recomended option though  I would go into Synaptic Package Manager and install:
            "compizconfig-settings-manager"
which will give you all the compiz fusion options we all thirst for!!!



[[IMG]http://img99.imageshack.us/img99/7626/screenshot1wt4.th.png[/IMG]](http://img99.imageshack.us/my.php?image=screenshot1wt4.png)
[[IMG]http://img147.imageshack.us/img147/9711/screenshot2wd6.th.png[/IMG]](http://img147.imageshack.us/my.php?image=screenshot2wd6.png)
[[IMG]http://img67.imageshack.us/img67/9395/screenshot3br6.th.png[/IMG]](http://img67.imageshack.us/my.php?image=screenshot3br6.png)
[[IMG]http://img67.imageshack.us/img67/9536/screenshot4lw8.th.png[/IMG]](http://img67.imageshack.us/my.php?image=screenshot4lw8.png)
[[IMG]http://img106.imageshack.us/img106/3773/screenshot5gn6.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshot5gn6.png)
[[IMG]http://img106.imageshack.us/img106/4027/screenshot6ws4.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshot6ws4.png)
[[IMG]http://img106.imageshack.us/img106/4724/screenshot7qh1.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshot7qh1.png)
[[IMG]http://img221.imageshack.us/img221/262/screenshot10ut2.th.png[/IMG]](http://img221.imageshack.us/my.php?image=screenshot10ut2.png)

---

### Post by tahnok on 2007-10-25
What kind of ATI card are you using?

---

### Post by Sabaki on 2007-10-25
Well, this didn't work for me. It errored out on Step 6:

bash ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy

with:

...
cp: cannot stat './usr/X11R6/lib/modules/dri'  no such file or directory
dh_install: command returned error code 256
make : *** [binary] error 1

So what am I missing here?

I don't even see a /usr/X11R6/lib/modules  directory!


Chuck
-------------
Ubuntu 64 'Gutsy' 
AMD Athlon 64 3500+
Motherboard ECS RS482-M
1G Ram
ATI RV410 [Radeon X700 Pro (PCIE)]

---

### Post by SupWiz17 on 2007-10-25
Last time I removed my old driver I get a black screen when I restart. Is there a way to get around that so I can install the new driver?

---

### Post by DestroyMicroshaft on 2007-10-26
Hello, 1st I am using a cheapo x1300, but getting great results.

2nd, make sure you have all the required packages to build which it sounds like you do, so what I would do, is cd my directory to wherever your driver is and try it again possibly like this:>  sudo ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy --force

And 3rd, if you reboot to a black screen try hitting: ctrl + alt + f1, that should bring you to a  command prompt requiring you to re-login, if it doesnt, do a manual reboot, and boot into recovery mode, run this command: > sudo dpkg-reconfigure xserver-xorg
Now select vesa from the upcoming list, after you agree for hardware auto detection, other then making sure vesa is selected use tab and enter to select ok without changing anything on the upcoming screens, when you are finished, reboot by hitting ctrl+alt+del, and boot normally, this should have disabled fglrx, and brought you back to using the free driver, You should be able to remove any remains of the old fglrx, with out getting a black screen.

---

### Post by fli_guy84 on 2007-10-26
That's a nice theme you got there. May I know where can I get it? :P

---

### Post by Nem1976 on 2007-10-26
I tried using this guide and couldn't get it to ever work.  My system would keep loading mesa drivers no matter what I tried.  So I reloaded Gutsy fresh and installed the drivers with the steps above and it's working now.  Compiz-fusion with no xgl is what I have been wanting for a while.

---

### Post by gmaniac on 2007-10-26
Anyone has this problem ?

FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'


Full log
```
ATI module generator V 2.0
==========================
initializing...
build_date =Fri Oct 26 19:37:40 EEST 2007
uname -a =Linux nuclear 2.6.22-14-rt #1 SMP PREEMPT RT Mon Oct 15 01:05:51 GMT 2007 i686 GNU/Linux
uname -s =Linux
uname -m =i686
uname -r =2.6.22-14-rt
uname -v =#1 SMP PREEMPT RT Mon Oct 15 01:05:51 GMT 2007
uid=0(root) gid=0(root) groups=0(root)
.
drwxr-xr-x 39 root root 12288 2007-10-26 18:30 /usr/include
.
total 71772
drwxr-sr-x  2 root src      4096 2007-10-24 19:02 ati
-rw-r--r--  1 root root    45209 2007-09-27 21:37 CONFIG
-rw-r--r--  1 root root    46911 2007-08-25 21:56 CONFIG.old
-rw-rw-r--  1 root root  1682212 2007-10-26 19:17 fglrx.tar.bz2
lrwxrwxrwx  1 root src        26 2007-10-26 19:26 linux -> linux-headers-2.6.22-14-rt
drwxr-xr-x 20 root root     4096 2007-10-15 22:51 linux-2.6.23
-rw-r--r--  1 geo  geo  45488158 2007-10-12 00:12 linux-2.6.23.tar.bz2
drwxr-xr-x 19 root root     4096 2007-10-26 19:15 linux-headers-2.6.22-14
drwxr-xr-x 10 root root     4096 2007-10-26 19:15 linux-headers-2.6.22-14-rt
-rw-r--r--  1 root src   8558116 2007-07-22 19:10 linux-headers-2.6.22.1-beta2_2.6.22.1-beta2-10.00.Custom_i386.deb
-rw-r--r--  1 root src   8638134 2007-08-14 14:33 linux-headers-2.6.22.2-beta2_2.6.22.2-beta2-10.00.Custom_i386.deb
-rw-r--r--  1 root src   4431692 2007-07-22 18:58 linux-image-2.6.22.1-beta2_2.6.22.1-beta2-10.00.Custom_i386.deb
-rw-r--r--  1 root src   4458624 2007-08-14 14:24 linux-image-2.6.22.2-beta2_2.6.22.2-beta2-10.00.Custom_i386.deb
lrwxrwxrwx  1 root src        26 2007-10-26 19:22 linux-OLDVERSION.1193415962 -> linux-headers-2.6.22-14-rt
drwxr-xr-x  3 root src      4096 2007-10-26 19:16 modules
.
file /lib/modules/2.6.22-14-rt/build/include/linux/agp_backend.h says: AGP=1
OsVersion says: SMP=1
file /proc/kallsyms says: SMP=1
file /lib/modules/2.6.22-14-rt/build/include/linux/autoconf.h says: SMP=1
file /lib/modules/2.6.22-14-rt/build/include/linux/autoconf.h says: MODVERSIONS=1
.
CC=gcc
cc_version=
found major but not minor version match for gcc and the ip-library
ls -l ./libfglrx_ip.a
lrwxrwxrwx 1 root root 18 2007-10-26 19:37 ./libfglrx_ip.a -> libfglrx_ip.a.GCC4
.
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
def_vma_api_version=-DFGL_LINUX253P1_VMA_API
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.22-14-rt/build SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-rt'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:365: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:366: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘fglrx_pci_suspend’:
/usr/src/modules/fglrx/firegl_public.c:799: warning: passing argument 1 of ‘firegl_pci_save_state’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘fglrx_pci_resume’:
/usr/src/modules/fglrx/firegl_public.c:841: warning: passing argument 1 of ‘firegl_pci_restore_state’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_pci_find_device’:
/usr/src/modules/fglrx/firegl_public.c:2019: warning: ‘pci_find_device’ is deprecated (declared at include/linux/pci.h:477)
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_request_irq’:
/usr/src/modules/fglrx/firegl_public.c:2962: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:68)
/usr/src/modules/fglrx/firegl_public.c:2962: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:5439: warning: ‘kmem_cache_t’ is deprecated
  LD [M]  /usr/src/modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'
make: *** [kmod_build] Error 2
build failed with return value 2
```

---

### Post by gmaniac on 2007-10-26
Replying to my own post 
I had to remove the rt kernel and install the generic one for some reason...:confused:

---

### Post by karhulitos on 2007-10-26
> **Nem1976 said:**
> I tried using this guide and couldn't get it to ever work.  My system would keep loading mesa drivers no matter what I tried.  So I reloaded Gutsy fresh and installed the drivers with the steps above and it's working now.  Compiz-fusion with no xgl is what I have been wanting for a while.

I have the same. All has gone ok but I always get only Mesa in glxinfo and fgl_glxgears core dumps:
```

~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30

```

This is an upgrade (Edgy/Feisty/Gutsy) and I wouldn't want to wipe all working things I have here.
Any hints what to look if Mesa stays stubbornly here?

xorg.conf in case the problem lies there:

Again I've done something wrong earlier. I did exactly [this]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually") and now I have fglrx. (and for the first time dektop effects)

---

### Post by DestroyMicroshaft on 2007-10-26
honestly I had no success using this guide, or any other for installing this driver on anything but a fresh install, but understand that you dont want to lose all the stuff youve got on your system, but, if you cant get this driver to work any other way, and your willing to throw in the towel and go fresh, use "apt on cd" to clone your repository as I did, easy enough to use software, and nice to a have a repository on disc you know. Sorry I cant be more help then that.


As for my themes,[http://gnome-look.org]("http://gnome-look.org"), got it all and then some!

---

### Post by christianxxx on 2007-10-27
Hooray! Got this working on my HP nc6000 laptop. I'm finally able to show off to my brother-in-law's friend. They've been waiting all week to see the wonderful eyecandies of Compiz.

But with a gxfcard with 64 mb memory, I think I'll disable this as soon as possible. But I hope to see some improvement in some 3d games, though. Especially Legends, which I've had some problems with.


Christian


Update: Couldn't make it work properly in Legends. All other OpenGL games work properly, but graphics in Legends are full of glitches. I'll try a separate post on this...

---

### Post by simeli on 2007-10-28
i just don't get the fglrx module loaded. any suggestions?

my graphics card:  ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)


i did everything as descirbed above, i did not get any error messages, aslo dmesg doesn't show anything. what else can i do?

---

### Post by phusho on 2007-10-29
Your card is not supported.

---

### Post by mzw! on 2007-10-30
> **gmaniac said:**
> Anyone has this problem ?

FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'


Full log
```
ATI module generator V 2.0
==========================
initializing...
build_date =Fri Oct 26 19:37:40 EEST 2007
uname -a =Linux nuclear 2.6.22-14-rt #1 SMP PREEMPT RT Mon Oct 15 01:05:51 GMT 2007 i686 GNU/Linux
uname -s =Linux
uname -m =i686
uname -r =2.6.22-14-rt
uname -v =#1 SMP PREEMPT RT Mon Oct 15 01:05:51 GMT 2007
uid=0(root) gid=0(root) groups=0(root)
.
drwxr-xr-x 39 root root 12288 2007-10-26 18:30 /usr/include
.
total 71772
drwxr-sr-x  2 root src      4096 2007-10-24 19:02 ati
-rw-r--r--  1 root root    45209 2007-09-27 21:37 CONFIG
-rw-r--r--  1 root root    46911 2007-08-25 21:56 CONFIG.old
-rw-rw-r--  1 root root  1682212 2007-10-26 19:17 fglrx.tar.bz2
lrwxrwxrwx  1 root src        26 2007-10-26 19:26 linux -> linux-headers-2.6.22-14-rt
drwxr-xr-x 20 root root     4096 2007-10-15 22:51 linux-2.6.23
-rw-r--r--  1 geo  geo  45488158 2007-10-12 00:12 linux-2.6.23.tar.bz2
drwxr-xr-x 19 root root     4096 2007-10-26 19:15 linux-headers-2.6.22-14
drwxr-xr-x 10 root root     4096 2007-10-26 19:15 linux-headers-2.6.22-14-rt
-rw-r--r--  1 root src   8558116 2007-07-22 19:10 linux-headers-2.6.22.1-beta2_2.6.22.1-beta2-10.00.Custom_i386.deb
-rw-r--r--  1 root src   8638134 2007-08-14 14:33 linux-headers-2.6.22.2-beta2_2.6.22.2-beta2-10.00.Custom_i386.deb
-rw-r--r--  1 root src   4431692 2007-07-22 18:58 linux-image-2.6.22.1-beta2_2.6.22.1-beta2-10.00.Custom_i386.deb
-rw-r--r--  1 root src   4458624 2007-08-14 14:24 linux-image-2.6.22.2-beta2_2.6.22.2-beta2-10.00.Custom_i386.deb
lrwxrwxrwx  1 root src        26 2007-10-26 19:22 linux-OLDVERSION.1193415962 -> linux-headers-2.6.22-14-rt
drwxr-xr-x  3 root src      4096 2007-10-26 19:16 modules
.
file /lib/modules/2.6.22-14-rt/build/include/linux/agp_backend.h says: AGP=1
OsVersion says: SMP=1
file /proc/kallsyms says: SMP=1
file /lib/modules/2.6.22-14-rt/build/include/linux/autoconf.h says: SMP=1
file /lib/modules/2.6.22-14-rt/build/include/linux/autoconf.h says: MODVERSIONS=1
.
CC=gcc
cc_version=
found major but not minor version match for gcc and the ip-library
ls -l ./libfglrx_ip.a
lrwxrwxrwx 1 root root 18 2007-10-26 19:37 ./libfglrx_ip.a -> libfglrx_ip.a.GCC4
.
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
def_vma_api_version=-DFGL_LINUX253P1_VMA_API
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.22-14-rt/build SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-rt'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:365: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:366: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘fglrx_pci_suspend’:
/usr/src/modules/fglrx/firegl_public.c:799: warning: passing argument 1 of ‘firegl_pci_save_state’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘fglrx_pci_resume’:
/usr/src/modules/fglrx/firegl_public.c:841: warning: passing argument 1 of ‘firegl_pci_restore_state’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_pci_find_device’:
/usr/src/modules/fglrx/firegl_public.c:2019: warning: ‘pci_find_device’ is deprecated (declared at include/linux/pci.h:477)
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_request_irq’:
/usr/src/modules/fglrx/firegl_public.c:2962: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:68)
/usr/src/modules/fglrx/firegl_public.c:2962: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:5439: warning: ‘kmem_cache_t’ is deprecated
  LD [M]  /usr/src/modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'
make: *** [kmod_build] Error 2
build failed with return value 2
```


I also have this exact issue, but only happens with the Real Time kernel from Ubuntu Studio. I googled it but didn't figure out how to solve it.
Does anybody know how to build FGLRX with the 2.6.22-14-rt???
Help us please!!

---

### Post by Digitallysick on 2007-10-30
when trying to install the ati driver, i get an error about no dri modules, finally i just had to use envy to install the ati driver, i can't seem to do it any other way, compiz never works for me, all my window borders disappear

---

### Post by LordMau on 2007-10-31
> **mzw! said:**
> I also have this exact issue, but only happens with the Real Time kernel from Ubuntu Studio. I googled it but didn't figure out how to solve it.
Does anybody know how to build FGLRX with the 2.6.22-14-rt???
Help us please!!

Here too. Good thing I hadnt removed the generic kernel yet. I'd really like to use 8.42 with the -rt kernel. Anyone please suggest a way?

---

### Post by LordMau on 2007-10-31
double post

---

### Post by frankpolo on 2007-10-31
I am new to Ubuntu, but not computers so I understand the basics. I installed Kubuntu as an extended partition as created a home partition, a swap partition and the root out of the extended partition. This will be my second time trying to get the desktop cube working with my ATI X1950 Pro. The first time I built the driver using the ati 8.43 instructions and fglrxinfo shows ATI as the driver and xorg shows fglrx under ATI. The open GL screensavers open up properly to. I can't remember the command but I ran the spinning gears in a cube test and it worked properly and quickly. I installed the compiz that is under add/remove programs but the desktop effects box is empty. I finally had to add compiz xserver-fgl. I could not get the cube to work and it disabled my hardware acceleration. Upon trying to get the cube to work last night my video got all jacked up and I ended up reinstalling Kubuntu during which I reformatted my extended partitions, so this is a new install. I built the ATI drivers and it came out as mesa. I followed another post in this forum and got my fglrx info to show my ATI card. I added the compiz from Add/Remove programs but it is still blank. I verified that open gl screen savers are working properly. Every article I look at says just installing compiz from add remove programs should get your cube running and enable all the effects. What do I need to do to get compiz installed properly and working with fglrx instead of xgl? Thanks for your time.

Frank

---

### Post by kevindubrow on 2007-11-02
Hey, I was following the guide and once I restarted I have to use a text prompt. ANy clue what I should do next? Thanks.

---

### Post by mzw! on 2007-11-03
Nobody found the way to install the fglrx 8.42 with the real time kernel yet? I would appreciate your help really much!

---

### Post by kevindubrow on 2007-11-03
What does one do when they get a text only interface after the restart? I ran all of the codes and edited that file, restarted and now I have no graphical interface. Thanks for the help.

---

### Post by userfriendly on 2007-11-04
> **mzw! said:**
> I also have this exact issue, but only happens with the Real Time kernel from Ubuntu Studio. I googled it but didn't figure out how to solve it.
Does anybody know how to build FGLRX with the 2.6.22-14-rt???
Help us please!!
> **LordMau said:**
> Here too. Good thing I hadnt removed the generic kernel yet. I'd really like to use 8.42 with the -rt kernel. Anyone please suggest a way?

may i add my voice? exact same problem here.

usually i'm fine with booting the generic kernel, but i'd really like to start playing with jack & ardour etc.

---

### Post by dibley on 2007-11-04
Hi Guys,

I've followed the guide through completely but still can't get the effects to work. I'm not sure if I'm missing an obvious step but I'm pretty new to Linux in general (trying to get away from Windows) so any help would be appreciated.

I followed the guide fully and didn't encounter any errors, but the effects don't display - the display on my smaller second monitor adjusts to follow the mouse cursor, which i believe is a feature provided by Compiz Fusion - but not the wobbly windows or anything else like that.

I've tried changing session to both XClient and Gnome, and typing "compiz" in a terminal - which turned my whole screen white with just a cursor. Music kept playing and the cursor changed as it passed over links in the webpage that was displaying previously but had to ctrl alt esc to get my desktop back.

Any ideas on what i should do next?

Edit: Oops, forgot to give you any details! Using an ATI X1300 graphics card, and a fresh install of gutsy. Not sure if you need any other info...

---

### Post by mzw! on 2007-11-11
I googled again but did not find how to get fglrx with the real time kernel included in ubuntu studio.
Is there anybody knowing how to do that? Please!

Thank you all for your patience

---

### Post by pyro_xp2k on 2007-11-11
The reason that fglrx won't compile with the realtime kernel is because it was compiled with paravirtualization support enabled, which causes problems because flgrx is not GPL.

Recompile the kernel without paravirtualization support and it should work.

---

### Post by pljones on 2007-11-11
Is there no way to pass an "I know that but just do it" flag to GCC / LD?

---

### Post by ktchn on 2007-11-11
> **pyro_xp2k said:**
> The reason that fglrx won't compile with the realtime kernel is because it was compiled with paravirtualization support enabled, which causes problems because flgrx is not GPL.

Recompile the kernel without paravirtualization support and it should work.

Have you managed to do this?  I tried, and failed on make-kpkg:

```
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-rt'
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-i386
make[2]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'
make: *** [debian/stamp-kernel-conf] Error 2

```

I haven't compiled the gutsy kernel before but I compiled feisty on the same machine (upgraded from feisty->gutsy a couple weeks ago).  Any help appreciated...

---

### Post by 4n1s on 2007-11-12
> **userfriendly said:**
> may i add my voice? exact same problem here.

usually i'm fine with booting the generic kernel, but i'd really like to start playing with jack & ardour etc.

I've tried to modify /usr/src/linux-headers-2.6.22-14-rt/Module.symvers at the lines:
```
0x8d522714      __rcu_read_lock vmlinux EXPORT_SYMBOL_GPL
```
```
0x2469810f      __rcu_read_unlock       vmlinux EXPORT_SYMBOL_GPL
```

deleting the "_GPL" string this way

```
0x8d522714      __rcu_read_lock vmlinux EXPORT_SYMBOL
```
```
0x2469810f      __rcu_read_unlock       vmlinux EXPORT_SYMBOL
```

In this way i succeed in compiling the module. However when i try to load it with

```
insmod fglrx.ko 
insmod: error inserting 'fglrx.ko': -1 Unknown symbol in module
```

dmesg give me back this:

```
[ 3534.310052] fglrx: Unknown symbol __rcu_read_unlock
[ 3534.310182] fglrx: Unknown symbol __rcu_read_lock

```

It seems to me that it doesn't succed in finding the kernel module it, maybe beacause of my hack.

So I tried a different way:
I tried to modify the source code of the module *firegl_public.c* in order to make it use the old *read_lock* system call (which is not GPL_ONLY) instead of rcu_read_lock. I deleted lines 1209 1210 1211 1213 1226 1227 1228 1230.
In this way the module compiles correctly even without chainging the Module.symvers file in kernel headers. however When I try to load it with insmod I face another problem:

```
fglrx: Unknown symbol tasklist_lock
```

This happens because the "tasklist_lock" system call doesn't exist anymore (I guess since 2.6.17).

In the end I am giving up by now, I will try to build a realtime kernel without paravitualization support and see. If anyone succeed in some way please report it.

---

### Post by pyro_xp2k on 2007-11-12
> **ktchn said:**
> Have you managed to do this?  I tried, and failed on make-kpkg:
...
I haven't compiled the gutsy kernel before but I compiled feisty on the same machine (upgraded from feisty->gutsy a couple weeks ago).  Any help appreciated...

Yep, it worked for me.
I first had that problem in Feisty after customizing a new kernel and never figured out why it wouldn't compile until later.

---

### Post by seanxemo on 2007-11-12
Hey, I followed the guide completely and even worked perfectly and I finally thought I was going to have compiz fusion working, but after I restarted all I ended up with was a white screen with a mouse.  Any help would be appreciated.

---

### Post by mzw! on 2007-11-13
Finally after almost 2 hors I re-compiled the kernel, removing the paravirtualization (or so I think), and it went well until I tried to install again the fglrx, which gave me this error:
> 
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol  
 &#9474; '__rcu_read_lock'                                                          
 &#9474; make[2]: *** [__modpost] Error 1                                   
 &#9474; make[1]: *** [modules] Error 2                                       
 &#9474; make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'       
 &#9474; make: *** [build] Error 2 

Any idea?

How exactly I remove that option?

---

### Post by cyclocross on 2007-11-13
I don't seem to have opengl at all now.  When I run  fglrxinfo  I get:

fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Anyone know where I went wrong?

Thanks

---

### Post by Mjölner on 2007-11-13
Hi

I am using an "Internal gfx Radeon X1200 Series" 

I'm following the guide but when I get to step 9:
> 9. Time for the initial configuration of fglrx.
sudo aticonfig --initial --force 

my terminal tells me:
> Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

I have looked around the forums and cant find the answer](*,)
I am new to Ubuntu and linux. Any help or suggestions will be appreciated.
Thanks in advance

---

### Post by pyro_xp2k on 2007-11-13
> **mzw! said:**
> Finally after almost 2 hors I re-compiled the kernel, removing the paravirtualization (or so I think), and it went well until I tried to install again the fglrx, which gave me this error:


Any idea?

How exactly I remove that option?

[[URL]http://ubuntuforums.org/showthread.php?t=311158]([URL]http://ubuntuforums.org/showthread.php?t=311158)[/url]
At step nine.

Look for it under *Processor Type and Features* and uncheck it.

Before preceding to step ten, note that if you're going to use kernel 2.6.23, you'll have to patch flgrx for it prior to compiling it -- see attachment for the patch.  To do so, install [FONT=Courier New]fglrx-kernel-source_8.42.3-1_i386.deb[/FONT] and [FONT=Courier New]xorg-driver-fglrx-dev_8.42.3-1_i386.deb[/FONT] if you haven't already and then cd /usr/src/modules/fglrx and do [FONT=Courier New]bzcat /the/path/to/patch842.tar.bz2 | patch -p0
[/FONT]

---

### Post by 4n1s on 2007-11-14
> **4n1s said:**
> 
In the end I am giving up by now, I will try to build a realtime kernel without paravitualization support and see. If anyone succeed in some way please report it.

I confirm that realtime-kernel recompilation (without paravirtualization) solves the ati-driver realtime kernel problem.

---

### Post by mzw! on 2007-11-14
how did you exactly do that? I tried re-compiling the kernel, after I modified the config files, but the same error occured when building the ati driver.

Could you point us some guide to compile the kernel without paravirtualization? I do not know what I am doing wrong.
Thank you!

---

### Post by pyro_xp2k on 2007-11-14
> **mzw! said:**
> how did you exactly do that? I tried re-compiling the kernel, after I modified the config files, but the same error occured when building the ati driver.

Could you point us some guide to compile the kernel without paravirtualization? I do not know what I am doing wrong.
Thank you!

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
Sorry - the link got broke in the last post.

---

### Post by mzw! on 2007-11-15
Thak you for the link, I had a look at it, but... I still don't really know because that is for newer kernel, I just wanted to compile the Real Time kernel from gutsy... but anyway, thank you!!

---

### Post by JohnG_ie on 2007-11-15
Yes that seems to be for a vanilla kernel. Where do I find the full source for the 2.6.22-14-rt linux kernel?

Thanks

---

### Post by JohnG_ie on 2007-11-15
To answer my own question, rt linux is just a patch applied to a vanilla kernel. RT patches can be found here:

[http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/)

---

### Post by ktchn on 2007-11-15
> **pyro_xp2k said:**
> Yep, it worked for me.
I first had that problem in Feisty after customizing a new kernel and never figured out why it wouldn't compile until later.

I got it to compile -- I somehow had the rt kernel installed but not the entire linux-rt meta-package.  Also, I had been following [tseliot's guide]("http://ubuntuforums.org/showthread.php?t=56835"), which didn't include the modules_image argument to the make-kpkg command.  After looking more closely at my list of installed packages and following the instructions in the [master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158"), I was able to recompile my existing kernel configuration after disabling paravirtualization as suggested.  Thanks for the initial tip, pyro_xp2k

Afterwards, I was able to install the latest fglrx drivers following "method 2" outlined in [these instructions.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

### Post by mzw! on 2007-11-16
I still trying to compile the kernel, can you please make a guide with the exact steps you made to achieve it?

Last time it gave me an error when compiling the kernel related to fglrx...

---

### Post by ankara on 2007-11-16
im very happy to see that other people are having the same trouble with the ubuntustudio RT kernel and are seemingly having success.
just for my benefit, when you enable the flgrx driver without a recompiled kernel, do you get a system hard lock upon starting X?
FYI i have radeon X300, am2 semptron 3000, 1gb corsair, gigabyte GA-M55-plus-SG3, and ubuntu studio gutsy.
ill be trying a recompile tonight.

---

### Post by mzw! on 2007-11-16
Oh man, I feel stupid, I compiled a kernel for 5th time and neither this one was able to build fglrx succcesfully.

I followed more or less the steps stated in the master kernel thread, but with the ubuntu kernel, and applying the RT patch from ubuntu git. Everything seemed to go ok, but still I have the same error with the RCU_lock or something like that...

I'd appreciate very much if any of you, who got the fglrx working on the RT kernel, could do a step by step guide, describing what you exactly do.

Thanks a lot.

---

### Post by ktchn on 2007-11-16
> **mzw! said:**
> Oh man, I feel stupid, I compiled a kernel for 5th time and neither this one was able to build fglrx succcesfully.

I followed more or less the steps stated in the master kernel thread, but with the ubuntu kernel, and applying the RT patch from ubuntu git. Everything seemed to go ok, but still I have the same error with the RCU_lock or something like that...

I'd appreciate very much if any of you, who got the fglrx working on the RT kernel, could do a step by step guide, describing what you exactly do.

Thanks a lot.

Are you already running the rt kernel from ubuntu studio?  If so, you don't need to apply the rt patch -- step 8 should take care of recreating your current configuration.  From there you will need to deselect paravirualization during make xconfig/make menuconfig.  I found it more easily using make xconfig.  

Your kernel should compile with or without paravirtualization, however -- its the proprietary ati driver which is incompatible with that option.

From your description it sounds like you might not have all the packages and source required to build the kernel, rt or otherwise.

---

### Post by ankara on 2007-11-16
> 
Entering directory `/usr/src/modules/fglrx'
dh_testdir
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
make[2]: Entering directory `/usr/src/linux-2.6.23'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:365: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:366: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_check_pci&#8217;:
/usr/src/modules/fglrx/firegl_public.c:1990: warning: &#8216;pci_find_slot&#8217; is deprecated (declared at include/linux/pci.h:481)
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_pci_find_device&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2019: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:480)
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_vm_test_and_clear_dirty&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2544: error: implicit declaration of function &#8216;ptep_test_and_clear_dirty&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_pci_find_slot&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2852: warning: &#8216;pci_find_slot&#8217; is deprecated (declared at include/linux/pci.h:481)
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_request_irq&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2962: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:64)
/usr/src/modules/fglrx/firegl_public.c:2962: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_pte_phys_addr_str&#8217;:
/usr/src/modules/fglrx/firegl_public.c:3536: error: implicit declaration of function &#8216;pte_read&#8217;
/usr/src/modules/fglrx/firegl_public.c:3538: error: implicit declaration of function &#8216;pte_exec&#8217;
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:5439: error: expected specifier-qualifier-list before &#8216;kmem_cache_t&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_SlabCache_Initialize&#8217;:
/usr/src/modules/fglrx/firegl_public.c:5478: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;routine_type&#8217;
/usr/src/modules/fglrx/firegl_public.c:5479: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
/usr/src/modules/fglrx/firegl_public.c:5480: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;name&#8217;
/usr/src/modules/fglrx/firegl_public.c:5484: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5485: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;name&#8217;
/usr/src/modules/fglrx/firegl_public.c:5485: error: too many arguments to function &#8216;kmem_cache_create&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_SlabCache_Destroy&#8217;:
/usr/src/modules/fglrx/firegl_public.c:5508: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5518: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5520: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_SlabCache_AllocEntry&#8217;:
/usr/src/modules/fglrx/firegl_public.c:5555: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;routine_type&#8217;
/usr/src/modules/fglrx/firegl_public.c:5556: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
/usr/src/modules/fglrx/firegl_public.c:5580: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5583: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
/usr/src/modules/fglrx/firegl_public.c:5591: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_SlabCache_FreeEntry&#8217;:
/usr/src/modules/fglrx/firegl_public.c:5619: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;routine_type&#8217;
/usr/src/modules/fglrx/firegl_public.c:5620: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
/usr/src/modules/fglrx/firegl_public.c:5632: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5635: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
make[3]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1
make[2]: *** [_module_/usr/src/modules/fglrx] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.23'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx'
Module /usr/src/modules/fglrx failed.
dont feel stupid dude. 

@ktchn
no, im sure all the required packages are installed, on my system at least.
i cant see why the flgrx module would be part of the compile, i added it to the /etc/default/linux-restricted-modules-common file. or is that file just with regards to Xserver?

one more thing, why would a whole kernel compile fail just because one module failed to compile properly, i'd have thought that the option to skip the module would be present for non essential ones.

---

### Post by mzw! on 2007-11-17
> **ktchn said:**
> Are you already running the rt kernel from ubuntu studio?  If so, you don't need to apply the rt patch -- step 8 should take care of recreating your current configuration.  From there you will need to deselect paravirualization during make xconfig/make menuconfig.  I found it more easily using make xconfig.  

Your kernel should compile with or without paravirtualization, however -- its the proprietary ati driver which is incompatible with that option.

From your description it sounds like you might not have all the packages and source required to build the kernel, rt or otherwise.

I compiled the generic kernel and I was able to install the deb packages. But for example, if you download the sources, ther is a folder with a patch for the RT kernel from ubuntu studio
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-gutsy.git;a=tree;h=09be68099d20251c478171ec69e8b307916b643b;hb=f865d06fb2754d444ef7ba25f08666b8a155ca32;f=debian/binary-custom.d/rt/patchset]("http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-gutsy.git;a=tree;h=09be68099d20251c478171ec69e8b307916b643b;hb=f865d06fb2754d444ef7ba25f08666b8a155ca32;f=debian/binary-custom.d/rt/patchset")

I don't know if you only import the config from the rt-kernel is enough or you have to apply that patch.

So, What I do is apply that patch to the sources from apt-get, and then import the config file from the installed rt kernel (the ubuntustudio one). And I follow the steps, make xconfig, deactivate paravirtualization... etc.

No errors after that, but when I try to build fglrx, still the same error.

---

### Post by pyro_xp2k on 2007-11-17
I went and applied the real time patch to the kernel and when I tried compiling it, got the GPL error so it looks like that particular patch is incompatible, too.

I'll keep playing around with it but it seems like at the moment you'll probably have to stick with the vanilla or the generic Ubuntu-patched kernel and recompile it with preemptiveness set to 'Low-Latency Desktop' and paravirtualization disabled.

---

### Post by mzw! on 2007-11-17
Thank you very much, I'll try the vanilla with the RT patch and see what happens.

---

### Post by kylecchh on 2007-11-17
Followed the guide, worked perfectly...
Until we get to install compiz...
I cannot enable any effects! I get "visual effects could not be enabled"
Any help?
Thanks,
Kyle

---

### Post by JohnG_ie on 2007-11-17
Ok I've got things working with the RT kernel, here is what I did:

1) Install kernel source from ubuntu repositories

2) Download and apply patch-2.6.22.1-rt9 from kernel.org

3) Follow the steps to recompile the kernel as listed in [the master kernel thread](http://ubuntuforums.org/showthread.php?t=311158).

4) Before going on the compile the kernel (step 10), open the file /usr/src/linux/kernel/rcupreempt.c in your favourite text editor.

Scroll right down to the bottom of the file

You should see the following 5 lines:

EXPORT_SYMBOL_GPL(call_rcu);
EXPORT_SYMBOL_GPL(rcu_batches_completed);
EXPORT_SYMBOL_GPL(__synchronize_sched);
EXPORT_SYMBOL_GPL(__rcu_read_lock);
EXPORT_SYMBOL_GPL(__rcu_read_unlock);

replace them with:

EXPORT_SYMBOL(call_rcu);
EXPORT_SYMBOL(rcu_batches_completed);
EXPORT_SYMBOL(__synchronize_sched);
EXPORT_SYMBOL(__rcu_read_lock);
EXPORT_SYMBOL(__rcu_read_unlock);

5) Compile & install the kernel. 

6) Reboot, install the fglrx driver as described in this thread.


Enjoy :)


p.s. Does this break the GPL license in any way?

---

### Post by pyro_xp2k on 2007-11-18
I ended up having to replace all instances of ' EXPORT_SYMBOL_GPL' with ' EXPORT_SYMBOL' throughout the entire file.
That worked perfectly -- you rock, dude. :guitar::)

---

### Post by mzw! on 2007-11-18
Thank you! It worked!
IT compiled the fglrx module as well with no problems. I applied the rt patch from ubuntustudio, but now I found another problem... I cannot start jack with real time if I am not root... hehe
Again, thankyou!

---

### Post by terminal on 2007-12-25
Agreed . I recompiled linux 2.6.23.12 from the link to above thread and followed JohnG_ie's steps and now i am on RT kernel with fglrx rocking :D . Has anyone found fix for the flickering in video problem ? Except using X11 output ?

Did anybody notice that fgl_gkxgears is showing very low framerate compared to older driver ? I think its syncing max fps to refresh supported by monitor . I am getting 70 fps on it and glxgears shows well above 250 fps . If i remember correctly older drive showed more than 1000 fps with fgl_glxgears .  glxinfo shows direct and fglrxinfo is showing rendering string as ATI .

---

### Post by FastZ on 2007-12-27
Ok so as to get this thread back on the topic of the OP and off the one about the RT kernel, I've completed the steps provided in the OP and everything went error free until I restarted, went to System>Preferences>Appearance>Visual Effects and tried to enable desktop effects.  Once I select the Normal, Extra, or Custom options, my screen immediately goes solid white and stays that way until I restart GDM.  Any suggestions on what might cause that?  I know i read somewhere above about someone else running into this problem but of course his post got lost in the RT kernel discussion.  Could someone offer some suggestions?  Thanks.

---

### Post by Cybolic on 2008-07-05
If you put the attached patch in /usr/src, you can follow the guide below, which will give you a rt kernel with the gpl stuff removed as the only change:

Prepare the system and get the packages:
```
cd /usr/src
sudo -s
sudo apt-get install linux-kernel-devel fakeroot build-essential
apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)

```

Copy the kernel source to a new dir and cd to it:
```

cp linux-$(uname -r | cut -d- -f 1-2) linux-$(uname -r | cut -d- -f 1-2)-rt -R
ln -s linux-$(uname -r | cut -d- -f 1-2)-rt linux && cd linux

```

Copy the no-gpl patch to where the debian tools will find and use it:
```

bzcat ../2000-rcupreemt-no-gpl.patch.bz2 > debian/binary-custom.d/rt/patchset/2000-rcupreemt-no-gpl.patch

```

Build the kernel packages:
```

AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-rt

```

Now you should have your new kernel packages in /usr/src, ready to install :D

If you need more info on this guide, I recommend reading this page:
[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

---

