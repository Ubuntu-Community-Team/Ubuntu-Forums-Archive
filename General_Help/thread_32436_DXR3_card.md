---
title: "DXR3 card"
date: 2005-05-07
forum: General Help
---

### Post by Laerte Andrade on 2005-05-07
I'm having trouble setting up my Creative DXR3 card for MPEG2 playback. I have downloaded the packages below and installed them. Then I tried following the instructions at the [http://dxr3.sourceforge.net/](http://dxr3.sourceforge.net/) site, but when I run *make* in /usr/src/modules/em8300, it simply doesn't work. Did anyone managed to install it successfully? Any other ideas at all? Thanks in advance.

I've altered the kernel source location in *Makefile* (as required by the instructions in the site) from:
**KERNEL_LOCATION?=/lib/modules/$(shell uname -r)/build**
to:
**KERNEL_LOCATION?=/usr**
since the package *em8300-headers* put a file called em8300.h in /usr/include/linux. I have no idea if I'm doing something terribly wrong here. Anyone can help me? Thanks in advance.


packages:
em8300
em8300-bin
em8300-headers
em8300-source

---

### Post by gsanse on 2005-09-07
I am also having the same problem. Did you have any progress?

---

### Post by gsanse on 2005-09-09
[QUOTE=Laerte Andrade]I'm having trouble setting up my Creative DXR3 card for MPEG2 playback. I have downloaded the packages below and installed them. Then I tried following the instructions at the [http://dxr3.sourceforge.net/](http://dxr3.sourceforge.net/) site, but when I run *make* in /usr/src/modules/em8300, it simply doesn't work. Did anyone managed to install it successfully? Any other ideas at all? Thanks in advance.

I've altered the kernel source location in *Makefile* (as required by the instructions in the site) from:
**KERNEL_LOCATION?=/lib/modules/$(shell uname -r)/build**
to:
**KERNEL_LOCATION?=/usr**
since the package *em8300-headers* put a file called em8300.h in /usr/include/linux. I have no idea if I'm doing something terribly wrong here. Anyone can help me? Thanks in advance.


packages:
em8300
em8300-bin
em8300-headers
em8300-source[/QUOTE]
 Laerte,

I investigated this a little bit more and found some interesting info. First of all, if you install the packages as you describe, you don't have to follow the instructions at [http://dxr3.sourceforge.net/](http://dxr3.sourceforge.net/). You would do that if you want to install the driver from source. Installing from packages should do all the configuration and nothing else would be needed. The problem is that Hoary repositories now have em8300 (0.14.0-2) and this version is know not to work with 2.6 kernels. There is a bug filed in bugzilla about this problem, check it at [http://lists.ubuntu.com/archives/kernel-bugs/2005-May/001363.html](http://lists.ubuntu.com/archives/kernel-bugs/2005-May/001363.html). However the new version of em8300 (0.15.1) does support 2.6 kernels. My conclusion, and I will try that later when I get to my Linux box, is that you should remove the em8300 packages using synaptic and install the driver from source using the 0.15.1 version. I will report the outcome of this later.

Regards,

gsanse

---

### Post by gsanse on 2005-09-10
I got it working and here is what I did.

1- Download the em8300 0.15.0 package from here: [http://ftp.us.debian.org/debian/pool/contrib/e/em8300/em8300_0.15.0.dfsg-2_i386.deb](http://ftp.us.debian.org/debian/pool/contrib/e/em8300/em8300_0.15.0.dfsg-2_i386.deb). Install it doing $sudo dpgk -i em8300_0.15.0.dfsg-2_i386.deb. Follow the instructions.

2- Download the source code for the em8300 driver frome here: [http://dxr3.sourceforge.net/download.html](http://dxr3.sourceforge.net/download.html). You will need the source for the package because the package does not compile the modules automatically, you have to do it by hand. Extratct the source, enter the modules directory and execute $make and then $sudo make install. This will install the modules.

3- Everything should be installed now. However, there is a small problem with the installation. The owner of the /dev/em8300* files created is root:root. If you try to use mplayer to play a file using the dxr3 output you will get an error saying that mplayer cannot access the em8300 device. To fix this you need to edit the permissions for udev. Go to /etc/udev/permissions.d and execute

$sudo cp udev.permissions udev.permissions.original

doing this you will have a backup of your original udev.permissions file in case anything goes wrong. After that, execeute $sudo gedit udev.permissions to alter the file. You need to add few lines to change the ownership of the em8300* files. I am not sure, but I think you can add this anywhere in the # character devices section of this file. To keep thing nice I added the line closer to some other video devices. My file looks like this (altered section in bold):

# name:user:group:mode

# character devices

ptmx:root:tty:0666
random:root:root:0666
urandom:root:root:0444
kmem:root:kmem:0640
mem:root:kmem:0640
port:root:kmem:0640
null:root:root:0666
zero:root:root:0666
full:root:root:0666

misc/nvram:root:nvram:660
nvram:root:nvram:660
misc/rtc:root:audio:0664
rtc:root:audio:0664
inotify:root:root:0666

tts/*:root:dialout:0660
bluetooth/rfcomm/*:root:dialout:0660
tty[BCDEFHILMPRSTUVWX][0-9]*:root:dialout:0660
ttyS[ACIR][0-9]*:root:dialout:0660
ttyUSB[0-9]*:root:dialout:0660
ttyACM[0-9]*:root:dialout:0660
ippp[0-9]*:root:dialout:0660
isdn[0-9]*:root:dialout:0660
isdnctrl[0-9]*:root:dialout:0660
capi[0-9.]*:root:dialout:0660
dcbri[0-9]*:root:dialout:0660
ircomm[0-9]*:root:dialout:0660
rfcomm[0-9]*:root:dialout:0660
tty:root:tty:0666

snd/*:root:audio:0660
sound/*:root:audio:0660
admmidi*:root:audio:0660
adsp*:root:audio:0660
aload*:root:audio:0660
amidi*:root:audio:0660
amixer*:root:audio:0660
audio*:root:audio:0660
dmfm*:root:audio:0660
dsp*:root:audio:0660
audio*:root:audio:0660
mixer*:root:audio:0660
music:root:audio:0660
sequencer*:root:audio:0660

printers/*:root:lp:0660
usb/lp[0-9]*:root:lp:0660
usb/legousbtower[0-9]*:root:root:666
lp[0-9]*:root:lp:0660
parport[0-9]*:root:lp:0660
irlpt[0-9]*:root:lp:0660
usblp[0-9]*:root:lp:0660

input/mice:root:root:0600
input/mouse[0-9]*:root:root:0600
input/js[0-9]*:root:root:0644
input/*:root:root:0600
mouse[0-9]*:root:root:0600
js[0-9]*:root:root:0644
sonypi:root:root:0666

dri/card[0-9]*:root:video:0660
fb/*:root:video:0660
fb[0-9]*:root:video:0660
agpgart:root:video:0660
nvidia*:root:video:0660

v4l/*:root:video:0660
video[0-9]*:root:video:0660
radio[0-9]*:root:video:0660
vbi[0-9]*:root:video:0660
vtx[0-9]*:root:video:0660
dvb/*:root:video:0660
**em8300*:root:video:0660**

raw1394:root:video:0600
# When the kernel gets proper support for 1394, change this to a wildcard:
video1394/0:root:video:0660

# block devices

floppy/*:root:floppy:0660
fd[0-9]*:root:floppy:0660
cdemu/*:root:cdrom:0660
pktcdvd/*:root:cdrom:0660
pktcdvd/control:root:root:0644

ram[0-9]*:root:disk:0660
raw/*:root:disk:0660

ide/*/cd:root:cdrom:0660
ide/*:root:disk:0660
hd[a-s]:root:disk:0660
hd[a-s][0-9]*:root:disk:0660

scsi/*/cd:root:cdrom:0660
scsi/*:root:disk:0660
sd[a-z]:root:disk:0660
sd[a-z][0-9]*:root:disk:0660
sd[a-i][a-z]:root:disk:0660
sd[a-i][a-z][0-9]*:root:disk:0660
s[gr][0-9]*:root:disk:0660
scd[0-9]*:root:cdrom:0660

dasd[0-9]*:root:disk:0660
ataraid[0-9]*:root:disk:0660

loop/*:root:disk:0660
loop[0-9]*:root:disk:0660
md/*:root:disk:0660
md[0-9]*:root:disk:0660
dm-*:root:disk:0640

ht[0-9]*:root:tape:0660
nht[0-9]*:root:tape:0660
pt[0-9]*:root:tape:0660
npt[0-9]*:root:tape:0660
st[0-9]*:root:tape:0660
nst[0-9]*:root:tape:0660

sgi_fetchop:root:root:666
iseries/vcd*:root:disk:660
iseries/vd*:root:disk:660

4- That's it, everything should be working.

Regards,

gsanse

---

### Post by deadland on 2007-11-30
I am using gutsy right now and I want to run a VDR on this machine. I can compile the modules, but I can't use she modules. I didn't install the packets of ubuntu.

That how it looks like, when I am compiling the modules:

```
root@vdr:/usr/src/em8300-0.16.3/modules# make 
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/em8300-0.16.3/modules modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/em8300-0.16.3/modules/adv717x.o
  CC [M]  /usr/src/em8300-0.16.3/modules/bt865.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_main.o
/usr/src/em8300-0.16.3/modules/em8300_main.c: In Funktion »em8300_probe«:
/usr/src/em8300-0.16.3/modules/em8300_main.c:689: Warnung: »deprecated_irq_flag« ist veraltet (deklariert bei include/linux/interrupt.h:66)
/usr/src/em8300-0.16.3/modules/em8300_main.c:689: Warnung: »deprecated_irq_flag« ist veraltet (deklariert bei include/linux/interrupt.h:66)
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_i2c.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_audio.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_fifo.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_video.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_misc.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_dicom.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_ucode.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_ioctl.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_spu.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em9010.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_registration.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_procfs.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_devfs.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_udev.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_sysfs.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_alsa.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_params.o
  CC [M]  /usr/src/em8300-0.16.3/modules/em8300_eeprom.o
  LD [M]  /usr/src/em8300-0.16.3/modules/em8300.o
  Building modules, stage 2.
  MODPOST 3 modules
  CC      /usr/src/em8300-0.16.3/modules/adv717x.mod.o
  LD [M]  /usr/src/em8300-0.16.3/modules/adv717x.ko
  CC      /usr/src/em8300-0.16.3/modules/bt865.mod.o
  LD [M]  /usr/src/em8300-0.16.3/modules/bt865.ko
  CC      /usr/src/em8300-0.16.3/modules/em8300.mod.o
  LD [M]  /usr/src/em8300-0.16.3/modules/em8300.ko
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
root@vdr:/usr/src/em8300-0.16.3/modules# make install
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/em8300-0.16.3/modules INSTALL_MOD_PATH= modules_install
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /usr/src/em8300-0.16.3/modules/adv717x.ko
  INSTALL /usr/src/em8300-0.16.3/modules/bt865.ko
  INSTALL /usr/src/em8300-0.16.3/modules/em8300.ko
  DEPMOD  2.6.22-14-generic
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'

```

Looks fine!!!


when I run modprobe em8300:

```
root@vdr:/usr/src/em8300-0.16.3/modules# modprobe em8300
FATAL: Error inserting em8300 (/lib/modules/2.6.22-14-generic/em8300/em8300.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

and thats what dmesg says:

```
dmesg | grep em8300
[   39.451189] em8300: disagrees about version of symbol snd_pcm_new
[   39.451207] em8300: Unknown symbol snd_pcm_new
[   39.451747] em8300: disagrees about version of symbol snd_card_register
[   39.451754] em8300: Unknown symbol snd_card_register
[   39.451928] em8300: disagrees about version of symbol snd_card_free
[   39.451934] em8300: Unknown symbol snd_card_free
[   39.452110] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   39.452118] em8300: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   39.453764] em8300: disagrees about version of symbol snd_card_new
[   39.453773] em8300: Unknown symbol snd_card_new
[   39.453950] em8300: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   39.453957] em8300: Unknown symbol snd_pcm_lib_malloc_pages
[   39.454130] em8300: disagrees about version of symbol snd_pcm_lib_ioctl
[   39.454137] em8300: Unknown symbol snd_pcm_lib_ioctl
[   39.454309] em8300: disagrees about version of symbol snd_pcm_lib_free_pages
[   39.454316] em8300: Unknown symbol snd_pcm_lib_free_pages
[   39.454812] em8300: disagrees about version of symbol snd_pcm_set_ops
[   39.454818] em8300: Unknown symbol snd_pcm_set_ops
[   39.455058] em8300: disagrees about version of symbol snd_device_new
[   39.455064] em8300: Unknown symbol snd_device_new
[   39.455880] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_free_for_all
[   39.455887] em8300: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[   39.456388] em8300: disagrees about version of symbol snd_pcm_period_elapsed
[   39.456394] em8300: Unknown symbol snd_pcm_period_elapsed
[   59.602112] em8300: disagrees about version of symbol snd_pcm_new
[   59.602140] em8300: Unknown symbol snd_pcm_new
[   59.602698] em8300: disagrees about version of symbol snd_card_register
[   59.602704] em8300: Unknown symbol snd_card_register
[   59.602884] em8300: disagrees about version of symbol snd_card_free
[   59.602890] em8300: Unknown symbol snd_card_free
[   59.603071] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   59.603078] em8300: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   59.604605] em8300: disagrees about version of symbol snd_card_new
[   59.604612] em8300: Unknown symbol snd_card_new
[   59.604794] em8300: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   59.604801] em8300: Unknown symbol snd_pcm_lib_malloc_pages
[   59.604979] em8300: disagrees about version of symbol snd_pcm_lib_ioctl
[   59.604986] em8300: Unknown symbol snd_pcm_lib_ioctl
[   59.605185] em8300: disagrees about version of symbol snd_pcm_lib_free_pages
[   59.605193] em8300: Unknown symbol snd_pcm_lib_free_pages
[   59.605695] em8300: disagrees about version of symbol snd_pcm_set_ops
[   59.605701] em8300: Unknown symbol snd_pcm_set_ops
[   59.605946] em8300: disagrees about version of symbol snd_device_new
[   59.605952] em8300: Unknown symbol snd_device_new
[   59.606782] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_free_for_all
[   59.606789] em8300: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[   59.607294] em8300: disagrees about version of symbol snd_pcm_period_elapsed
[   59.607301] em8300: Unknown symbol snd_pcm_period_elapsed
[  241.883225] em8300: disagrees about version of symbol snd_pcm_new
[  241.883255] em8300: Unknown symbol snd_pcm_new
[  241.883821] em8300: disagrees about version of symbol snd_card_register
[  241.883827] em8300: Unknown symbol snd_card_register
[  241.884007] em8300: disagrees about version of symbol snd_card_free
[  241.884013] em8300: Unknown symbol snd_card_free
[  241.884194] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  241.884202] em8300: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  241.885730] em8300: disagrees about version of symbol snd_card_new
[  241.885737] em8300: Unknown symbol snd_card_new
[  241.885919] em8300: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  241.885926] em8300: Unknown symbol snd_pcm_lib_malloc_pages
[  241.886139] em8300: disagrees about version of symbol snd_pcm_lib_ioctl
[  241.886147] em8300: Unknown symbol snd_pcm_lib_ioctl
[  241.886326] em8300: disagrees about version of symbol snd_pcm_lib_free_pages
[  241.886333] em8300: Unknown symbol snd_pcm_lib_free_pages
[  241.886834] em8300: disagrees about version of symbol snd_pcm_set_ops
[  241.886840] em8300: Unknown symbol snd_pcm_set_ops
[  241.887116] em8300: disagrees about version of symbol snd_device_new
[  241.887122] em8300: Unknown symbol snd_device_new
[  241.887954] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_free_for_all
[  241.887961] em8300: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[  241.888466] em8300: disagrees about version of symbol snd_pcm_period_elapsed
[  241.888473] em8300: Unknown symbol snd_pcm_period_elapsed
[  536.767460] em8300: disagrees about version of symbol snd_pcm_new
[  536.767487] em8300: Unknown symbol snd_pcm_new
[  536.768457] em8300: disagrees about version of symbol snd_card_register
[  536.768467] em8300: Unknown symbol snd_card_register
[  536.768647] em8300: disagrees about version of symbol snd_card_free
[  536.768653] em8300: Unknown symbol snd_card_free
[  536.768834] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  536.768842] em8300: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  536.771599] em8300: disagrees about version of symbol snd_card_new
[  536.771609] em8300: Unknown symbol snd_card_new
[  536.771791] em8300: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  536.771798] em8300: Unknown symbol snd_pcm_lib_malloc_pages
[  536.771977] em8300: disagrees about version of symbol snd_pcm_lib_ioctl
[  536.771984] em8300: Unknown symbol snd_pcm_lib_ioctl
[  536.772161] em8300: disagrees about version of symbol snd_pcm_lib_free_pages
[  536.772167] em8300: Unknown symbol snd_pcm_lib_free_pages
[  536.772668] em8300: disagrees about version of symbol snd_pcm_set_ops
[  536.772675] em8300: Unknown symbol snd_pcm_set_ops
[  536.772919] em8300: disagrees about version of symbol snd_device_new
[  536.772925] em8300: Unknown symbol snd_device_new
[  536.773777] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_free_for_all
[  536.773786] em8300: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[  536.774292] em8300: disagrees about version of symbol snd_pcm_period_elapsed
[  536.774299] em8300: Unknown symbol snd_pcm_period_elapsed
[  749.828590] em8300: disagrees about version of symbol snd_pcm_new
[  749.828619] em8300: Unknown symbol snd_pcm_new
[  749.829635] em8300: disagrees about version of symbol snd_card_register
[  749.829645] em8300: Unknown symbol snd_card_register
[  749.829825] em8300: disagrees about version of symbol snd_card_free
[  749.829832] em8300: Unknown symbol snd_card_free
[  749.830013] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  749.830021] em8300: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  749.832791] em8300: disagrees about version of symbol snd_card_new
[  749.832802] em8300: Unknown symbol snd_card_new
[  749.832984] em8300: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  749.832991] em8300: Unknown symbol snd_pcm_lib_malloc_pages
[  749.833170] em8300: disagrees about version of symbol snd_pcm_lib_ioctl
[  749.833177] em8300: Unknown symbol snd_pcm_lib_ioctl
[  749.833354] em8300: disagrees about version of symbol snd_pcm_lib_free_pages
[  749.833360] em8300: Unknown symbol snd_pcm_lib_free_pages
[  749.833862] em8300: disagrees about version of symbol snd_pcm_set_ops
[  749.833869] em8300: Unknown symbol snd_pcm_set_ops
[  749.834113] em8300: disagrees about version of symbol snd_device_new
[  749.834119] em8300: Unknown symbol snd_device_new
[  749.834969] em8300: disagrees about version of symbol snd_pcm_lib_preallocate_free_for_all
[  749.834977] em8300: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[  749.835483] em8300: disagrees about version of symbol snd_pcm_period_elapsed
[  749.835490] em8300: Unknown symbol snd_pcm_period_elapsed

```

---

