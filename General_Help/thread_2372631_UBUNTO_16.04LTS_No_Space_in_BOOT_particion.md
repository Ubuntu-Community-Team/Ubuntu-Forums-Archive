---
title: "UBUNTO 16.04LTS: No Space in BOOT particion"
date: 2017-09-27
forum: General Help
---

### Post by tony-rosmaninho on 2017-09-27
I have one Ubuntu PC without espace in Boot Particion.


I have a lot of Kernel version's, and i don't know how to remove it.

I Already try:

```
 sudo apt autoremove
```
 
Result:
```
[COLOR=#2C001E][FONT=Ubuntu]sudo apt autoremove[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Building dependency tree       [/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Reading state information... Done[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]You might want to run 'apt-get -f install' to correct these.[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]The following packages have unmet dependencies:[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] linux-image-extra-4.4.0-89-generic : Depends: linux-image-4.4.0-89-generic but it is not installed[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] linux-image-extra-4.4.0-93-generic : Depends: linux-image-4.4.0-93-generic but it is not installed[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] linux-image-extra-4.4.0-96-generic : Depends: linux-image-4.4.0-96-generic but it is not installed[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] linux-image-generic : Depends: linux-image-4.4.0-96-generic but it is not installed[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]E: Unmet dependencies. Try using -f.[/FONT][/COLOR]
```



```
 sudo apt autoremove -f
```

Result:

```
[COLOR=#2C001E][FONT=Ubuntu]udo apt autoremove -f[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Building dependency tree       [/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Reading state information... Done[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Correcting dependencies... Done[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]The following additional packages will be installed:[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]  linux-image-4.4.0-89-generic linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Suggested packages:[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]The following NEW packages will be installed:[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]  linux-image-4.4.0-89-generic linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]0 upgraded, 3 newly installed, 0 to remove and 242 not upgraded.[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]9 not fully installed or removed.[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Need to get 116 MB/138 MB of archives.[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]After this operation, 201 MB of additional disk space will be used.[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Do you want to continue? [Y/n] Y[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Get:1 http://pt.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-89-generic amd64 4.4.0-89.112 [21,9 MB][/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Get:2 http://pt.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-89-generic amd64 4.4.0-89.112 [36,0 MB] [/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Get:3 http://pt.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-93-generic amd64 4.4.0-93.116 [21,9 MB]       [/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Get:4 http://pt.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-93-generic amd64 4.4.0-93.116 [35,9 MB] [/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Fetched 116 MB in 5min 2s (382 kB/s)                                                                                                [/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu](Reading database ... 551859 files and directories currently installed.)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Preparing to unpack .../linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb ...[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Examining /etc/kernel/preinst.d/[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Done.[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Unpacking linux-image-4.4.0-96-generic (4.4.0-96.119) ...[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb (--unpack):[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] cannot copy extracted data for './boot/vmlinuz-4.4.0-96-generic' to '/boot/vmlinuz-4.4.0-96-generic.dpkg-new': failed to write (No space left on device)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]No apport report written because the error message indicates a disk full error[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Examining /etc/kernel/postrm.d .[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]The link /initrd.img is a damaged link[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Removing symbolic link initrd.img [/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] you may need to re-run your boot loader[grub][/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Preparing to unpack .../linux-image-4.4.0-89-generic_4.4.0-89.112_amd64.deb ...[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Examining /etc/kernel/preinst.d/[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Done.[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Unpacking linux-image-4.4.0-89-generic (4.4.0-89.112) ...[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-89-generic_4.4.0-89.112_amd64.deb (--unpack):[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] cannot copy extracted data for './boot/vmlinuz-4.4.0-89-generic' to '/boot/vmlinuz-4.4.0-89-generic.dpkg-new': failed to write (No space left on device)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]No apport report written because the error message indicates a disk full error[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Examining /etc/kernel/postrm.d .[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Preparing to unpack .../linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb ...[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Examining /etc/kernel/preinst.d/[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Done.[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Unpacking linux-image-4.4.0-93-generic (4.4.0-93.116) ...[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb (--unpack):[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] cannot copy extracted data for './boot/System.map-4.4.0-93-generic' to '/boot/System.map-4.4.0-93-generic.dpkg-new': failed to write (No space left on device)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]No apport report written because the error message indicates a disk full error[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Examining /etc/kernel/postrm.d .[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] /var/cache/apt/archives/linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] /var/cache/apt/archives/linux-image-4.4.0-89-generic_4.4.0-89.112_amd64.deb[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] /var/cache/apt/archives/linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/COLOR]
```

I try to install Synaptic, but it was not possible

Can anyone Help

---

### Post by ajgreeny on 2017-09-27
Show us the output of command ```
dpkg -l linux-image* linux-headers*
``` which will list the current situation regarding installed and removed kernels, and we can then use dpkg to remove one  or two unneeded kernels, after which the autoremove command may work; it needs headroom to work successfully and without that headroom it will always fail.

---

### Post by tony-rosmaninho on 2017-09-27
> **ajgreeny said:**
> Show us the output of command ```
dpkg -l linux-image* linux-headers*
``` which will list the current situation regarding installed and removed kernels, and we can then use dpkg to remove one  or two unneeded kernels, after which the autoremove command may work; it needs headroom to work successfully and without that headroom it will always fail.

Result:

```
dpkg -l linux-image* linux-headers*Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.4.0-66.87  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-66.87  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-70.91  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-70.91  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-71.92  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-71.92  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-72.93  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-72.93  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-75.96  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-75.96  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-78.99  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-78.99  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-79.100 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-79.100 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-81.104 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-81.104 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-83.106 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-83.106 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-87.110 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-87.110 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-89.112 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-89.112 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-93.116 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-93.116 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-96.119 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-96.119 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0.96.101 amd64        Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
rc  linux-image-4. 4.4.0-31.50  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-34.53  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-36.55  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-38.57  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-42.62  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-45.66  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-47.68  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-51.72  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-53.74  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-57.78  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-59.80  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-62.83  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-63.84  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-64.85  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-66.87  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-70.91  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-71.92  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-72.93  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-75.96  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-78.99  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-79.100 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-81.104 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-83.106 amd64        Linux kernel image for version 4.
iF  linux-image-4. 4.4.0-87.110 amd64        Linux kernel image for version 4.
in  linux-image-4. <none>       amd64        (no description available)
in  linux-image-4. <none>       amd64        (no description available)
in  linux-image-4. <none>       amd64        (no description available)
rc  linux-image-ex 4.4.0-31.50  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-34.53  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-36.55  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-38.57  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-42.62  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-45.66  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-47.68  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-51.72  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-53.74  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-57.78  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-59.80  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-62.83  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-63.84  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-64.85  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-66.87  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-70.91  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-71.92  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-72.93  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-75.96  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-78.99  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-79.100 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-81.104 amd64        Linux kernel extra modules for ve
iF  linux-image-ex 4.4.0-83.106 amd64        Linux kernel extra modules for ve
iU  linux-image-ex 4.4.0-87.110 amd64        Linux kernel extra modules for ve
rH  linux-image-ex 4.4.0-89.112 amd64        Linux kernel extra modules for ve
rH  linux-image-ex 4.4.0-93.116 amd64        Linux kernel extra modules for ve
iU  linux-image-ex 4.4.0-96.119 amd64        Linux kernel extra modules for ve
iU  linux-image-ge 4.4.0.96.101 amd64        Generic Linux kernel image



```

---

### Post by tony-rosmaninho on 2017-09-27
I try autoremove, but no success again:

```
sudo apt autoremove[sudo] password for equipband: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-89-generic : Depends: linux-image-4.4.0-89-generic but it is not installed
 linux-image-extra-4.4.0-93-generic : Depends: linux-image-4.4.0-93-generic but it is not installed
 linux-image-extra-4.4.0-96-generic : Depends: linux-image-4.4.0-96-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-96-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

---

### Post by ian-weisser on 2017-09-27
Please show us the complete output of the following terminal commands:
```
df
df -i
uname -r
```

---

### Post by ajgreeny on 2017-09-27
You have already told us you have a separate /boot partition so I assumed, perhaps wrongly, that it was full and that was the reason for your problem.

The **df -h/df -i** commands suggested by Ian will probably confirm that, and the **uname -r** command will tell us which kernel version you are currently using so we do not try to remove that.

However, you have so many unneeded kernels that I think we can safely suggest some to remove as a start using command ```
sudo dpkg -P linux-image{,-extra}-4.4.0-{66,70,72,75}-generic
```
That may give us enough headroom for the autoremove command to now start working, though it looks as if you have some part installed kernel packages that may need sorting out before re-running autoremove with ```
sudo dpkg --configure -a
sudo apt install -f
```
I also note that you have even more linux-headers packages remaining which can quickly utilise all the inodes available and Ian's **df -i** command will tell us the situation about that.
Hopefully, once headroom is available the autoremove command will be able to remove all unwanted header packages as well.

Good luck!

---

### Post by tony-rosmaninho on 2017-09-27
> **ian-weisser said:**
> Please show us the complete output of the following terminal commands:
```
df
df -i
uname -r
```

```
 df -iFilesystem                    Inodes  IUsed    IFree IUse% Mounted on
udev                          246346    511   245835    1% /dev
tmpfs                         251580    742   250838    1% /run
/dev/mapper/ubuntu--vg-root 60882944 828703 60054241    2% /
tmpfs                         251580     10   251570    1% /dev/shm
tmpfs                         251580      6   251574    1% /run/lock
tmpfs                         251580     16   251564    1% /sys/fs/cgroup
/dev/mapper/pdc_jbgbcjibg1    124928    348   124580    1% /boot
tmpfs                         251580     32   251548    1% /run/user/1000



```


```
uname -r4.4.0-83-generic



```

I'm using 4.4.0-83 because 4.4.0-87 don't boot, i have to make a expert setup, and load a holder version

---

### Post by tony-rosmaninho on 2017-09-27
> **ajgreeny said:**
> You have already told us you have a separate /boot partition so I assumed, perhaps wrongly, that it was full and that was the reason for your problem.

The **df -h/df -i** commands suggested by Ian will probably confirm that, and the **uname -r** command will tell us which kernel version you are currently using so we do not try to remove that.

However, you have so many unneeded kernels that I think we can safely suggest some to remove as a start using command ```
sudo dpkg -P linux-image{,-extra}-4.4.0-{66,70,72,75}-generic
```
That may give us enough headroom for the autoremove command to now start working, though it looks as if you have some part installed kernel packages that may need sorting out before re-running autoremove with ```
sudo dpkg --configure -a
sudo apt install -f
```
I also note that you have even more linux-headers packages remaining which can quickly utilise all the inodes available and Ian's **df -i** command will tell us the situation about that.
Hopefully, once headroom is available the autoremove command will be able to remove all unwanted header packages as well.

Good luck!

I guess i already delete some hold kernels.... but stay with problems

```
udo dpkg -P linux-image{,-extra}-4.4.0-{66,70,72,75}-generic[sudo] password for equipband: 
(Reading database ... 551858 files and directories currently installed.)
Removing linux-image-extra-4.4.0-66-generic (4.4.0-66.87) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-66-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-66-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-70-generic (4.4.0-70.91) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-70-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-70-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-70-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-72-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-72-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-75-generic (4.4.0-75.96) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-75-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-75-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-75-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-66-generic (4.4.0-66.87) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-66-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-66-generic (4.4.0-66.87) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Removing linux-image-4.4.0-70-generic (4.4.0-70.91) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-70-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-70-generic (4.4.0-70.91) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
Removing linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Removing linux-image-4.4.0-75-generic (4.4.0-75.96) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-75-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-75-generic (4.4.0-75.96) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Errors were encountered while processing:
 linux-image-extra-4.4.0-66-generic
 linux-image-extra-4.4.0-70-generic
 linux-image-extra-4.4.0-72-generic
 linux-image-extra-4.4.0-75-generic
```


with this code ```
[COLOR=#000000][FONT=&quot]sudo dpkg --configure -a[/FONT][/COLOR]
``` 
I have this:

```
sudo dpkg --configure -adpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-96-generic; however:
  Package linux-image-4.4.0-96-generic is not installed.
 linux-image-generic depends on linux-image-extra-4.4.0-96-generic; however:
  Package linux-image-extra-4.4.0-96-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.96.101); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic
 linux-generic



```

---

### Post by tony-rosmaninho on 2017-09-27
I try:
```
 sudo apt install -f 
```

and i get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-image-4.4.0-89-generic linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-89-generic linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
0 upgraded, 3 newly installed, 0 to remove and 242 not upgraded.
5 not fully installed or removed.
Need to get 0 B/138 MB of archives.
After this operation, 201 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 529402 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Done.
Unpacking linux-image-4.4.0-96-generic (4.4.0-96.119) ...
Preparing to unpack .../linux-image-4.4.0-89-generic_4.4.0-89.112_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
Done.
Unpacking linux-image-4.4.0-89-generic (4.4.0-89.112) ...
Preparing to unpack .../linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
Done.
Unpacking linux-image-4.4.0-93-generic (4.4.0-93.116) ...
Setting up linux-image-4.4.0-96-generic (4.4.0-96.119) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-extra-4.4.0-96-generic (4.4.0-96.119) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (4.4.0.96.101) ...
Setting up linux-generic (4.4.0.96.101) ...
Setting up linux-image-4.4.0-89-generic (4.4.0-89.112) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
dpkg: error processing package linux-image-extra-4.4.0-89-generic (--configure):
 package linux-image-extra-4.4.0-89-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Setting up linux-image-4.4.0-93-generic (4.4.0-93.116) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-93-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found initrd image: /boot/initrd.img-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
dpkg: error processing package linux-image-extra-4.4.0-93-generic (--configure):
 package linux-image-extra-4.4.0-93-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Errors were encountered while processing:
 linux-image-extra-4.4.0-89-generic
 linux-image-extra-4.4.0-93-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
equipband@equipband-server:~$ 



```

---

### Post by tony-rosmaninho on 2017-09-28
thank's to all.....

Your help was essential to solve my problem....

---

### Post by ajgreeny on 2017-09-28
> **tony-rosmaninho said:**
> thank's to all.....

Your help was essential to solve my problem....
So please enlighten us; what was the eventual solution?

---

### Post by tony-rosmaninho on 2017-10-02
Hi,

Solved with this instrutions,
```
sudo dpkg -P linux-image{,-extra}-4.4.0-{66,70,72,75}-generic
```
 ```
sudo dpkg --configure -a
sudo apt install -f
```


thank's

---

### Post by digz6666 on 2018-01-30
Thanks, it helped me to solve my problem. My /boot partition got full and updates were not working, and now its fine :)

---

