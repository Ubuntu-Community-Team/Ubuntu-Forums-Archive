---
title: "Flummoxed about kernel cruft in /boot"
date: 2014-08-30
forum: General Help
---

### Post by kansasnoob on 2014-08-30
I know there are a gazillion threads about removing old kernels and cleaning up /boot, but this is kind of a doozy. This should be a fun ride for anyone up to the challenge.

I find that the old kernels are removed but cruft remains in /boot and therefore shows up in every grub update. I have two installs of Trusty on the same machine (one on the main drive that I use for everyday purposes and another on a drive that I connect when I'm iso testing so I don't put my data at risk) and only one is effected. The only difference I can think of is that **[COLOR="#FF0000"]this install began as an upgrade via live DVD[/COLOR]** so a lot of the logs are different, notice "ubiquity-apt-clone":

```
lance@lance-desktop:~$ ls /
bin    etc             lib         opt   sbin  **[COLOR="#FF0000"]ubiquity-apt-clone[/COLOR]**  vmlinuz.old
boot   home            lost+found  proc  srv   usr
cdrom  initrd.img      media       root  sys   var
dev    initrd.img.old  mnt         run   tmp   vmlinuz

```

And the absence of some things like installer info in /var/log:

```
lance@lance-desktop:~$ ls /var/log
alternatives.log       dmesg            pm-powersave.log
alternatives.log.1     dmesg.0          pm-powersave.log.1
alternatives.log.2.gz  dmesg.1.gz       pm-powersave.log.2.gz
apport.log             dmesg.2.gz       samba
apport.log.1           dmesg.3.gz       speech-dispatcher
apport.log.2.gz        dmesg.4.gz       syslog
apport.log.3.gz        dpkg.log         syslog.1
apport.log.4.gz        dpkg.log.1       syslog.2.gz
apport.log.5.gz        dpkg.log.2.gz    syslog.3.gz
apport.log.6.gz        faillog          syslog.4.gz
apt                    fontconfig.log   syslog.5.gz
auth.log               fsck             syslog.6.gz
auth.log.1             gpu-manager.log  syslog.7.gz
auth.log.2.gz          gufw.log         udev
auth.log.3.gz          hp               ufw.log
auth.log.4.gz          kern.log         unattended-upgrades
boot.log               kern.log.1       upstart
bootstrap.log          kern.log.2.gz    wtmp
btmp                   kern.log.3.gz    wtmp.1
btmp.1                 kern.log.4.gz    Xorg.0.log
cups                   lastlog          Xorg.0.log.old
dist-upgrade           lightdm

```

I've personally used Synaptic to manually remove old kernels for a long time. Typically I'll just run "sudo update-grub" and then copy-n-paste the actual number of the kernel I wish to remove into the quick filter. For example, on the effected system I get:

```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-23-generic
Found initrd image: /boot/initrd.img-3.13.0-23-generic
Found linux image: /boot/vmlinuz-3.13.0-22-generic
Found initrd image: /boot/initrd.img-3.13.0-22-generic
Found linux image: /boot/vmlinuz-3.13.0-21-generic
Found initrd image: /boot/initrd.img-3.13.0-21-generic
Found linux image: /boot/vmlinuz-3.13.0-20-generic
Found initrd image: /boot/initrd.img-3.13.0-20-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin

```

So if I wanted to remove all parts of "3.13.0-34" I'd do this:

[ATTACH=CONFIG]255960[/ATTACH]

But if I do the same with the oldest - nothing (probably an old kernel left over from the Trusty dev cycle):

[ATTACH=CONFIG]255961[/ATTACH]

Or even "3.13.0-29" - still nothing installed:

[ATTACH=CONFIG]255962[/ATTACH]

But look at /boot:

```
lance@lance-desktop:~$ ls -a /boot
.                             initrd.img-3.13.0-29-generic
..                            initrd.img-3.13.0-34-generic
abi-3.13.0-20-generic         initrd.img-3.13.0-35-generic
abi-3.13.0-21-generic         memtest86+.bin
abi-3.13.0-22-generic         memtest86+.elf
abi-3.13.0-23-generic         memtest86+_multiboot.bin
abi-3.13.0-29-generic         System.map-3.13.0-20-generic
abi-3.13.0-34-generic         System.map-3.13.0-21-generic
abi-3.13.0-35-generic         System.map-3.13.0-22-generic
config-3.13.0-20-generic      System.map-3.13.0-23-generic
config-3.13.0-21-generic      System.map-3.13.0-29-generic
config-3.13.0-22-generic      System.map-3.13.0-34-generic
config-3.13.0-23-generic      System.map-3.13.0-35-generic
config-3.13.0-29-generic      vmlinuz-3.13.0-20-generic
config-3.13.0-34-generic      vmlinuz-3.13.0-21-generic
config-3.13.0-35-generic      vmlinuz-3.13.0-22-generic
grub                          vmlinuz-3.13.0-23-generic
initrd.img-3.13.0-20-generic  vmlinuz-3.13.0-29-generic
initrd.img-3.13.0-21-generic  vmlinuz-3.13.0-34-generic
initrd.img-3.13.0-22-generic  vmlinuz-3.13.0-35-generic
initrd.img-3.13.0-23-generic

```

Or this:

```
lance@lance-desktop:~$ dpkg -l 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version              Architecture         Description
+++-===============================-====================-====================-====================================================================
un  linux-image                     <none>               <none>               (no description available)
un  linux-image-3.0                 <none>               <none>               (no description available)
rc  linux-image-3.13.0-24-generic   3.13.0-24.47         i386                 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.13.0-30-generic   3.13.0-30.55         i386                 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.13.0-32-generic   3.13.0-32.57         i386                 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-34-generic   3.13.0-34.60         i386                 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic   3.13.0-35.62         i386                 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-24-gen 3.13.0-24.47         i386                 Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-30-gen 3.13.0-30.55         i386                 Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-32-gen 3.13.0-32.57         i386                 Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-34-gen 3.13.0-34.60         i386                 Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-gen 3.13.0-35.62         i386                 Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic             3.13.0.35.42         i386                 Generic Linux kernel image

```

So things have not cleaned up as they should have. Now what? I'm tempted to just rm -r the parts I don't want in /boot but I'm not sure, and I'm really curious what caused this to begin with. Any thoughts?

---

### Post by kansasnoob on 2014-08-30
Actually that /ubiquity-apt-clone is interesting:

```
lance@lance-desktop:~$ ls /ubiquity-apt-clone
apt-clone-state-ubuntu.tar.gz

```

In the tar.gz is an "installed.pkgs" and the snip-it regarding kernels:

```
linux-firmware 1.127.4 1
linux-generic 3.13.0.30.36 0
linux-headers-3.13.0-20 3.13.0-20.42 1
linux-headers-3.13.0-20-generic 3.13.0-20.42 1
linux-headers-3.13.0-21 3.13.0-21.43 1
linux-headers-3.13.0-21-generic 3.13.0-21.43 1
linux-headers-3.13.0-22 3.13.0-22.44 1
linux-headers-3.13.0-22-generic 3.13.0-22.44 1
linux-headers-3.13.0-23 3.13.0-23.45 1
linux-headers-3.13.0-23-generic 3.13.0-23.45 1
linux-headers-3.13.0-24 3.13.0-24.47 1
linux-headers-3.13.0-24-generic 3.13.0-24.47 1
linux-headers-3.13.0-29 3.13.0-29.53 1
linux-headers-3.13.0-29-generic 3.13.0-29.53 1
linux-headers-3.13.0-30 3.13.0-30.54 1
linux-headers-3.13.0-30-generic 3.13.0-30.54 1
linux-headers-generic 3.13.0.30.36 1
linux-image-3.13.0-20-generic 3.13.0-20.42 1
linux-image-3.13.0-21-generic 3.13.0-21.43 1
linux-image-3.13.0-22-generic 3.13.0-22.44 1
linux-image-3.13.0-23-generic 3.13.0-23.45 1
linux-image-3.13.0-24-generic 3.13.0-24.47 1
linux-image-3.13.0-29-generic 3.13.0-29.53 1
linux-image-3.13.0-30-generic 3.13.0-30.54 1
linux-image-extra-3.13.0-20-generic 3.13.0-20.42 1
linux-image-extra-3.13.0-21-generic 3.13.0-21.43 1
linux-image-extra-3.13.0-22-generic 3.13.0-22.44 1
linux-image-extra-3.13.0-23-generic 3.13.0-23.45 1
linux-image-extra-3.13.0-24-generic 3.13.0-24.47 1
linux-image-extra-3.13.0-29-generic 3.13.0-29.53 1
linux-image-extra-3.13.0-30-generic 3.13.0-30.54 1
linux-image-generic 3.13.0.30.36 1
linux-libc-dev 3.13.0-30.54 0
```

Sort of makes me think that's one more reason to only perform totally fresh installs!

Aha, also an "extended_states" log in there:

```
Package: linux-image-extra-3.13.0-20-generic
Architecture: i386
Auto-Installed: 1

Package: linux-image-3.13.0-20-generic
Architecture: i386
Auto-Installed: 1

Package: linux-headers-3.13.0-20
Architecture: i386
Auto-Installed: 1

Package: linux-headers-3.13.0-20-generic
Architecture: i386
Auto-Installed: 1

Package: libqupzilla1
Architecture: i386
Auto-Installed: 1

Package: libqt4-sql-sqlite
Architecture: i386
Auto-Installed: 1

Package: tasksel-data
Architecture: i386
Auto-Installed: 1

Package: aptitude-common
Architecture: i386
Auto-Installed: 1

Package: libboost-iostreams1.54.0
Architecture: i386
Auto-Installed: 1

Package: libcwidget3
Architecture: i386
Auto-Installed: 1

Package: aptitude
Architecture: i386
Auto-Installed: 1

Package: linux-image-extra-3.13.0-21-generic
Architecture: i386
Auto-Installed: 1

Package: linux-image-3.13.0-21-generic
Architecture: i386
Auto-Installed: 1

Package: linux-headers-3.13.0-21
Architecture: i386
Auto-Installed: 1

Package: libwayland-egl1-mesa
Architecture: i386
Auto-Installed: 1

Package: linux-headers-3.13.0-21-generic
Architecture: i386
Auto-Installed: 1

Package: libcgmanager0
Architecture: i386
Auto-Installed: 1

Package: linux-image-extra-3.13.0-22-generic
Architecture: i386
Auto-Installed: 1

Package: linux-headers-3.13.0-22
Architecture: i386
Auto-Installed: 1

Package: linux-headers-3.13.0-22-generic
Architecture: i386
Auto-Installed: 1
```

So I really think that reinstall from a few months back was just a bad idea.

---

### Post by SeijiSensei on 2014-08-30
I'm not sure what you're asking.  Do you want to remove the stale kernels and associated files from /boot?  You can do that as root just using rm:
```

# cd /boot
# rm -f *3.13.0-20*

```
That removes the files associated with the 3.13.0-20 kernel version.  Just don't delete the ones currently being used during boot, usually the most recent and the next most recent versions.  I've done this a number of times when kernels were not being removed automatically.  I think if there are stale kernels older than the preceding version, they are not marked for autoremove.  Once you reduce the list of kernels to just the current and previous versions, autoremove appears to sync up correctly in later updates.

---

### Post by kansasnoob on 2014-08-30
> **SeijiSensei said:**
> I'm not sure what you're asking.  Do you want to remove the stale kernels and associated files from /boot?  You can do that as root just using rm:
```

# cd /boot
# rm -f *3.13.0-20*

```
That removes the files associated with the 3.13.0-20 kernel version.  Just don't delete the ones currently being used during boot, usually the most recent and the next most recent versions.  I've done this a number of times when kernels were not being removed automatically.  I think if there are stale kernels older than the preceding version, they are not marked for autoremove.  Once you reduce the list of kernels to just the current and previous versions, autoremove appears to sync up correctly in later updates.

I was thinking about using rm -r with each specific file name in /boot. The -f suffix kind of scares me.

OTOH I'm thinking that I should just wipe this, perform a fresh install, and then restore my backed up data. I just used this install to test the upgrade/reinstall via live DVD several months ago as part of iso testing and kept it because it had been working acceptably.

What would rm -r do combined with wild cards, eg; rm -r *3.13.0-20* ?

I guess since I don't care about blowing it up this would be a good time to experiment :twisted:

---

### Post by Bashing-om on 2014-08-30
kansasnoob; Hey !
> 
This should be a fun ride for anyone up to the challenge.

I wanna play !
There is this to consider:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command Where the The state is 'rc', the package is removed, but the config files are not removed.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

``` To help clear away some cruft so we can see a tree or so through that forest .

Yeah, I like reading through config files, and identifying where they originated, and what they control. One of these days I may even learn to "read the source" , Luke.

[INDENT][INDENT]a constant process of learning
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2014-08-31
> **kansasnoob said:**
> What would rm -r do combined with wild cards, eg; rm -r *3.13.0-20* ?

The -r switch tells rm to recurse down the directory tree.  That doesn't apply to these files.  They are all stored in /boot itself.  Otherwise rm would delete any files matching the glob in subdirectories as well.

Using "rm -f *3.13.0-20*" will delete only the files associated with that kernel version.  So you can start with the oldest kernel and delete each group one at a time.  If you don't use "-f" then you will be asked to confirm the removal of each individual file.  Maybe you should start with that.

You can use more complex globs as well.  For instance
```
rm -f *3.13.0-2[0-8]*
```
will delete kernels with versions -20 through -28, but not -29 or -30.

---

### Post by kansasnoob on 2014-08-31
> **SeijiSensei said:**
> The -r switch tells rm to recurse down the directory tree.  That doesn't apply to these files.  They are all stored in /boot itself.  Otherwise rm would delete any files matching the glob in subdirectories as well.

Using "rm -f *3.13.0-20*" will delete only the files associated with that kernel version.  So you can start with the oldest kernel and delete each group one at a time.  If you don't use "-f" then you will be asked to confirm the removal of each individual file.  Maybe you should start with that.

You can use more complex globs as well.  For instance
```
rm -f *3.13.0-2[0-8]*
```
will delete kernels with versions -20 through -28, but not -29 or -30.

Thanks for the detailed explanation.

---

### Post by kansasnoob on 2014-08-31
> **Bashing-om said:**
> kansasnoob; Hey !

I wanna play !
There is this to consider:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command Where the The state is 'rc', the package is removed, but the config files are not removed.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

``` To help clear away some cruft so we can see a tree or so through that forest .

Yeah, I like reading through config files, and identifying where they originated, and what they control. One of these days I may even learn to "read the source" , Luke.

[INDENT][INDENT]a constant process of learning
[/INDENT][/INDENT]

That seems risky ................ or is it?

I might be inclined to try it though. When I did that "reinstall' using the automated logic of the installer I also went from Ubuntu GNOME to Ubuntu. I did notice that some configuration such as fonts was goofy as compared to an actual fresh install.

Is there a way of running that in a "print-only" or "simulate" mode so you can see what it's going to do before you commit to it?

---

### Post by ian-weisser on 2014-09-01
Yes. Add a --simulate flag to the list of arguments.

Was this, by chance, LVM/encrypted? Or have you discovered an all-new bug?

---

### Post by kansasnoob on 2014-09-02
> **ian-weisser said:**
> Yes. Add a --simulate flag to the list of arguments.

Was this, by chance, LVM/encrypted? Or have you discovered an all-new bug?

It's not LVM or encrypted. Just really straight-forward / simple as it gets:

[ATTACH=CONFIG]256070[/ATTACH]

As far as it being a bug ...................... clear back around Maverick they added the upgrade option to ubiquity, internally referred to as *reuse*, and it will also offer the option to replace the same version while retaining docs, pics, etc. But quite honestly, at this point, the only safe option offered by ubiquity is Something else - why didn't they just call it Advanced partitioning???

IMHO they need to try and patch the installer temporarily to at least reduce the instances of lost data and operating systems (Mint's patch seems reasonable) and then go back to the drawing board and start from scratch using the pre-Maverick installer as a starting point.

---

### Post by ian-weisser on 2014-09-02
Sounds like a good Ubuntu Online Summit discussion.

---

### Post by kansasnoob on 2014-09-10
> **SeijiSensei said:**
> I'm not sure what you're asking.  Do you want to remove the stale kernels and associated files from /boot?  You can do that as root just using rm:
```

# cd /boot
# rm -f *3.13.0-20*

```
That removes the files associated with the 3.13.0-20 kernel version.  Just don't delete the ones currently being used during boot, usually the most recent and the next most recent versions.  I've done this a number of times when kernels were not being removed automatically.  I think if there are stale kernels older than the preceding version, they are not marked for autoremove.  Once you reduce the list of kernels to just the current and previous versions, autoremove appears to sync up correctly in later updates.

Just getting back to this after a gazillion and one distractions ;)

This actually looks good (after a couple of brain hiccups):

```
lance@lance-desktop:~$ ls /boot
abi-3.13.0-20-generic         initrd.img-3.13.0-34-generic
abi-3.13.0-21-generic         initrd.img-3.13.0-35-generic
abi-3.13.0-22-generic         memtest86+.bin
abi-3.13.0-23-generic         memtest86+.elf
abi-3.13.0-29-generic         memtest86+_multiboot.bin
abi-3.13.0-34-generic         System.map-3.13.0-20-generic
abi-3.13.0-35-generic         System.map-3.13.0-21-generic
config-3.13.0-20-generic      System.map-3.13.0-22-generic
config-3.13.0-21-generic      System.map-3.13.0-23-generic
config-3.13.0-22-generic      System.map-3.13.0-29-generic
config-3.13.0-23-generic      System.map-3.13.0-34-generic
config-3.13.0-29-generic      System.map-3.13.0-35-generic
config-3.13.0-34-generic      vmlinuz-3.13.0-20-generic
config-3.13.0-35-generic      vmlinuz-3.13.0-21-generic
grub                          vmlinuz-3.13.0-22-generic
initrd.img-3.13.0-20-generic  vmlinuz-3.13.0-23-generic
initrd.img-3.13.0-21-generic  vmlinuz-3.13.0-29-generic
initrd.img-3.13.0-22-generic  vmlinuz-3.13.0-34-generic
initrd.img-3.13.0-23-generic  vmlinuz-3.13.0-35-generic
initrd.img-3.13.0-29-generic
lance@lance-desktop:~$ cd /boot
lance@lance-desktop:/boot$ rm -f *3.13.0-20*
rm: cannot remove ‘abi-3.13.0-20-generic’: Permission denied
rm: cannot remove ‘config-3.13.0-20-generic’: Permission denied
rm: cannot remove ‘initrd.img-3.13.0-20-generic’: Permission denied
rm: cannot remove ‘System.map-3.13.0-20-generic’: Permission denied
rm: cannot remove ‘vmlinuz-3.13.0-20-generic’: Permission denied
lance@lance-desktop:/boot$ sudo rm -f *3.13.0-20*
[sudo] password for lance: 
lance@lance-desktop:/boot$ ls /boot
abi-3.13.0-21-generic         initrd.img-3.13.0-34-generic
abi-3.13.0-22-generic         initrd.img-3.13.0-35-generic
abi-3.13.0-23-generic         memtest86+.bin
abi-3.13.0-29-generic         memtest86+.elf
abi-3.13.0-34-generic         memtest86+_multiboot.bin
abi-3.13.0-35-generic         System.map-3.13.0-21-generic
config-3.13.0-21-generic      System.map-3.13.0-22-generic
config-3.13.0-22-generic      System.map-3.13.0-23-generic
config-3.13.0-23-generic      System.map-3.13.0-29-generic
config-3.13.0-29-generic      System.map-3.13.0-34-generic
config-3.13.0-34-generic      System.map-3.13.0-35-generic
config-3.13.0-35-generic      vmlinuz-3.13.0-21-generic
grub                          vmlinuz-3.13.0-22-generic
initrd.img-3.13.0-21-generic  vmlinuz-3.13.0-23-generic
initrd.img-3.13.0-22-generic  vmlinuz-3.13.0-29-generic
initrd.img-3.13.0-23-generic  vmlinuz-3.13.0-34-generic
initrd.img-3.13.0-29-generic  vmlinuz-3.13.0-35-generic

```

So that's one to keep in the toolbox for future reference, many thanks :D

---

### Post by kansasnoob on 2014-09-10
> **Bashing-om said:**
> kansasnoob; Hey !

I wanna play !
There is this to consider:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command Where the The state is 'rc', the package is removed, but the config files are not removed.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

``` To help clear away some cruft so we can see a tree or so through that forest .

Yeah, I like reading through config files, and identifying where they originated, and what they control. One of these days I may even learn to "read the source" , Luke.

[INDENT][INDENT]a constant process of learning
[/INDENT][/INDENT]

This also looks OK so I'm gonna go for it:

```
lance@lance-desktop:~$ dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge --simulate
[sudo] password for lance: 
(Reading database ... 269880 files and directories currently installed.)
Would remove or purge libavcodec54:i386 (6:9.13-0ubuntu0.14.04.1) ...
Would remove or purge linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Would remove or purge linux-image-3.13.0-30-generic (3.13.0-30.55) ...
Would remove or purge linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Would remove or purge linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Would remove or purge linux-image-extra-3.13.0-30-generic (3.13.0-30.55) ...
Would remove or purge linux-image-extra-3.13.0-32-generic (3.13.0-32.57) ...
lance@lance-desktop:~$ ls /boot
abi-3.13.0-21-generic         initrd.img-3.13.0-34-generic
abi-3.13.0-22-generic         initrd.img-3.13.0-35-generic
abi-3.13.0-23-generic         memtest86+.bin
abi-3.13.0-29-generic         memtest86+.elf
abi-3.13.0-34-generic         memtest86+_multiboot.bin
abi-3.13.0-35-generic         System.map-3.13.0-21-generic
config-3.13.0-21-generic      System.map-3.13.0-22-generic
config-3.13.0-22-generic      System.map-3.13.0-23-generic
config-3.13.0-23-generic      System.map-3.13.0-29-generic
config-3.13.0-29-generic      System.map-3.13.0-34-generic
config-3.13.0-34-generic      System.map-3.13.0-35-generic
config-3.13.0-35-generic      vmlinuz-3.13.0-21-generic
grub                          vmlinuz-3.13.0-22-generic
initrd.img-3.13.0-21-generic  vmlinuz-3.13.0-23-generic
initrd.img-3.13.0-22-generic  vmlinuz-3.13.0-29-generic
initrd.img-3.13.0-23-generic  vmlinuz-3.13.0-34-generic
initrd.img-3.13.0-29-generic  vmlinuz-3.13.0-35-generic

```

I'll investigate 'libavcodec54' after the purge ;)

---

### Post by kansasnoob on 2014-09-10
Still need to manually clean up /boot:

```
lance@lance-desktop:~$ dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
(Reading database ... 269880 files and directories currently installed.)
Removing libavcodec54:i386 (6:9.13-0ubuntu0.14.04.1) ...
Purging configuration files for libavcodec54:i386 (6:9.13-0ubuntu0.14.04.1) ...
Removing linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Purging configuration files for linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Removing linux-image-3.13.0-30-generic (3.13.0-30.55) ...
Purging configuration files for linux-image-3.13.0-30-generic (3.13.0-30.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Removing linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Purging configuration files for linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Removing linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Purging configuration files for linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Removing linux-image-extra-3.13.0-30-generic (3.13.0-30.55) ...
Purging configuration files for linux-image-extra-3.13.0-30-generic (3.13.0-30.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Removing linux-image-extra-3.13.0-32-generic (3.13.0-32.57) ...
Purging configuration files for linux-image-extra-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
lance@lance-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lance@lance-desktop:~$ ls /boot
abi-3.13.0-21-generic         initrd.img-3.13.0-34-generic
abi-3.13.0-22-generic         initrd.img-3.13.0-35-generic
abi-3.13.0-23-generic         memtest86+.bin
abi-3.13.0-29-generic         memtest86+.elf
abi-3.13.0-34-generic         memtest86+_multiboot.bin
abi-3.13.0-35-generic         System.map-3.13.0-21-generic
config-3.13.0-21-generic      System.map-3.13.0-22-generic
config-3.13.0-22-generic      System.map-3.13.0-23-generic
config-3.13.0-23-generic      System.map-3.13.0-29-generic
config-3.13.0-29-generic      System.map-3.13.0-34-generic
config-3.13.0-34-generic      System.map-3.13.0-35-generic
config-3.13.0-35-generic      vmlinuz-3.13.0-21-generic
grub                          vmlinuz-3.13.0-22-generic
initrd.img-3.13.0-21-generic  vmlinuz-3.13.0-23-generic
initrd.img-3.13.0-22-generic  vmlinuz-3.13.0-29-generic
initrd.img-3.13.0-23-generic  vmlinuz-3.13.0-34-generic
initrd.img-3.13.0-29-generic  vmlinuz-3.13.0-35-generic

```

---

### Post by kansasnoob on 2014-09-10
I must be doing something wrong here:

```
lance@lance-desktop:~$ sudo rm -f *3.13.0-21*
lance@lance-desktop:~$ ls /boot
abi-3.13.0-21-generic         initrd.img-3.13.0-34-generic
abi-3.13.0-22-generic         initrd.img-3.13.0-35-generic
abi-3.13.0-23-generic         memtest86+.bin
abi-3.13.0-29-generic         memtest86+.elf
abi-3.13.0-34-generic         memtest86+_multiboot.bin
abi-3.13.0-35-generic         System.map-3.13.0-21-generic
config-3.13.0-21-generic      System.map-3.13.0-22-generic
config-3.13.0-22-generic      System.map-3.13.0-23-generic
config-3.13.0-23-generic      System.map-3.13.0-29-generic
config-3.13.0-29-generic      System.map-3.13.0-34-generic
config-3.13.0-34-generic      System.map-3.13.0-35-generic
config-3.13.0-35-generic      vmlinuz-3.13.0-21-generic
grub                          vmlinuz-3.13.0-22-generic
initrd.img-3.13.0-21-generic  vmlinuz-3.13.0-23-generic
initrd.img-3.13.0-22-generic  vmlinuz-3.13.0-29-generic
initrd.img-3.13.0-23-generic  vmlinuz-3.13.0-34-generic
initrd.img-3.13.0-29-generic  vmlinuz-3.13.0-35-generic

```

Worked well with *3.13.0-20* but not *3.13.0-21* :confused:

EDIT: Duh ................ I forgot to cd /boot :oops:

---

### Post by kansasnoob on 2014-09-10
Figured something simple like this; 'libavcodec54' was just replaced by 'libavcodec-extra-54' probably as part of the extras mega-package.

Otherwise I seem to have a clean working OS:

```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin

```

So I have two new tools in my toolkit :guitar:

Many, many thanks :D

---

### Post by kansasnoob on 2014-09-10
> **ian-weisser said:**
> Sounds like a good Ubuntu Online Summit discussion.

Over the next week or so, as time allows, I'll pull up some old notes and likely post about my previous battles with the [installer team]("https://launchpad.net/~ubuntu-installer") here:

[http://ubuntuforums.org/showthread.php?t=2237479](http://ubuntuforums.org/showthread.php?t=2237479)

I can tell you that the installer team is no doubt among the most insular I've found in the Ubuntu community, can't say it much better than [Merriam-Webster]("http://www.merriam-webster.com/dictionary/insular"):

> separated from other people or cultures : not knowing or interested in new or different ideas

Actually in this case I suppose it would be better to say they think they're smarter than everyone else, which is undoubtedly true on a technical level, so they refuse to listen to input from the average user. I can't find the old bug report but at one time many cycles back the option that is now called Something else actually said something to the effect, "so you think you're smarter than us". It's hard to find closed bug reports but I'll try.

EDIT: Just to put a wee bit of perspective on my previous battles with the installer team here's a couple of slightly oldish forum links:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

[http://ubuntuforums.org/showthread.php?t=1717793](http://ubuntuforums.org/showthread.php?t=1717793)

And archived from Ayatana:

[http://www.mail-archive.com/ayatana@lists.launchpad.net/msg04586.html](http://www.mail-archive.com/ayatana@lists.launchpad.net/msg04586.html)

I have battle scars :frown:

---

