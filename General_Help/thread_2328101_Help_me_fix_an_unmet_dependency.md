---
title: "Help me fix an unmet dependency"
date: 2016-06-17
forum: General Help
---

### Post by Andrew_Fischer on 2016-06-17
Hello,

I am running Ubuntu 14.04 LTS   server  on a Dell Server  and have  a problem with an unmet dependency. 



```
[FONT=Menlo]elli:~$ sudo apt-get update
[/FONT](...)
[FONT=Menlo]Fetched 5,303 kB in 4s (1,142 kB/s)[/FONT]
[FONT=Menlo]Reading package lists... Done
[/FONT][FONT=Menlo]
$ sudo apt-get dist-upgrade[/FONT]
[FONT=Menlo]Reading package lists... Done[/FONT]
[FONT=Menlo]Building dependency tree       [/FONT]
[FONT=Menlo]Reading state information... Done[/FONT]
[FONT=Menlo]You might want to run ‘apt-get -f install’ to correct these.[/FONT]
[FONT=Menlo]The following packages have unmet dependencies.[/FONT]
[FONT=Menlo] srvadmin-isvc : Depends: srvadmin-hapi (>= 8.3.0) but 7.4.0-1 is installed[/FONT]
[FONT=Menlo]E: Unmet dependencies. Try using -f.
[/FONT]
[FONT=Menlo]$sudo apt-get -f install
[/FONT][FONT=Menlo]
[/FONT]
[FONT=Menlo]Reading package lists... Done[/FONT]
[FONT=Menlo]Building dependency tree       [/FONT]
[FONT=Menlo]Reading state information... Done[/FONT]
[FONT=Menlo]Correcting dependencies... Done[/FONT]
[FONT=Menlo]The following packages were automatically installed and are no longer required:[/FONT]
[FONT=Menlo]  linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic[/FONT]
[FONT=Menlo]  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic[/FONT]
[FONT=Menlo]  linux-headers-3.13.0-77 linux-headers-3.13.0-77-generic[/FONT]
[FONT=Menlo]  linux-image-3.13.0-74-generic linux-image-3.13.0-76-generic[/FONT]
[FONT=Menlo]  linux-image-3.13.0-77-generic linux-image-3.13.0-87-generic[/FONT]
[FONT=Menlo]  linux-image-extra-3.13.0-74-generic linux-image-extra-3.13.0-76-generic[/FONT]
[FONT=Menlo]  linux-image-extra-3.13.0-77-generic[/FONT]
[FONT=Menlo]Use 'apt-get autoremove' to remove them.[/FONT]
[FONT=Menlo]The following extra packages will be installed:[/FONT]
[FONT=Menlo]  srvadmin-hapi[/FONT]
[FONT=Menlo]The following packages will be upgraded:[/FONT]
[FONT=Menlo]  srvadmin-hapi[/FONT]
[FONT=Menlo]1 to upgrade, 0 to newly install, 0 to remove and 43 not to upgrade.[/FONT]
[FONT=Menlo]42 not fully installed or removed.[/FONT]
[FONT=Menlo]Need to get 0 B/300 kB of archives.[/FONT]
[FONT=Menlo]After this operation, 329 kB disk space will be freed.[/FONT]
[FONT=Menlo]Do you want to continue? [Y/n] Y[/FONT]
[FONT=Menlo](Reading database ... 197747 files and directories currently installed.)[/FONT]
[FONT=Menlo]Preparing to unpack .../srvadmin-hapi_8.3.0-1_amd64.deb ...[/FONT]
[FONT=Menlo]dpkg: error processing archive /var/cache/apt/archives/srvadmin-hapi_8.3.0-1_amd64.deb (--unpack):[/FONT]
[FONT=Menlo] subprocess new pre-installation script returned error exit status 127[/FONT]
[FONT=Menlo]Stopping Systems Management Device Drivers:[/FONT]
[FONT=Menlo]Stopping dell_rbu: * [/FONT]
[FONT=Menlo]Starting Systems Management Device Drivers:[/FONT]
[FONT=Menlo]Starting dell_rbu: * [/FONT]
[FONT=Menlo]Starting ipmi driver:  * Already started[/FONT]
[FONT=Menlo]Processing triggers for libc-bin (2.19-0ubuntu6.9) ...[/FONT]
[FONT=Menlo]Errors were encountered while processing:[/FONT]
[FONT=Menlo] /var/cache/apt/archives/srvadmin-hapi_8.3.0-1_amd64.deb[/FONT]
[FONT=Menlo]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]


[FONT=Menlo]


[/FONT]

```


[B]apt-get -f install does not fix the problem.  What can I do?? 
[/B]


srvadmin-hapi  is Dell OpenManage Server Administrator.    I don't absolutely have to have it. I only look after three servers and only one is on Dell Hardware.

---

### Post by Bashing-om on 2016-06-17
Andrew_Fischer; Hello;

I will kick this off .
I do not find "srvadmin-hapi" in the 14.04 software repository:
```

sysop@1404mini:~$ apt search srvadmin-hapi
Sorting... Done
Full Text Search... Done
sysop@1404mini:~$

```

Let's see if we can find where it comes from:
```

apt-cache policy srvadmin-hapi

```

And refocus our attention.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by Andrew_Fischer on 2016-06-18
Thanks!  I will have to wait until Monday.     IT is doing a major upgrade this weekend and we have no network connections. 

.  I think OpenManage is from Dell. I'll chase it down and reply here early next week.

---

### Post by CantankRus on 2016-06-18
Answer from Dell...
[http://permalink.gmane.org/gmane.linux.hardware.dell.poweredge/46666](http://permalink.gmane.org/gmane.linux.hardware.dell.poweredge/46666)

---

### Post by Andrew_Fischer on 2016-06-20
[FONT=Menlo]srvadmin-hapi:[/FONT]
[FONT=Menlo]  Installed: 7.4.0-1[/FONT]
[FONT=Menlo]  Candidate: 8.3.0-1[/FONT]
[FONT=Menlo]  Version table:[/FONT]
[FONT=Menlo]     8.3.0-1 0[/FONT]
[FONT=Menlo]        500 [http://linux.dell.com/repo/community/ubuntu/](http://linux.dell.com/repo/community/ubuntu/) trusty/openmanage amd64 Packages[/FONT]
[FONT=Menlo] *** 7.4.0-1 0[/FONT]
[FONT=Menlo]        500 [http://linux.dell.com/repo/community/ubuntu/](http://linux.dell.com/repo/community/ubuntu/) trusty/openmanage amd64 Packages[/FONT]
[FONT=Menlo]        100 /var/lib/dpkg/status[/FONT]

> **CantankRus said:**
> Answer from Dell...
[http://permalink.gmane.org/gmane.linux.hardware.dell.poweredge/46666](http://permalink.gmane.org/gmane.linux.hardware.dell.poweredge/46666)


ahh   we don't want to  install 8.3 on top of  7.4.        Time to learn how to fix this.

For anyone else chasing down this problem -- 

ignore -- still working on it.

---

### Post by Andrew_Fischer on 2016-06-20
I just made things a lot worse   < ugh >

I edited /etc/apt/sources.list.d/linux.del.com/sources.list    and changed the  line to 

deb [http://linux.dell.com/repo/community/ubuntu](http://linux.dell.com/repo/community/ubuntu) trusty openmanage/740


Then I ran  apt-get update    It hit open manage/740   so far so good.



```

[FONT=Menlo]sudo apt-get dist-upgrade[/FONT]

[FONT=Menlo]Reading package lists... Done[/FONT]

[FONT=Menlo]Building dependency tree       [/FONT]

[FONT=Menlo]Reading state information... Done[/FONT]

[FONT=Menlo]You might want to run ‘apt-get -f install’ to correct these.[/FONT]

[FONT=Menlo]The following packages have unmet dependencies.[/FONT]

[FONT=Menlo] srvadmin-isvc : Depends: srvadmin-hapi (>= 8.3.0) but 7.4.0-1 is installed[/FONT]

[FONT=Menlo]E: Unmet dependencies. Try using -f.[/FONT]


```




```


[FONT=Menlo]sudo apt-get -f install[/FONT]
[FONT=Menlo]Reading package lists... Done[/FONT]
[FONT=Menlo]Building dependency tree       [/FONT]
[FONT=Menlo]Reading state information... Done[/FONT]
[FONT=Menlo]Correcting dependencies... Done[/FONT]
[FONT=Menlo]The following packages were automatically installed and are no longer required:[/FONT]
[FONT=Menlo]  icedtea-netx icedtea-netx-common libargtable2-0 libopenipmi0 libperl5.18[/FONT]
[FONT=Menlo]  libsmbios2 libsnmp-base libsnmp30 libsysfs2 libxslt1.1[/FONT]
[FONT=Menlo]  linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic[/FONT]
[FONT=Menlo]  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic[/FONT]
[FONT=Menlo]  linux-headers-3.13.0-77 linux-headers-3.13.0-77-generic[/FONT]
[FONT=Menlo]  linux-image-3.13.0-74-generic linux-image-3.13.0-76-generic[/FONT]
[FONT=Menlo]  linux-image-3.13.0-77-generic linux-image-3.13.0-87-generic[/FONT]
[FONT=Menlo]  linux-image-extra-3.13.0-74-generic linux-image-extra-3.13.0-76-generic[/FONT]
[FONT=Menlo]  linux-image-extra-3.13.0-77-generic openipmi python-libsmbios setserial[/FONT]
[FONT=Menlo]  smbios-utils srvadmin-deng srvadmin-deng-snmp srvadmin-hapi[/FONT]
[FONT=Menlo]  srvadmin-idrac-ivmcli srvadmin-idrac-snmp srvadmin-idrac-vmcli[/FONT]
[FONT=Menlo]  srvadmin-idracadm srvadmin-idracadm7 srvadmin-jre srvadmin-nvme[/FONT]
[FONT=Menlo]  srvadmin-omacs srvadmin-omcommon srvadmin-omilcore srvadmin-oslog[/FONT]
[FONT=Menlo]  srvadmin-rac-components srvadmin-rac4 srvadmin-rac4-populator[/FONT]
[FONT=Menlo]  srvadmin-racadm4 srvadmin-racadm5 srvadmin-racdrsc srvadmin-racsvc[/FONT]
[FONT=Menlo]  srvadmin-realssd srvadmin-rnasoap srvadmin-smcommon srvadmin-smweb[/FONT]
[FONT=Menlo]  srvadmin-standardagent srvadmin-storelib srvadmin-storelib-sysfs[/FONT]
[FONT=Menlo]  srvadmin-tomcat srvadmin-webserver srvadmin-xmlsup[/FONT]
[FONT=Menlo]Use 'apt-get autoremove' to remove them.[/FONT]
[FONT=Menlo]The following packages will be REMOVED[/FONT]
[FONT=Menlo]  srvadmin-all srvadmin-base srvadmin-idrac srvadmin-idrac7 srvadmin-isvc[/FONT]
[FONT=Menlo]  srvadmin-isvc-snmp srvadmin-omacore srvadmin-ominst srvadmin-rac5[/FONT]
[FONT=Menlo]  srvadmin-server-cli srvadmin-server-snmp srvadmin-storage[/FONT]
[FONT=Menlo]  srvadmin-storage-cli srvadmin-storage-snmp srvadmin-storageservices[/FONT]
[FONT=Menlo]  srvadmin-storageservices-cli srvadmin-storageservices-snmp[/FONT]
[FONT=Menlo]0 to upgrade, 0 to newly install, 17 to remove and 19 not to upgrade.[/FONT]
[FONT=Menlo]42 not fully installed or removed.[/FONT]
[FONT=Menlo]After this operation, 16.5 MB disk space will be freed.[/FONT]
[FONT=Menlo]Do you want to continue? [Y/n] Y[/FONT]
[FONT=Menlo](Reading database ... 197744 files and directories currently installed.)[/FONT]
[FONT=Menlo]Removing srvadmin-all (7.4.0) ...[/FONT]
[FONT=Menlo]Removing srvadmin-idrac (7.4.0-1) ...[/FONT]
[FONT=Menlo]Removing srvadmin-storageservices (7.4.0) ...[/FONT]
[FONT=Menlo]Removing srvadmin-storageservices-snmp (7.4.0) ...[/FONT]
[FONT=Menlo]Removing srvadmin-isvc-snmp (7.4.0-1) ...[/FONT]
[FONT=Menlo]Removing srvadmin-server-cli (7.4.0) ...[/FONT]
[FONT=Menlo]Removing srvadmin-server-snmp (7.4.0) ...[/FONT]
[FONT=Menlo]Removing srvadmin-base (7.4.0) ...[/FONT]
[FONT=Menlo]Removing srvadmin-idrac7 (7.4.0-1) ...[/FONT]
[FONT=Menlo]Removing srvadmin-storageservices-cli (7.4.0) ...[/FONT]
[FONT=Menlo]Removing srvadmin-storage-cli (7.4.0-1) ...[/FONT]
[FONT=Menlo]Removing srvadmin-omacore (7.4.0-1) ...[/FONT]
[FONT=Menlo]/opt/dell/srvadmin/lib/srvadmin-omacore/cli_ini_modifier.sh: line 33: /opt/dell/srvadmin/lib/srvadmin-omilcore/Funcs.sh: No such file or directory[/FONT]
[FONT=Menlo]/opt/dell/srvadmin/lib/srvadmin-omacore/unregister-omacore.sh: line 3: /opt/dell/srvadmin/lib/srvadmin-omilcore/Funcs.sh: No such file or directory[/FONT]
[FONT=Menlo]/opt/dell/srvadmin/lib/srvadmin-omacore/unregister-omacore.sh: line 4: GetRegVal: command not found[/FONT]
[FONT=Menlo]Removing srvadmin-ominst (7.4.0-1) ...[/FONT]
[FONT=Menlo]Removing srvadmin-rac5 (7.4.0-1) ...[/FONT]
[FONT=Menlo]Removing srvadmin-storage-snmp (7.4.0-1) ...[/FONT]
[FONT=Menlo]Removing srvadmin-storage (7.4.0-1) ...[/FONT]
[FONT=Menlo]Removing srvadmin-isvc (8.3.0-1) ...[/FONT]
[FONT=Menlo]/var/lib/dpkg/info/srvadmin-isvc.postrm: 15: /var/lib/dpkg/info/srvadmin-isvc.postrm: cannot create /opt/dell/srvadmin/etc/omreg.cfg: Directory nonexistent[/FONT]
[FONT=Menlo]Processing triggers for libc-bin (2.19-0ubuntu6.9) ...[/FONT]
[FONT=Menlo]Setting up libapt-inst1.5:amd64 (1.0.1ubuntu2.14) ...[/FONT]
[FONT=Menlo]Setting up libexpat1:amd64 (2.1.0-4ubuntu1.2) ...[/FONT]
[FONT=Menlo]Setting up libssl1.0.0:amd64 (1.0.1f-1ubuntu2.19) ...[/FONT]
[FONT=Menlo]Setting up libtasn1-6:amd64 (3.4-3ubuntu0.4) ...[/FONT]
[FONT=Menlo]Setting up bash-completion (1:2.1-4ubuntu0.2) ...[/FONT]
[FONT=Menlo]Setting up libxml2:amd64 (2.9.1+dfsg1-3ubuntu4.8) ...[/FONT]
[FONT=Menlo]Setting up libasan0:amd64 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up libatomic1:amd64 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up libgd3:amd64 (2.1.0-3ubuntu0.1) ...[/FONT]
[FONT=Menlo]Setting up libgomp1:amd64 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up libitm1:amd64 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up liblcms2-2:amd64 (2.5-0ubuntu4.1) ...[/FONT]
[FONT=Menlo]Setting up libnl-3-200:amd64 (3.2.21-1ubuntu3) ...[/FONT]
[FONT=Menlo]Setting up libnl-genl-3-200:amd64 (3.2.21-1ubuntu3) ...[/FONT]
[FONT=Menlo]Setting up libquadmath0:amd64 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up libtsan0:amd64 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up linux-image-3.13.0-87-generic (3.13.0-87.133) ...[/FONT]
[FONT=Menlo]Running depmod.[/FONT]
[FONT=Menlo]update-initramfs: deferring update (hook will be called later)[/FONT]
[FONT=Menlo]Examining /etc/kernel/postinst.d.[/FONT]
[FONT=Menlo]run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-87-generic /boot/vmlinuz-3.13.0-87-generic[/FONT]
[FONT=Menlo]run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-87-generic /boot/vmlinuz-3.13.0-87-generic[/FONT]
[FONT=Menlo]update-initramfs: Generating /boot/initrd.img-3.13.0-87-generic[/FONT]
[FONT=Menlo]run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-87-generic /boot/vmlinuz-3.13.0-87-generic[/FONT]
[FONT=Menlo]run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-87-generic /boot/vmlinuz-3.13.0-87-generic[/FONT]
[FONT=Menlo]Generating grub configuration file ...[/FONT]
[FONT=Menlo]Found linux image: /boot/vmlinuz-3.13.0-87-generic[/FONT]
[FONT=Menlo]Found initrd image: /boot/initrd.img-3.13.0-87-generic[/FONT]
[FONT=Menlo]Found linux image: /boot/vmlinuz-3.13.0-85-generic[/FONT]
[FONT=Menlo]Found initrd image: /boot/initrd.img-3.13.0-85-generic[/FONT]
[FONT=Menlo]Found linux image: /boot/vmlinuz-3.13.0-79-generic[/FONT]
[FONT=Menlo]Found initrd image: /boot/initrd.img-3.13.0-79-generic[/FONT]
[FONT=Menlo]Found linux image: /boot/vmlinuz-3.13.0-77-generic[/FONT]
[FONT=Menlo]Found initrd image: /boot/initrd.img-3.13.0-77-generic[/FONT]
[FONT=Menlo]Found linux image: /boot/vmlinuz-3.13.0-76-generic[/FONT]
[FONT=Menlo]Found initrd image: /boot/initrd.img-3.13.0-76-generic[/FONT]
[FONT=Menlo]Found linux image: /boot/vmlinuz-3.13.0-74-generic[/FONT]
[FONT=Menlo]Found initrd image: /boot/initrd.img-3.13.0-74-generic[/FONT]
[FONT=Menlo]Found memtest86+ image: /boot/memtest86+.elf[/FONT]
[FONT=Menlo]Found memtest86+ image: /boot/memtest86+.bin[/FONT]
[FONT=Menlo]done[/FONT]
[FONT=Menlo]Setting up openjdk-7-jre-headless:amd64 (7u101-2.6.6-0ubuntu0.14.04.1) ...[/FONT]
[FONT=Menlo]Installing new version of config file /etc/java-7-openjdk/management/management.properties ...[/FONT]
[FONT=Menlo]Setting up srvadmin-storelib-sysfs (8.3.0) ...[/FONT]
[FONT=Menlo]update-alternatives: using /lib/x86_64-linux-gnu/libsysfs.so.2 to provide /opt/lsi/3rdpartylibs/x86_64/libsysfs.so (srvadmin-storelib-sysfs) in auto mode[/FONT]
[FONT=Menlo]update-alternatives: warning: not replacing /opt/lsi/3rdpartylibs/x86_64/libsysfs.so with a link[/FONT]
[FONT=Menlo]Setting up libc-dev-bin (2.19-0ubuntu6.9) ...[/FONT]
[FONT=Menlo]Setting up linux-libc-dev:amd64 (3.13.0-87.133) ...[/FONT]
[FONT=Menlo]Setting up libc6-dev:amd64 (2.19-0ubuntu6.9) ...[/FONT]
[FONT=Menlo]Setting up binutils (2.24-5ubuntu14.1) ...[/FONT]
[FONT=Menlo]Setting up cpp-4.8 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up libgcc-4.8-dev:amd64 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up gcc-4.8 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up libstdc++-4.8-dev:amd64 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up g++-4.8 (4.8.4-2ubuntu1~14.04.3) ...[/FONT]
[FONT=Menlo]Setting up libexpat1-dev:amd64 (2.1.0-4ubuntu1.2) ...[/FONT]
[FONT=Menlo]Setting up libopenipmi0 (2.0.18-0ubuntu7.2) ...[/FONT]
[FONT=Menlo]Setting up openipmi (2.0.18-0ubuntu7.2) ...[/FONT]
[FONT=Menlo]Installing new version of config file /etc/init.d/openipmi ...[/FONT]
[FONT=Menlo]Setting up openjdk-7-jre:amd64 (7u101-2.6.6-0ubuntu0.14.04.1) ...[/FONT]
[FONT=Menlo]Setting up openjdk-7-jdk:amd64 (7u101-2.6.6-0ubuntu0.14.04.1) ...[/FONT]
[FONT=Menlo]Setting up srvadmin-omilcore (8.3.0) ...[/FONT]
[FONT=Menlo]/var/lib/dpkg/info/srvadmin-omilcore.postinst: 9: /var/lib/dpkg/info/srvadmin-omilcore.postinst: cannot create /opt/dell/srvadmin/etc/omreg.cfg: Directory nonexistent[/FONT]
[FONT=Menlo]     **********************************************************[/FONT]
[FONT=Menlo]     After the install process completes, you may need [/FONT]
[FONT=Menlo]     to log out and then log in again to reset the PATH[/FONT]
[FONT=Menlo]     variable to access the Dell OpenManage CLI utilities[/FONT]
[FONT=Menlo]     **********************************************************[/FONT]
[FONT=Menlo]Setting up srvadmin-deng (8.3.0-1) ...[/FONT]
[FONT=Menlo]Installing new version of config file /etc/ld.so.conf.d/srvadmin-deng.conf ...[/FONT]
[FONT=Menlo]cp: cannot create regular file ‘/opt/dell/srvadmin/etc/srvadmin-deng/ini/dcsndy64.ini’: No such file or directory[/FONT]
[FONT=Menlo]dpkg: error processing package srvadmin-deng (--configure):[/FONT]
[FONT=Menlo] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=Menlo]Setting up srvadmin-nvme (8.3.0) ...[/FONT]
[FONT=Menlo]Setting up srvadmin-omacs (8.3.0-2) ...[/FONT]
[FONT=Menlo]chmod: cannot access ‘/opt/dell/srvadmin/etc/openmanage/oma/ini/*.*’: No such file or directory[/FONT]
[FONT=Menlo]dpkg: error processing package srvadmin-omacs (--configure):[/FONT]
[FONT=Menlo] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=Menlo]Setting up srvadmin-smcommon (8.3.0) ...[/FONT]
[FONT=Menlo]Setting up srvadmin-storelib (8.3.0) ...[/FONT]
[FONT=Menlo]Setting up srvadmin-xmlsup (8.3.0-1) ...[/FONT]
[FONT=Menlo]Setting up icedtea-7-jre-jamvm:amd64 (7u101-2.6.6-0ubuntu0.14.04.1) ...[/FONT]
[FONT=Menlo]Processing triggers for libc-bin (2.19-0ubuntu6.9) ...[/FONT]
[FONT=Menlo]Processing triggers for ureadahead (0.100.0-16) ...[/FONT]
[FONT=Menlo]ureadahead will be reprofiled on next reboot[/FONT]
[FONT=Menlo]Errors were encountered while processing:[/FONT]
[FONT=Menlo] srvadmin-deng[/FONT]
[FONT=Menlo] srvadmin-omacs[/FONT]
[FONT=Menlo]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]
[FONT=Menlo]andrewfischer@elli:/etc/apt/sources.list.d$ sudo shutdown -r now[/FONT]

```



Leaving me a with a computer that can't find the   root drive.   


< sigh >     Time for   DVD boot.

---

