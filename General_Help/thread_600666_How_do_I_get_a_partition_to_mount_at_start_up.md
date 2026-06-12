---
title: "How do I get a partition to mount at start up?"
date: 2007-11-02
forum: General Help
---

### Post by MR.UNOWEN on 2007-11-02
Can some one please give me a step by step direction on how to have a fat32 partition load at start up? I know there's already a thread about this, but no one seems to notice that one and the explanations on that one are unclear.

---

### Post by lolindrath on 2007-11-02
Hi There,

Checkout this article: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

It looks to be pretty self-explanatory.

--Lolindrath

---

### Post by MR.UNOWEN on 2007-11-02
it's not working 

"sudo: umount/dev/hdb1: command not found"

How do I go about having it mount in /media?

---

### Post by anaconda on 2007-11-02
öh..
what are you trying to do?

and there is supposed to be a space between umount and /dev/hdb1

THe link lolindrath gave you is a good one.

Basically all you have to do is to create the folder /fat_file and add the following line to your /etc/fstab file:
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0 

and reboot.

The umount command isn't even necessary, because when you reboot all disks will be unmounted. and when the machine starts again every disk which is mentioned in fstab will be mounted.

---

### Post by Steve1961 on 2007-11-02
and once you have the line in fstab you don't even need to reboot to mount the drive.  Just type sudo mount -a

---

### Post by MR.UNOWEN on 2007-11-02
Still not doing it. Also there is no hdb1 directory.

Here's what I do have
> 
dev$ dir
4-1        ptyc2  ptyr1  ptyw0  ram9        tty60  ttye8  ttyt3  ttyy2
4-1.2      ptyc3  ptyr2  ptyw1  random      tty61  ttye9  ttyt4  ttyy3
adsp       ptyc4  ptyr3  ptyw2  rtc         tty62  ttyea  ttyt5  ttyy4
agpgart    ptyc5  ptyr4  ptyw3  scd0        tty63  ttyeb  ttyt6  ttyy5
audio      ptyc6  ptyr5  ptyw4  sda         tty7   ttyec  ttyt7  ttyy6
bus        ptyc7  ptyr6  ptyw5  sda1        tty8   ttyed  ttyt8  ttyy7
cdrom      ptyc8  ptyr7  ptyw6  sda2        tty9   ttyee  ttyt9  ttyy8
cdrw       ptyc9  ptyr8  ptyw7  sda3        ttya0  ttyef  ttyta  ttyy9
console    ptyca  ptyr9  ptyw8  sda4        ttya1  ttyp0  ttytb  ttyya
core       ptycb  ptyra  ptyw9  sequencer   ttya2  ttyp1  ttytc  ttyyb
disk       ptycc  ptyrb  ptywa  sequencer2  ttya3  ttyp2  ttytd  ttyyc
dmfm       ptycd  ptyrc  ptywb  sg0         ttya4  ttyp3  ttyte  ttyyd
dmmidi     ptyce  ptyrd  ptywc  sg1         ttya5  ttyp4  ttytf  ttyye
dri        ptycf  ptyre  ptywd  shm         ttya6  ttyp5  ttyu0  ttyyf
dsp        ptyd0  ptyrf  ptywe  snapshot    ttya7  ttyp6  ttyu1  ttyz0
dvd        ptyd1  ptys0  ptywf  snd         ttya8  ttyp7  ttyu2  ttyz1
dvdrw      ptyd2  ptys1  ptyx0  sndstat     ttya9  ttyp8  ttyu3  ttyz2
fd         ptyd3  ptys2  ptyx1  sr0         ttyaa  ttyp9  ttyu4  ttyz3
fd0        ptyd4  ptys3  ptyx2  stderr      ttyab  ttypa  ttyu5  ttyz4
full       ptyd5  ptys4  ptyx3  stdin       ttyac  ttypb  ttyu6  ttyz5
fuse       ptyd6  ptys5  ptyx4  stdout      ttyad  ttypc  ttyu7  ttyz6
hpet       ptyd7  ptys6  ptyx5  tty         ttyae  ttypd  ttyu8  ttyz7
hwrng      ptyd8  ptys7  ptyx6  tty0        ttyaf  ttype  ttyu9  ttyz8
initctl    ptyd9  ptys8  ptyx7  tty1        ttyb0  ttypf  ttyua  ttyz9
input      ptyda  ptys9  ptyx8  tty10       ttyb1  ttyq0  ttyub  ttyza
kmem       ptydb  ptysa  ptyx9  tty11       ttyb2  ttyq1  ttyuc  ttyzb
kmsg       ptydc  ptysb  ptyxa  tty12       ttyb3  ttyq2  ttyud  ttyzc
log        ptydd  ptysc  ptyxb  tty13       ttyb4  ttyq3  ttyue  ttyzd
loop0      ptyde  ptysd  ptyxc  tty14       ttyb5  ttyq4  ttyuf  ttyze
lp0        ptydf  ptyse  ptyxd  tty15       ttyb6  ttyq5  ttyv0  ttyzf
MAKEDEV    ptye0  ptysf  ptyxe  tty16       ttyb7  ttyq6  ttyv1  urandom
mem        ptye1  ptyt0  ptyxf  tty17       ttyb8  ttyq7  ttyv2  usb1
midi       ptye2  ptyt1  ptyy0  tty18       ttyb9  ttyq8  ttyv3  usb2
mixer      ptye3  ptyt2  ptyy1  tty19       ttyba  ttyq9  ttyv4  usb3
net        ptye4  ptyt3  ptyy2  tty2        ttybb  ttyqa  ttyv5  usb4
null       ptye5  ptyt4  ptyy3  tty20       ttybc  ttyqb  ttyv6  usbdev1.1_ep00
nvidia0    ptye6  ptyt5  ptyy4  tty21       ttybd  ttyqc  ttyv7  usbdev1.1_ep81
nvidiactl  ptye7  ptyt6  ptyy5  tty22       ttybe  ttyqd  ttyv8  usbdev2.1_ep00
oldmem     ptye8  ptyt7  ptyy6  tty23       ttybf  ttyqe  ttyv9  usbdev2.1_ep81
parport0   ptye9  ptyt8  ptyy7  tty24       ttyc0  ttyqf  ttyva  usbdev3.1_ep00
port       ptyea  ptyt9  ptyy8  tty25       ttyc1  ttyr0  ttyvb  usbdev3.1_ep81
ppp        ptyeb  ptyta  ptyy9  tty26       ttyc2  ttyr1  ttyvc  usbdev4.1_ep00
psaux      ptyec  ptytb  ptyya  tty27       ttyc3  ttyr2  ttyvd  usbdev4.1_ep81
ptmx       ptyed  ptytc  ptyyb  tty28       ttyc4  ttyr3  ttyve  usbdev4.2_ep00
pts        ptyee  ptytd  ptyyc  tty29       ttyc5  ttyr4  ttyvf  usbdev4.2_ep81
ptya0      ptyef  ptyte  ptyyd  tty3        ttyc6  ttyr5  ttyw0  usbdev4.3_ep00
ptya1      ptyp0  ptytf  ptyye  tty30       ttyc7  ttyr6  ttyw1  usbdev4.3_ep02
ptya2      ptyp1  ptyu0  ptyyf  tty31       ttyc8  ttyr7  ttyw2  usbdev4.3_ep03
ptya3      ptyp2  ptyu1  ptyz0  tty32       ttyc9  ttyr8  ttyw3  usbdev4.3_ep81
ptya4      ptyp3  ptyu2  ptyz1  tty33       ttyca  ttyr9  ttyw4  usbdev4.3_ep82
ptya5      ptyp4  ptyu3  ptyz2  tty34       ttycb  ttyra  ttyw5  usbdev4.3_ep83
ptya6      ptyp5  ptyu4  ptyz3  tty35       ttycc  ttyrb  ttyw6  vcs
ptya7      ptyp6  ptyu5  ptyz4  tty36       ttycd  ttyrc  ttyw7  vcs1
ptya8      ptyp7  ptyu6  ptyz5  tty37       ttyce  ttyrd  ttyw8  vcs2
ptya9      ptyp8  ptyu7  ptyz6  tty38       ttycf  ttyre  ttyw9  vcs3
ptyaa      ptyp9  ptyu8  ptyz7  tty39       ttyd0  ttyrf  ttywa  vcs4
ptyab      ptypa  ptyu9  ptyz8  tty4        ttyd1  ttys0  ttywb  vcs5
ptyac      ptypb  ptyua  ptyz9  tty40       ttyd2  ttyS0  ttywc  vcs6
ptyad      ptypc  ptyub  ptyza  tty41       ttyd3  ttys1  ttywd  vcs7
ptyae      ptypd  ptyuc  ptyzb  tty42       ttyd4  ttyS1  ttywe  vcs8
ptyaf      ptype  ptyud  ptyzc  tty43       ttyd5  ttys2  ttywf  vcsa
ptyb0      ptypf  ptyue  ptyzd  tty44       ttyd6  ttyS2  ttyx0  vcsa1
ptyb1      ptyq0  ptyuf  ptyze  tty45       ttyd7  ttys3  ttyx1  vcsa2
ptyb2      ptyq1  ptyv0  ptyzf  tty46       ttyd8  ttyS3  ttyx2  vcsa3
ptyb3      ptyq2  ptyv1  ram0   tty47       ttyd9  ttys4  ttyx3  vcsa4
ptyb4      ptyq3  ptyv2  ram1   tty48       ttyda  ttys5  ttyx4  vcsa5
ptyb5      ptyq4  ptyv3  ram10  tty49       ttydb  ttys6  ttyx5  vcsa6
ptyb6      ptyq5  ptyv4  ram11  tty5        ttydc  ttys7  ttyx6  vcsa7
ptyb7      ptyq6  ptyv5  ram12  tty50       ttydd  ttys8  ttyx7  vcsa8
ptyb8      ptyq7  ptyv6  ram13  tty51       ttyde  ttys9  ttyx8  watchdog
ptyb9      ptyq8  ptyv7  ram14  tty52       ttydf  ttysa  ttyx9  xconsole
ptyba      ptyq9  ptyv8  ram15  tty53       ttye0  ttysb  ttyxa  zero
ptybb      ptyqa  ptyv9  ram2   tty54       ttye1  ttysc  ttyxb
ptybc      ptyqb  ptyva  ram3   tty55       ttye2  ttysd  ttyxc
ptybd      ptyqc  ptyvb  ram4   tty56       ttye3  ttyse  ttyxd
ptybe      ptyqd  ptyvc  ram5   tty57       ttye4  ttysf  ttyxe
ptybf      ptyqe  ptyvd  ram6   tty58       ttye5  ttyt0  ttyxf
ptyc0      ptyqf  ptyve  ram7   tty59       ttye6  ttyt1  ttyy0
ptyc1      ptyr0  ptyvf  ram8   tty6        ttye7  ttyt2  ttyy1


---

### Post by dcstar on 2007-11-02
> **MR.UNOWEN said:**
> Can some one please give me a step by step direction on how to have a fat32 partition load at start up? I know there's already a thread about this, but no one seems to notice that one and the explanations on that one are unclear.

[http://ubuntuforums.org/showpost.php?p=3694162&postcount=2](http://ubuntuforums.org/showpost.php?p=3694162&postcount=2)

---

### Post by MR.UNOWEN on 2007-11-02
Thanks

---

### Post by John Read on 2007-11-03
There's a pretty good 

[URL="http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop"]


Essentially if you want everyone to be able to write to the vfat drive, you add something like the
following to your fstab file ...

/dev/hda1  /media/windows  vfat  iocharset=utf8,umask=000   0   0

where hda1 is replaced with your partition
windows can be any directory name you like, e.g. win_data

Of course you need to create that directory, e.g.
  sudo mkdir /media/windows



Here are the steps.

First create a backup of the fstab file..
sudo cp /etc/fstab /etc/fstab_original

Then edit the fstab file..
sudo gedit /etc/fstab

Then add the line below to the fstab file

/dev/hda1  /media/windows  vfat  iocharset=utf8,umask=000   0   0

and save it and reboot.

If you stuff it all up, just delete the fstab file...
sudo rm /etc/fstab

And copy the backup to create a new fstab file...
sudo cp /etc/fstab_original /etc/fstab


Good luck.

---

