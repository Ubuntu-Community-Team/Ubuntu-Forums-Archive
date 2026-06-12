---
title: "My update is stuck"
date: 2017-01-13
forum: General Help
---

### Post by Evil Wayz on 2017-01-13
Software updater told me to update "Ubuntu base" so I did, and linux-firmware was one of the packages that needed upgrading.  Well, after about an hour, software updater crashed. I was forced to delete the lock file and use sudo dpkg --reconfigure -a.

So now it's stuck here:

```
Setting up linux-firmware (1.157.8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-040800-generic
W: plymouth module (/usr/lib/x86_64-linux-gnu/plymouth//.so) missing, skipping that theme.

```

Should I wait?  Normally the next thing that happens is a grub update.  

Running 15.04.1 LTS, with xubuntu desktop and 4.8.0 kernel.

Now I'm getting this, and i don't want to restart my computer for fear that my system is currently borked. 

```
dpkg: error: parsing file '/var/lib/dpkg/updates/0080' near line 0:
 newline in field name '#padding
```

---

### Post by Bashing-om on 2017-01-13
Evil Wayz; Hey !

You Bad bad bad boy ..... You have been around long enough to know better then to run an out of date - no longer supported release.
15.04 has been End_Of_Life for some time . It no longer has the support of the software repository .
You know the drill: Upgrade the 15.04 ( ouch; such a long hard road 15.04 -> 15.10 -> 16.04) through the EOL upgrade system . Or a fresh clean install of a current release .

[INDENT][INDENT]there is no other help
[INDENT][INDENT][INDENT]for this situation
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by howefield on 2017-01-13
> **Bashing-om said:**
> You Bad bad bad boy ..... You have been around long enough to know better then to run an out of date - no longer supported release.

My money is on a typo.. ;) 

> *I am running 16.04.1 LTS with the 4.8 kernel and xubuntu desktop.*

---

### Post by #&amp;thj^% on 2017-01-13
> **Evil Wayz said:**
> Software updater told me to update "Ubuntu base" so I did, and linux-firmware was one of the packages that needed upgrading.  Well, after about an hour, software updater crashed. I was forced to delete the lock file and use sudo dpkg --reconfigure -a.

So now it's stuck here:

```
Setting up linux-firmware (1.157.8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-040800-generic
W: plymouth module (/usr/lib/x86_64-linux-gnu/plymouth//.so) missing, skipping that theme.

```

Should I wait?  Normally the next thing that happens is a grub update.  

Running 15.04.1 LTS, with xubuntu desktop and 4.8.0 kernel.

Now I'm getting this, and i don't want to restart my computer for fear that my system is currently borked. 

```
dpkg: error: parsing file '/var/lib/dpkg/updates/0080' near line 0:
 newline in field name '#padding
```

Seen this before...and for me I did:
```
cd /var/lib/dpkg/updates && rm -rf 0080
sudo dpkg --configure -a
```
Then update again to see if the package manager is happy again.:)

---

### Post by Evil Wayz on 2017-01-13
That was a typo,  but I ran lsb_release -r just to make sure.  I'm actually running 16.04.1

I wasnt' sure if I could safely remove that line or not.  I'll try it again and report back.

It gets stuck at the same place.  If i recall linux-firmware controls the microcode for intel processors amongst other things.  What are the chances my computer will go into kernel panic and refuse to load?

---

### Post by Bashing-om on 2017-01-13
howefield; Uh Huh 

> **howefield said:**
> My money is on a typo.. ;)

Here are the 4 cookies for your money . Just to show my heart is in the right place, they are chocolate chip .

@Evil Wayz; carry on
My apologies for diverting the thread, I go back to watching over the shoulders .


[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2017-01-13
> **Evil Wayz said:**
> It gets stuck at the same place.  If i recall linux-firmware controls the microcode for intel processors amongst other things.  What are the chances my computer will go into kernel panic and refuse to load?

Lets have a quick peek then:
```
cd /var/lib/dpkg/updates
ls
```
Post back what shows there.
EDIT: Are you confusing firmware with microcode?
I have Intel here also:
```
CPU:       Quad core Intel Core i5-6400 (-MCP-) cache: 6144 KB 
           clock speeds: max: 3300 MHz 1: 898 MHz 2: 899 MHz 3: 818 MHz
           4: 879 MHz
```
And for installed I have:
```
apt policy linux-firmware
linux-firmware:
  Installed: 1.157.8
  Candidate: 1.157.8
  Version table:
 *** 1.157.8 500
        500 http://archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     1.157.6 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
     1.157.4 500
        500 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages
     1.157 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages
```
But I run with Proposed enabled ...So you may have a different version than mine.
But this:
```
apt policy intel-microcode
intel-microcode:
  Installed: (none)
  Candidate: 3.20151106.1
  Version table:
     3.20151106.1 500
        500 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages


```
I do not have installed.

---

### Post by Evil Wayz on 2017-01-13
It gets stuck at the same place.  If i recall linux-firmware controls the microcode for intel processors amongst other things.  What are the chances my computer will go into kernel panic and refuse to load?

---

### Post by #&amp;thj^% on 2017-01-13
There is always a good chance of that...
Can you post back what I asked to see in my Post #8
Lets see if we can get you healthy again.

---

### Post by Evil Wayz on 2017-01-13
```
wolf@shaitan:/var/lib/dpkg/updates$ ls
0000  0001  0002  0003  0004  0005  0006  0007  tmp.i
wolf@shaitan:/var/lib/dpkg/updates$ 

```

Firmware:  ```
wolf@shaitan:~$ apt policy linux-firmware
linux-firmware:
  Installed: 1.157.8
  Candidate: 1.157.8
  Version table:
 *** 1.157.8 500
        500 http://mirror.atlantic.net/ubuntu xenial-proposed/main amd64 Packages
        500 http://mirror.atlantic.net/ubuntu xenial-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     1.157.6 500
        500 http://mirror.atlantic.net/ubuntu xenial-updates/main amd64 Packages
        500 http://mirror.atlantic.net/ubuntu xenial-updates/main i386 Packages
     1.157.4 500
        500 http://mirror.atlantic.net/ubuntu xenial-security/main amd64 Packages
        500 http://mirror.atlantic.net/ubuntu xenial-security/main i386 Packages
     1.157 500
        500 http://mirror.atlantic.net/ubuntu xenial/main amd64 Packages
        500 http://mirror.atlantic.net/ubuntu xenial/main i386 Packages

```

intramfs has finally updated for the newest kernel.  It's currently working on one of the backups.  Why it's taking more than an hour per is beyond me.  

This is what microcode I'm running. I'm running a cpu that isn't on the recommended list for my board, but besides the complaint of a microcode error right after the bios it works fine.

```
wolf@shaitan:~$ apt policy intel-microcode
intel-microcode:
  Installed: 3.20151106.1
  Candidate: 3.20151106.1
  Version table:
 *** 3.20151106.1 500
        500 http://mirror.atlantic.net/ubuntu xenial/restricted amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by #&amp;thj^% on 2017-01-13
Actually, whether you have to install the intel-microcode package or not depends entirely on your firmware, and what processor you are using.

If you are using anything newer than a thrid-gen Core, you need the newest microcode to avoid several errata. It is much worse on 5th gen and 6th gen, where you are guaranteed to have crashes and data corruption due to issues on Intel TSX, AVX/AVX2, virtualization, and power management that were fixed in the latest microcode updates, but even 4th gen processors will misbehave badly when using older microcode.

Basically: install the intel microcode update package unless you really know better. The newer intel processors have a LOT of functionality defined or parametrized in microcode, and should be treated just like any software package that had receives critical fixes often: keep it up to date.

The issues that Intel has been fixing lately in public microcode updates are everything but minor. They fix at least one critical issue per public update.

So are you now good?

---

### Post by Evil Wayz on 2017-01-13
Im running a Q6800 quad 2 extreme.  So, intramfs has been buiklt for all three kernels i have installed, but now it's looking for 4.2, and i'm getting this:

```
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.2.0-16-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_gRuC0e/lib/modules/4.2.0-16-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_gRuC0e/lib/modules/4.2.0-16-generic/modules.builtin: No such file or directory


```

---

### Post by #&amp;thj^% on 2017-01-13
Well that is a big YUCK! Did you install "4.2.0-16-generic"?
Maybe we need to see this also:
```
ls -R /boot
```
This will be fairly big so if you would be as kind to use code tags for this output.
EDIT:Just to let you know I am going to have to catch a Plane here shortly...so I might not be around for a few (6) Hours...but will check back with you when I land.
But for now you can also go this route:
Make a backup and remove the /var/lib/dpkg/updates/0000-0007 via

```
sudo mv /var/lib/dpkg/updates/0001 /var/lib/dpkg/updates/0000 0001 0002 0003 0004 0005 0006 0007 tmp.i

```
After that:
```
sudo dpkg --configure -a
sudo apt install -f
```

---

### Post by Evil Wayz on 2017-01-14
Output of ls -R boot yields:

```
wolf@shaitan:~$ ls -R /boot
/boot:
abi-4.7.2-040702-generic         initrd.img-4.9.0-040900-generic
abi-4.8.0-040800-generic         initrd.img-4.9.3-040903-generic
abi-4.9.0-040900-generic         memtest86+.bin
abi-4.9.3-040903-generic         memtest86+.elf
config-4.7.2-040702-generic      memtest86+_multiboot.bin
config-4.8.0-040800-generic      System.map-4.7.2-040702-generic
config-4.9.0-040900-generic      System.map-4.8.0-040800-generic
config-4.9.3-040903-generic      System.map-4.9.0-040900-generic
extlinux                         System.map-4.9.3-040903-generic
grub                             vmlinuz-4.7.2-040702-generic
initrd.img-4.2.0-16-generic      vmlinuz-4.8.0-040800-generic
initrd.img-4.7.2-040702-generic  vmlinuz-4.9.0-040900-generic
initrd.img-4.8.0-040800-generic  vmlinuz-4.9.3-040903-generic

/boot/extlinux:
chain.c32      linux.cfg  memdisk.cfg    themes
extlinux.conf  memdisk    os-prober.cfg

/boot/extlinux/themes:
debian  debian-wheezy

/boot/extlinux/themes/debian-wheezy:
config.c32  memtest.bin  other.cfg   rosh.c32    stdmenu.cfg  vesamenu.c32
hdt.c32     menu.cfg     reboot.c32  splash.png  theme.cfg

/boot/grub:
fonts  gfxblacklist.txt  grub.cfg  grubenv  i386-pc  locale  unicode.pf2

/boot/grub/fonts:
unicode.pf2

/boot/grub/i386-pc:
915resolution.mod     gcry_whirlpool.mod        password_pbkdf2.mod
acpi.mod              gdb.mod                   pata.mod
adler32.mod           geli.mod                  pbkdf2.mod
affs.mod              gettext.mod               pbkdf2_test.mod
afs.mod               gfxmenu.mod               pcidump.mod
ahci.mod              gfxterm_background.mod    pci.mod
all_video.mod         gfxterm_menu.mod          plan9.mod
aout.mod              gfxterm.mod               play.mod
archelp.mod           gptsync.mod               png.mod
ata.mod               gzio.mod                  priority_queue.mod
at_keyboard.mod       halt.mod                  probe.mod
backtrace.mod         hashsum.mod               procfs.mod
bfs.mod               hdparm.mod                progress.mod
biosdisk.mod          hello.mod                 pxechain.mod
bitmap.mod            help.mod                  pxe.mod
bitmap_scale.mod      hexdump.mod               raid5rec.mod
blocklist.mod         hfs.mod                   raid6rec.mod
boot.img              hfspluscomp.mod           read.mod
boot.mod              hfsplus.mod               reboot.mod
bsd.mod               http.mod                  regexp.mod
btrfs.mod             hwmatch.mod               reiserfs.mod
bufio.mod             iorw.mod                  relocator.mod
cat.mod               iso9660.mod               romfs.mod
cbfs.mod              jfs.mod                   scsi.mod
cbls.mod              jpeg.mod                  search_fs_file.mod
cbmemc.mod            keylayouts.mod            search_fs_uuid.mod
cbtable.mod           keystatus.mod             search_label.mod
cbtime.mod            ldm.mod                   search.mod
chain.mod             legacycfg.mod             sendkey.mod
cmdline_cat_test.mod  legacy_password_test.mod  serial.mod
cmosdump.mod          linux16.mod               setjmp.mod
cmostest.mod          linux.mod                 setjmp_test.mod
cmp.mod               loadenv.mod               setpci.mod
command.lst           loopback.mod              sfs.mod
configfile.mod        lsacpi.mod                signature_test.mod
core.img              lsapm.mod                 sleep.mod
cpio_be.mod           lsmmap.mod                sleep_test.mod
cpio.mod              ls.mod                    spkmodem.mod
cpuid.mod             lspci.mod                 squash4.mod
crc64.mod             luks.mod                  syslinuxcfg.mod
cryptodisk.mod        lvm.mod                   tar.mod
crypto.lst            lzopio.mod                terminal.lst
crypto.mod            macbless.mod              terminal.mod
cs5536.mod            macho.mod                 terminfo.mod
datehook.mod          mda_text.mod              test_blockarg.mod
date.mod              mdraid09_be.mod           testload.mod
datetime.mod          mdraid09.mod              test.mod
diskfilter.mod        mdraid1x.mod              testspeed.mod
disk.mod              memdisk.mod               tftp.mod
div_test.mod          memrw.mod                 tga.mod
dm_nv.mod             minicmd.mod               time.mod
drivemap.mod          minix2_be.mod             trig.mod
echo.mod              minix2.mod                tr.mod
efiemu32.o            minix3_be.mod             truecrypt.mod
efiemu64.o            minix3.mod                true.mod
efiemu.mod            minix_be.mod              udf.mod
ehci.mod              minix.mod                 ufs1_be.mod
elf.mod               mmap.mod                  ufs1.mod
eval.mod              moddep.lst                ufs2.mod
exfat.mod             modinfo.sh                uhci.mod
exfctest.mod          morse.mod                 usb_keyboard.mod
ext2.mod              mpi.mod                   usb.mod
extcmd.mod            msdospart.mod             usbms.mod
fat.mod               multiboot2.mod            usbserial_common.mod
file.mod              multiboot.mod             usbserial_ftdi.mod
font.mod              nativedisk.mod            usbserial_pl2303.mod
freedos.mod           net.mod                   usbserial_usbdebug.mod
fshelp.mod            newc.mod                  usbtest.mod
fs.lst                nilfs2.mod                vbe.mod
functional_test.mod   normal.mod                verify.mod
gcry_arcfour.mod      ntfscomp.mod              vga.mod
gcry_blowfish.mod     ntfs.mod                  vga_text.mod
gcry_camellia.mod     ntldr.mod                 video_bochs.mod
gcry_cast5.mod        odc.mod                   video_cirrus.mod
gcry_crc.mod          offsetio.mod              video_colors.mod
gcry_des.mod          ohci.mod                  video_fb.mod
gcry_dsa.mod          part_acorn.mod            videoinfo.mod
gcry_idea.mod         part_amiga.mod            video.lst
gcry_md4.mod          part_apple.mod            video.mod
gcry_md5.mod          part_bsd.mod              videotest_checksum.mod
gcry_rfc2268.mod      part_dfly.mod             videotest.mod
gcry_rijndael.mod     part_dvh.mod              xfs.mod
gcry_rmd160.mod       part_gpt.mod              xnu.mod
gcry_rsa.mod          partmap.lst               xnu_uuid.mod
gcry_seed.mod         part_msdos.mod            xnu_uuid_test.mod
gcry_serpent.mod      part_plan.mod             xzio.mod
gcry_sha1.mod         part_sun.mod              zfscrypt.mod
gcry_sha256.mod       part_sunpc.mod            zfsinfo.mod
gcry_sha512.mod       parttool.lst              zfs.mod
gcry_tiger.mod        parttool.mod
gcry_twofish.mod      password.mod

/boot/grub/locale:
en_AU.mo  en_CA.mo  en_GB.mo  en@quot.mo

```

---

### Post by Bashing-om on 2017-01-14
Evil Wayz; Hey;

I continue to watch over your shoulder, while we await the primary responder to return - and as we still do not know what is calling that initrd.img-4.2.0-16-generic might be good to look at the base .
```

ls -al /usr/src/
ls -al /lib/modules/
dpkg -l | grep linux-

```

do what we can not to get any dirtier than we have to .

[INDENT][INDENT]what to do
[INDENT][INDENT]oh what to do
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-14
Output of first command:; ```
 wolf@shaitan:~$ ls -al /usr/src/
total 56
drwxr-xr-x 14 root root 4096 Jan 13 22:16 .
drwxr-xr-x 12 root root 4096 Apr 30  2016 ..
drwxr-xr-x  2 root root 4096 May  1  2016 bbswitch-0.8
drwxr-xr-x  3 root root 4096 May  9  2016 libdvd-pkg
drwxr-xr-x 24 root root 4096 Aug 30 22:14 linux-headers-4.7.2-040702
drwxr-xr-x  7 root root 4096 Aug 30 22:14 linux-headers-4.7.2-040702-generic
drwxr-xr-x 24 root root 4096 Nov  4 19:05 linux-headers-4.8.0-040800
drwxr-xr-x  7 root root 4096 Nov  4 19:05 linux-headers-4.8.0-040800-generic
drwxr-xr-x 24 root root 4096 Jan 13 15:43 linux-headers-4.9.0-040900
drwxr-xr-x  7 root root 4096 Jan 13 16:12 linux-headers-4.9.0-040900-generic
drwxr-xr-x 24 root root 4096 Jan 13 22:03 linux-headers-4.9.3-040903
drwxr-xr-x  7 root root 4096 Jan 13 22:20 linux-headers-4.9.3-040903-generic
drwxr-xr-x  8 root root 4096 Nov 19 19:22 nvidia-370-370.28
drwxr-xr-x  2 root root 4096 May 25  2016 .tmp_versions
wolf@shaitan:~$ 

```

Output of second command is
```

wolf@shaitan:~$ ls -al /lib/modules/
total 28
drwxr-xr-x  7 root root 4096 Jan 13 22:16 .
drwxr-xr-x 26 root root 4096 Nov 17 15:31 ..
drwxr-xr-x  2 root root 4096 May  1  2016 3.13.0-80-generic
drwxr-xr-x  6 root root 4096 Nov 19 19:21 4.7.2-040702-generic
drwxr-xr-x  6 root root 4096 Nov 19 19:25 4.8.0-040800-generic
drwxr-xr-x  6 root root 4096 Jan 13 16:26 4.9.0-040900-generic
drwxr-xr-x  6 root root 4096 Jan 13 23:01 4.9.3-040903-generic
wolf@shaitan:~
```

Output of third command is
```

wolf@shaitan:~$ dpkg -l | grep linux-
ii  ladspa-sdk                                            1.13-2                                        amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                            4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                        1.161.1                                       all          Firmware for Linux kernel drivers
ii  linux-firmware-nonfree                                1.16                                          all          Non-free firmware for Linux kernel drivers
ii  linux-headers-4.7.2-040702                            4.7.2-040702.201608201334                     all          Header files related to Linux kernel version 4.7.2
ii  linux-headers-4.7.2-040702-generic                    4.7.2-040702.201608201334                     amd64        Linux kernel headers for version 4.7.2 on 64 bit x86 SMP
ii  linux-headers-4.8.0-040800                            4.8.0-040800.201610022031                     all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-040800-generic                    4.8.0-040800.201610022031                     amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.9.0-040900                            4.9.0-040900.201612111631                     all          Header files related to Linux kernel version 4.9.0
ii  linux-headers-4.9.0-040900-generic                    4.9.0-040900.201612111631                     amd64        Linux kernel headers for version 4.9.0 on 64 bit x86 SMP
ii  linux-headers-4.9.3-040903                            4.9.3-040903.201701120631                     all          Header files related to Linux kernel version 4.9.3
ii  linux-headers-4.9.3-040903-generic                    4.9.3-040903.201701120631                     amd64        Linux kernel headers for version 4.9.3 on 64 bit x86 SMP
ii  linux-image-4.7.2-040702-generic                      4.7.2-040702.201608201334                     amd64        Linux kernel image for version 4.7.2 on 64 bit x86 SMP
ii  linux-image-4.8.0-040800-generic                      4.8.0-040800.201610022031                     amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.9.0-040900-generic                      4.9.0-040900.201612111631                     amd64        Linux kernel image for version 4.9.0 on 64 bit x86 SMP
ii  linux-image-4.9.3-040903-generic                      4.9.3-040903.201701120631                     amd64        Linux kernel image for version 4.9.3 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                  4.4.0-59.80                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by Bashing-om on 2017-01-14
Evil Wayz; Hummmmm ..

A minor issue here :
> 
drwxr-xr-x  2 root root 4096 May  1  2016 3.13.0-80-generic

but nothing to do with the 4.2.0-16 kernel !

We get any hints from:
```

ls -al /vmlinuz* /initrd.img*

```

looking for some direction somewhere from the system.

[INDENT][INDENT]ask the system  the right question
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-14
Not sure why that 3 kernel popped up, it was removed long ago.

ls -al /vmlinuz* /initrd.img* yields:```

wolf@shaitan:~$ ls -al /vmlinuz* /initrd.img*
lrwxrwxrwx 1 root root 36 Jan 13 22:44 /initrd.img -> boot/initrd.img-4.9.3-040903-generic
lrwxrwxrwx 1 root root 36 Jan 13 16:26 /initrd.img.old -> boot/initrd.img-4.9.0-040900-generic
lrwxrwxrwx 1 root root 33 Jan 13 22:44 /vmlinuz -> boot/vmlinuz-4.9.3-040903-generic
lrwxrwxrwx 1 root root 33 Jan 13 16:26 /vmlinuz.old -> boot/vmlinuz-4.9.0-040900-generic
wolf@shaitan:~$ 

```

---

### Post by Bashing-om on 2017-01-14
Evil Wayz; Humm ...

Got me , no telling here either what is calling the 4.2.0-16 kernel .

I am very interested in learning how to learn what is calling it . Will go back to lurk mode ; and continue to ponder this situation .

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-14
while we are doing the waiting thing, does anyone know the name of the meta package that automatically gives you the most current stable kernel, and updates it?

---

### Post by Bashing-om on 2017-01-14
Evil Wayz; Hey ...

I did note to self that you did not have  linux-image-generic installed, Thought as you are not running repo kernels you did not need nor want it. No idea presently on your system what all will be pulled in when it is installed .

[INDENT][INDENT]in the process of learning
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-14
I'm using the mainline kernel because I'm using a cpu that fits in the socket but isn't on the recommended list, as well as trying to get some HDMI features to work.

---

### Post by #&amp;thj^% on 2017-01-16
Well sorry for the long delay....sometimes Life happens.
But at this point...I really have nothing to offer here???
I'm totally Stumped how any of this happened in the first place?
But it sounds like this install is becoming a bit of this and that.(That just makes it a lot tougher in knowing what to do next)
I really thought this could be just a five minute fix...but the more information you provide...The more I question if it can be salvaged to a dependable working OS.
Best of Luck & Kind Regards

---

### Post by Bashing-om on 2017-01-16
Evil Wayz; Welllll ........


Still with no idea of what is calling the 4.2.0-16 kernel  .
I would love to get the smarter here .

Can we get any hints:
```

sudo update-initramfs -u

```
rebuilding the current image, see what the system advises .

[INDENT][INDENT]what to do
[INDENT][INDENT][INDENT]oh what to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-16
All that comes up is this:

```
update-initramfs: Generating /boot/initrd.img-4.9.3-040903-generic

```

---

### Post by Bashing-om on 2017-01-16
Evil Wayzll Ho Kay;

That is good - as far as it goes . but no hints !

reboot and run a new:
```

sudo apt update
sudo apt full-upgrade

```
let's see now where it fails .

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by mc4man on 2017-01-17
Is there any point to keeping the /boot/initrd.img-4.2.0-16-generic file?

---

### Post by Bashing-om on 2017-01-17
@mc4man;

No point as far as I know to keep that straggler nitrd.img-4.2.0-16-generic file . If it is not interfering leave it till we also clean up  3.13.0-80-generic pieces? Maybe we can come up with a clean way to do these ?? 

@ Evil Wayz;
Presently I will be interested in seeing a new fault failure advisory from the update/upgrade process.

[INDENT][INDENT]just my thoughts on the matter
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-18
No matter what kernel i use, and what type, It gets stuck on this:
```
 pci 0000:01:00:0 Video device with shadowed ROM at [mem 0x000c0000-0x000dffff] 
```

---

### Post by Bashing-om on 2017-01-18
Evil Wayz; Yukkie !

What is the graphic's card you have installed ? Maybe we can work a work-a-round to boot with the fall back graphic's driver .

[INDENT][INDENT]getting on too deep ?
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-18
Its an nvidia GT 730.  Thing is, it does this sometimes, and usually the work around is let hte coouter cool all the way down, and then run the recovery kernel.  Only its not working this time.

it occurs to me, the graphics driver didn't get rebuilt when i got the new kernel, maybe thats the problem.

---

### Post by Bashing-om on 2017-01-18
Evil Wayz; Oh Boy .

> 
then run the recovery kernel. Only its not working this time. 

so much for my thought for that work-a-round.

Let's try this to get to a terminal:
at the grub boot menu 'e' key for edit mode -> boot parameters screen.
Arrow down to the line starting with linux and replace quiet splash and all after with the term systemd.unit=multi-user.target .
key combo ctl+x to continue to TTY1 . 
can you log into the system here ?

[INDENT][INDENT]maybe yes
could be not so yes 
/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-18
" systemd.unit=multi-user.target " is what you want me to try?

---

### Post by Bashing-om on 2017-01-18
Evil Wayz; Ye Yah ,

systemd.unit=multi-user.target
as the only boot option . 
See what we can find to work from .

Tough to do the impossible
[INDENT][INDENT]with nothing[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-19
I don't have a nosplash.  I do have this:

[IMG]http://i66.tinypic.com/25qym0x.jpg[/IMG]

Should I try inserting it after ro nomodeset?

---

### Post by ventrical on 2017-01-19
I just had this happen with Mate 16.04 with the exception that I got a <apt-get -f install> so I

```

sudo apt-get -f install

```
 and it pulled something busted and fixed it. I had a /ppa that hadn't been updated in a while and it was blocking normal install.

Hey .. do you have any ppas?

regards..

---

### Post by Evil Wayz on 2017-01-19
I'm sure I do.  That's not the problem though, I can't get the OS to load, it sticks either on that video error, or a usb error.

---

### Post by Bashing-om on 2017-01-19
Evil Wayz; Hello;

Regret the delay in getting back to ya . The real life sometimes has it way .

As we are attempting booting to terminal, at this one time the 'nomodeset' boot parameter will not be needed. We try and boot to terminal where the GUI driver is not yet called for. Where else are you setting the boot parameter nomodeset ? Grub ? do we need to remove it ?
Replace nomodeset and ro with systemd.unit=multi-user.target . Key combo ctl+x to continue the boot process. 
Do you get a terminal and can you log into the system from here ?

[INDENT][INDENT]where there is a will
[INDENT][INDENT][INDENT]we will find a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-20
Didn't work.  I tried using the upstart kernel an it cleared out a bunch of orphaned inodes and got all the way to ohci irq 21 memory error and then got stuck again.

---

### Post by Bashing-om on 2017-01-20
Evil Wayz; Ouch !!

A memory error - such as ram ?? then for sure I would be running the mem test overnight .
Once ram is known to be good, next up is to run a file system check (e2fsck) from a liveUSB .

[INDENT][INDENT]Houston;
[INDENT][INDENT][INDENT]we have a problem
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-20
Didn't work.  I tried using the upstart kernel an it cleared out a bunch of orphaned inodes and got all the way to ohci irq 21 memory error and then got stuck again.

Heres the rub, i can't get it to read of a USB stick. If I end up throwing in the towel, im wondering how to get the data out of my two encrypted folders.

I am also curious if this is some sort of heat issue.  If i leave the tower off til its cool i don't get that video error, it usually gets stuck reading one of the hard drives, or i get multiple usb hub errors.

---

### Post by Bashing-om on 2017-01-20
Evil Wayz; Ohweeee ..

That sure points to hardware problems. A good cleaning of the box sure will not hurt .
As to recovering encrypted volumes - can not advise as I have no experience here .

[ I run in a very adverse environment, and I must clean my box about every 2 weeks ]

and gate or gate malfunction at hardware level;
[INDENT][INDENT]no telling what the output will be
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-20
so. Kaspersky or SuperGrub2?

---

### Post by Evil Wayz on 2017-01-20
Just for giggles I started the box up one more time, using the 4.8 recovery kernel.  Again this is not a permanent solution. just a work around.

And it's working again.

Until I have to restart it again and go thru this day or two process to get it working again.

It doesn't appear to be running hot.  I'm currently watching a movie, downloading torrents at around 750kbs, and i have 8 tabs open on Firefox.

[IMG]http://i67.tinypic.com/9bdttc.jpg[/IMG]

---

### Post by Bashing-om on 2017-01-21
Evil Wayz; Welp ...

To my mind, we should return to a mainline kernel, and see what the issues are with a supported kernel .

With a 4.8 kernel on xenial you should be talking to the developers.
Once we have the :
> 
4.4.0-59-generic

kernel installed, you still maintain the ability to boot the 4.8 kernel .

[INDENT][INDENT]leastways, just my thought
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-21
4.4.0-60-generic and 59 are both installed.  THey just don't work.

---

### Post by Bashing-om on 2017-01-21
Evil Wayz; Hey :
> 
THey just don't work. 

does not tell much and does nothing to help find the cause.
The -60 has not been released as of this date, how did you install ? Best I recall you do not have 'linux-generic linux-image-generic " installed to support the current kernels .

Show a new of what is installed:
```

dpkg -l | grep linux-

```
If ya want to work from a supported kernel . We see what we can do to get ya functional .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-21
By "do not work" i mean they either get stuck at that video error, or they get stuck with usb hub error.  THe only kernel that works is the 4.8 recovery.

As to the .60-generic, it just showed up in my software update. 

dpkg -l | grep linux- yields:
```
ii  ladspa-sdk                                            1.13-2                                        amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                            4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                        1.161.1                                       all          Firmware for Linux kernel drivers
ii  linux-firmware-nonfree                                1.16                                          all          Non-free firmware for Linux kernel drivers
ii  linux-headers-4.4.0-59                                4.4.0-59.80                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic                        4.4.0-59.80                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.7.2-040702                            4.7.2-040702.201608201334                     all          Header files related to Linux kernel version 4.7.2
ii  linux-headers-4.7.2-040702-generic                    4.7.2-040702.201608201334                     amd64        Linux kernel headers for version 4.7.2 on 64 bit x86 SMP
ii  linux-headers-4.8.0-040800                            4.8.0-040800.201610022031                     all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-040800-generic                    4.8.0-040800.201610022031                     amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.9.0-040900                            4.9.0-040900.201612111631                     all          Header files related to Linux kernel version 4.9.0
ii  linux-headers-4.9.0-040900-generic                    4.9.0-040900.201612111631                     amd64        Linux kernel headers for version 4.9.0 on 64 bit x86 SMP
ii  linux-headers-4.9.3-040903                            4.9.3-040903.201701120631                     all          Header files related to Linux kernel version 4.9.3
ii  linux-headers-4.9.3-040903-generic                    4.9.3-040903.201701120631                     amd64        Linux kernel headers for version 4.9.3 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic                          4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-60-generic                          4.4.0-60.81                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                          4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.7.2-040702-generic                      4.7.2-040702.201608201334                     amd64        Linux kernel image for version 4.7.2 on 64 bit x86 SMP
ii  linux-image-4.8.0-040800-generic                      4.8.0-040800.201610022031                     amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.9.0-040900-generic                      4.9.0-040900.201612111631                     amd64        Linux kernel image for version 4.9.0 on 64 bit x86 SMP
ii  linux-image-4.9.3-040903-generic                      4.9.3-040903.201701120631                     amd64        Linux kernel image for version 4.9.3 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic                    4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-60-generic                    4.4.0-60.81                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic                    4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                   4.4.0.62.65                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  4.4.0-62.83                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  linux-source-4.4.0                                    4.4.0-62.83                                   all          Linux kernel source for version 4.4.0 with Ubuntu patches
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

I notice that 3. whatever kernel fragment is gone.... I also see linux-image-extra-4.4.0-62-generic??????????

---

### Post by Bashing-om on 2017-01-21
Evil Wayz; Humm ..

You only have bits and pieces of both the -59 and -60 kernels installed.
My 16.04 system:
> 
sysop@x1604:/$ dpkg -l | grep linux-
ii  linux-base                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                              1.157.6                                       all          Firmware for Linux kernel drivers
ii  linux-generic                               4.4.0.59.62                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-57                      4.4.0-57.78                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic              4.4.0-57.78                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-59                      4.4.0-59.80                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic              4.4.0-59.80                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                       4.4.0.59.62                                   amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-57-generic                4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic                4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic          4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic          4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                         4.4.0.59.62                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-59.80                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
sysop@x1604:

The -60 kernel has yet to hit the repo :
> 
sysop@x1604:/$ apt list linux-image-extra-4.4.0-59-generic
Listing... Done
linux-image-extra-4.4.0-59-generic/xenial-updates,xenial-security,now 4.4.0-59.80 amd64 [installed,automatic]
sysop@x1604:/$ apt list linux-image-extra-4.4.0-60-generic
Listing... Done
sysop@x1604:/$


So we are back to working with the -59 kernel, If ya desire to try and find out the why the -59 fails on your system.
One possible reason is that there is not the drive space available to install all the components.
what have we for disk space usage ?
```

df -h
df -i

```
and I do propose we fully install the -59 kernel - one way or another - and try and get the -59 kernel functional .
It is your system, your time and effort ...

[INDENT][INDENT]what do you want to do ?
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-21
I usually operate on " if it aint' broke don't fix it."  Would be nice to boot to a non upstart/recover kernel though.  

wolf@shaitan:~$ df -h
```

Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           799M   72M  727M   9% /run
/dev/sdb1       1.8T  1.8T   62G  97% /
tmpfs           3.9G   33M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdd1       2.7T  2.6T   11G 100% /mnt/a3c50df9-9854-4f86-8be3-69b7960aec68
/dev/sdc1       1.8T  1.6T  166G  91% /mnt/e98468c7-fb88-4b83-b603-402fd5575208
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           799M   64K  799M   1% /run/user/1000
/dev/sda1       1.8T  1.6T  205G  89% /media/wolf/2a1e3aba-3972-4747-8794-cb8a38caf061
/dev/sr0        666M  666M     0 100% /media/wolf/WD SmartWare
/dev/sde1       1.9T  1.3T  597G  68% /media/wolf/My Book1

```

wolf@shaitan:~$ df -i
```
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             1015759    524   1015235    1% /dev
tmpfs            1021988    841   1021147    1% /run
/dev/sdb1      121250080 916625 120333455    1% /
tmpfs            1021988     37   1021951    1% /dev/shm
tmpfs            1021988      7   1021981    1% /run/lock
tmpfs            1021988     17   1021971    1% /sys/fs/cgroup
/dev/sdd1      183148544  31237 183117307    1% /mnt/a3c50df9-9854-4f86-8be3-69b7960aec68
/dev/sdc1      122101760 150899 121950861    1% /mnt/e98468c7-fb88-4b83-b603-402fd5575208
cgmfs            1021988     13   1021975    1% /run/cgmanager/fs
tmpfs            1021988     32   1021956    1% /run/user/1000
/dev/sda1      122101760 163317 121938443    1% /media/wolf/2a1e3aba-3972-4747-8794-cb8a38caf061
/dev/sr0            1454   1454         0  100% /media/wolf/WD SmartWare
/dev/sde1      625519308 108392 625410916    1% /media/wolf/My Book1
```

---

### Post by Bashing-om on 2017-01-21
Evil Wayz; WoW ...

Root with 1.8 Terra bytes and only 62 Gigs available However, at 97 % capacity you are looking at the journaling not able to compensate ; file system fragmentation .
Can you get rid of a LOT of old files ??

Next up to cover our bases, is the video situation. I can foresee we will have the display driver to re-build.
show:
```

sudo lshw -C display

```
Let's see what we are working with.

We then clean up - preparing to install the 4.4.0-59-generic kernel.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-21
How much do I need to free up, it's entirely media. 

wolf@shaitan:~$ sudo lshw -C display
```


  *-display               
       description: VGA compatible controller
       product: GK208 [GeForce GT 730]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:31 memory:eb000000-ebffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:2000(size=128) memory:c0000-dffff

```

---

### Post by Bashing-om on 2017-01-21
Evil Wayz; Welllllll ...

with 1,8 TB ... ouch .. need to get down to 90% capacity .. that may take some doing . 
> 
 you will start to see fragmentation if your file system fills up. If it’s 95% (or even 80%) full, 

particularly so with the large media files .
> 
Fragmentation thus only becomes an issue on ths latter type of system when a disk is so full that there just aren't any gaps a large file can be put into without splitting it up. So long as the disk is less than about 80% full, this is unlikely to happen.

as per : [https://www.howtoforge.com/tutorial/linux-filesystem-defrag/](https://www.howtoforge.com/tutorial/linux-filesystem-defrag/)
With 1.8 TB capacity, I would think 90% to be a reasonable target . If ya do your careful homework you will find the tools to defrag the hard drive in linux.

Now back to installing the -59 kernel.

Let's try:
```

sudo apt purge linux-firmware linux-generic linux-headers-generic

```
to remove the old associations. ,
see now what results:
```

sudo apt update
sudo apt install linux-firmware linux-generic linux-image-generic linux-headers-generic
sudo apt install --reinstall linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic linux-image-4.4.0-59-generic inux-image-extra-4.4.0-59-generic --fix-missing
sudo update-grub

```

Now what does grub show for booting ?
```

ls -al /vmlinuz* /initrd.img*

```

and did the 4.4.0-59 kernel reinstall ?
show a new:
```

dpkg -l | grep linux-

```
maybe now we can re-boot to see the real effect . Depending on what we see here .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-22
wolf@shaitan:~$ ls -al /vmlinuz* /initrd.img*
```

lrwxrwxrwx 1 root root 32 Jan 22 14:36 /initrd.img -> boot/initrd.img-4.4.0-62-generic
lrwxrwxrwx 1 root root 32 Jan 16 16:51 /initrd.img.old -> boot/initrd.img-4.4.0-60-generic
lrwxrwxrwx 1 root root 29 Jan 22 14:36 /vmlinuz -> boot/vmlinuz-4.4.0-62-generic
lrwxrwxrwx 1 root root 29 Jan 16 16:51 /vmlinuz.old -> boot/vmlinuz-4.4.0-60-generic

```

Looks like it installed .62
wolf@shaitan:~$ dpkg -l | grep linux-
```

ii  ladspa-sdk                                            1.13-2                                        amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                            4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                        1.157.8                                       all          Firmware for Linux kernel drivers
ii  linux-firmware-nonfree                                1.16                                          all          Non-free firmware for Linux kernel drivers
ii  linux-generic                                         4.4.0.62.65                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-59                                4.4.0-59.80                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic                        4.4.0-59.80                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-62                                4.4.0-62.83                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-62-generic                        4.4.0-62.83                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.7.2-040702                            4.7.2-040702.201608201334                     all          Header files related to Linux kernel version 4.7.2
ii  linux-headers-4.7.2-040702-generic                    4.7.2-040702.201608201334                     amd64        Linux kernel headers for version 4.7.2 on 64 bit x86 SMP
ii  linux-headers-4.8.0-040800                            4.8.0-040800.201610022031                     all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-040800-generic                    4.8.0-040800.201610022031                     amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.9.0-040900                            4.9.0-040900.201612111631                     all          Header files related to Linux kernel version 4.9.0
ii  linux-headers-4.9.0-040900-generic                    4.9.0-040900.201612111631                     amd64        Linux kernel headers for version 4.9.0 on 64 bit x86 SMP
ii  linux-headers-4.9.3-040903                            4.9.3-040903.201701120631                     all          Header files related to Linux kernel version 4.9.3
ii  linux-headers-4.9.3-040903-generic                    4.9.3-040903.201701120631                     amd64        Linux kernel headers for version 4.9.3 on 64 bit x86 SMP
ii  linux-headers-generic                                 4.4.0.62.65                                   amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-59-generic                          4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-60-generic                          4.4.0-60.81                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                          4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.7.2-040702-generic                      4.7.2-040702.201608201334                     amd64        Linux kernel image for version 4.7.2 on 64 bit x86 SMP
ii  linux-image-4.8.0-040800-generic                      4.8.0-040800.201610022031                     amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.9.0-040900-generic                      4.9.0-040900.201612111631                     amd64        Linux kernel image for version 4.9.0 on 64 bit x86 SMP
ii  linux-image-4.9.3-040903-generic                      4.9.3-040903.201701120631                     amd64        Linux kernel image for version 4.9.3 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic                    4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-60-generic                    4.4.0-60.81                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic                    4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                   4.4.0.62.65                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  4.4.0-62.83                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  linux-source-4.4.0                                    4.4.0-62.83                                   all          Linux kernel source for version 4.4.0 with Ubuntu patches
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2017-01-22
Evil Wayz; Huh ...

I am surprised as the re-install linux-firmware  pulled in the correct version .. so why oh why is the system pulling a -62 version kernel that is not in the repo ???
We got a PPA at play here ?
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
that we need to nullify to get booting the -59 kernel ?

Looks as if the -59 kernel is installed, can you choose it from grub's boot menu ? And if so what results in attempting to boot the -59 kernel ? 
Anticipating a need to install a proprietary graphic's driver for the GeForce GT 730 card .

[INDENT][INDENT]seems with me
[INDENT][INDENT][INDENT]a process of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Evil Wayz on 2017-01-31
I'm back, this is hte first time I've been able to use my computer.  Sort of.  It doesn't recognize usb hard drives at this time.  Prior to rebooting, I cleared 200gb of space off the drive and defragged.  I am more than a little annoyed that i buy a 2tb drive and only get 1.8gb to start with, and i'm expected to keep another 200gb free so the OS can do its job.  Is there a way to reset the usb hubs without restarting the computer?  I don't want to go days without a working desktop again.

---

