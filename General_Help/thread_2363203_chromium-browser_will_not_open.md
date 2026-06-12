---
title: "chromium-browser will not open"
date: 2017-06-07
forum: General Help
---

### Post by valvegrid on 2017-06-07
After an update this morning Chromium refused to open from the launcher, so I tried from the command line and got this.

I'm using Ubuntu 14.04 32 bit

The laptop is working OK, that is running Ubuntu 16.04 MATE, if there's no resolution I'm just load 16.04 MATE on this machine instead.

```
paul@paul-zoostorm:~$ chromium-browser
Using PPAPI flash.
 --ppapi-flash-path=/usr/lib/adobe-flashplugin/libpepflashplayer.so --ppapi-flash-version=
Received signal 11 SEGV_MAPERR 000002f5df78
#0 0x0000b470c4b3 base::debug::StackTrace::StackTrace()
#1 0x0000b470bd77 base::debug::StackTrace::StackTrace()
#2 0x0000b470c8ce <unknown>
#3 0x0000b485a410 ([vdso]+0x40f)
#4 0x0000b58c599c <unknown>
#5 0x0000b58c6758 <unknown>
#6 0x0000b56024b8 <unknown>
#7 0x0000b55fac43 <unknown>
#8 0x0000b55fde02 <unknown>
#9 0x0000afdbd01c BrowserContextKeyedServiceFactory::BuildServiceInstanceFor()
#10 0x0000b0488436 KeyedServiceFactory::GetServiceForContext()
#11 0x0000b55fdee6 <unknown>
#12 0x0000b554aa8e <unknown>
#13 0x0000b554b388 <unknown>
#14 0x0000b60ddc1e <unknown>
#15 0x0000b5537076 <unknown>
#16 0x0000b56a3832 <unknown>
#17 0x0000b56a3d15 <unknown>
#18 0x0000b22776dc content::StoragePartitionImplMap::Get()
#19 0x0000b1f40619 <unknown>
#20 0x0000b1f40f57 content::BrowserContext::GetStoragePartition()
#21 0x0000b1f41177 content::BrowserContext::GetDefaultStoragePartition()
#22 0x0000b56a0e4e <unknown>
#23 0x0000b56a1734 <unknown>
#24 0x0000b56a1af1 <unknown>
#25 0x0000b56a2787 <unknown>
#26 0x0000b56a29fb <unknown>
#27 0x0000b553b7c3 <unknown>
#28 0x0000b5540bfd <unknown>
#29 0x0000b5540ecc <unknown>
#30 0x0000b612af30 <unknown>
#31 0x0000b5759298 <unknown>
#32 0x0000b575a1dc <unknown>
#33 0x0000b1f43e69 content::BrowserMainLoop::PreMainMessageLoopRun()
#34 0x0000b226f607 content::StartupTaskRunner::RunAllTasksNow()
#35 0x0000b1f454fe content::BrowserMainLoop::CreateStartupTasks()
#36 0x0000b1f4a533 <unknown>
#37 0x0000b1f43032 content::BrowserMain()
#38 0x0000b26266ee <unknown>
#39 0x0000ad5c0b4b service_manager::Main()
#40 0x0000b2625240 content::ContentMain()
#41 0x0000b50eb047 ChromeMain
#42 0x0000b50e961b <unknown>
#43 0x0000ad70caf3 __libc_start_main
#44 0x0000b50eae8e <unknown>
  gs: 00000033  fs: 00000000  es: 0000007b  ds: 0000007b
 edi: b9037cc4 esi: b9037b28 ebp: bf866ed8 esp: bf866da0
 ebx: b9037970 edx: 00000006 ecx: 00000026 eax: bf866ef0
 trp: 0000000e err: 00000004  ip: b58c599c  cs: 00000073
 efl: 00210286 usp: bf866da0  ss: 0000007b
[end of stack trace]
Calling _exit(1). Core file will not be generated.
paul@paul-zoostorm:~$ [3767:3767:0607/160632.535486:ERROR:broker_posix.cc(41)] Invalid node channel message
../../sandbox/linux/seccomp-bpf-helpers/sigsys_handlers.cc:**CRASHING**:seccomp-bpf failure in syscall 0221
Received signal 11 SEGV_MAPERR 0000006f80dd
#0 0x0000b47064b3 base::debug::StackTrace::StackTrace()
#1 0x0000b4705d77 base::debug::StackTrace::StackTrace()
#2 0x0000b47068ce <unknown>
#3 0x0000b4854410 ([vdso]+0x40f)
#4 0x0000ad5ccf65 sandbox::CrashSIGSYS_Handler()
#5 0x0000ad5d443a sandbox::Trap::SigSys()
#6 0x0000ad5d459c sandbox::Trap::SigSysAction()
#7 0x0000b4854410 ([vdso]+0x40f)
#8 0x0000b4854428 ([vdso]+0x427)
#9 0x0000ad7ca7e5 fcntl
#10 0x0000ad7ca973 lockf
#11 0x0000a7170953 <unknown>
#12 0x0000a7172498 <unknown>
#13 0x0000a717262c <unknown>
#14 0x0000a717283e <unknown>
#15 0x0000a71bcfdd <unknown>
#16 0x0000a71703ba <unknown>
#17 0x0000a713b4c2 <unknown>
#18 0x0000a827ec21 <unknown>
  gs: 00000033  fs: 00000000  es: 0000007b  ds: 0000007b
 edi: bfd603c0 esi: 000000dd ebp: bfd60357 esp: bfd60340
 ebx: 00000000 edx: 000f8000 ecx: 4029fe4c eax: 006f80dd
 trp: 0000000e err: 00000006  ip: ad5ccf65  cs: 00000073
 efl: 00210206 usp: bfd60340  ss: 0000007b
[end of stack trace]
Calling _exit(1). Core file will not be generated.



```

---

### Post by 0skillz on 2017-06-07
same issue here, i have a couple of terminal pastes, one from initially  trying to start chromium-browser, another after purging, autoremoving,  and installing again.

xubuntu 16.04 LTS 32 bit virtual machine.  I also have the same version  of xubuntu installed on a laptop that is not having the problem... yet?

```

Script started on Wed 07 Jun 2017 12:23:19 PM EDT
 ]0;shayla@shayla-vm: ~shayla@shayla-vm:~$ chromium-browser --enable-logging
 Received signal 11 SEGV_MAPERR 0000031d9a20
 #0 0x0000b7618ee3 base::debug::StackTrace::StackTrace()
 #1 0x0000b7618767 base::debug::StackTrace::StackTrace()
 #2 0x0000b76192fe <unknown>
 #3 0x0000b7763c20 ([vdso]+0xc1f)
 #4 0x0000811e8c1c <unknown>
 #5 0x0000811e99d8 <unknown>
 #6 0x000080ef12e8 <unknown>
 #7 0x000080ee95c3 <unknown>
 #8 0x000080eeca72 <unknown>
 #9 0x0000b2c0299c BrowserContextKeyedServiceFactory::BuildServiceInstanceFor()
 #10 0x0000b32c0146 KeyedServiceFactory::GetServiceForContext()
 #11 0x000080eecb66 <unknown>
 #12 0x000080eded97 <unknown>
 #13 0x000080e20875 <unknown>
 #14 0x000080e222f8 <unknown>
 #15 0x000080e243ce <unknown>
 #16 0x000080e244cf <unknown>
 #17 0x000080e2478c <unknown>
 #18 0x000081af7be0 <unknown>
 #19 0x000081061148 <unknown>
 #20 0x00008106208c <unknown>
 #21 0x0000b4d890d9 content::BrowserMainLoop::PreMainMessageLoopRun()
 #22 0x0000b50e3657 content::StartupTaskRunner::RunAllTasksNow()
 #23 0x0000b4d8a76e content::BrowserMainLoop::CreateStartupTasks()
 #24 0x0000b4d8f7a3 <unknown>
 #25 0x0000b4d88252 content::BrowserMain()
 #26 0x0000b54c55ee <unknown>
 #27 0x0000b0211adb service_manager::Main()
 #28 0x0000b54c4140 content::ContentMain()
 #29 0x000080989ab7 <unknown>
 #30 0x00008098808b <unknown>
 #31 0x0000b0361637 __libc_start_main
 #32 0x0000809898fe <unknown>
   gs: 00000033  fs: 00000000  es: 0000007b  ds: 0000007b
  edi: 83e266d4 esi: 83e26538 ebp: bf81a168 esp: bf81a030
  ebx: 83e26380 edx: 00000006 ecx: 00000026 eax: bf81a180
  trp: 0000000e err: 00000004  ip: 811e8c1c  cs: 00000073
  efl: 00210286 usp: bf81a030  ss: 0000007b
 [end of stack trace]
 Calling _exit(1). Core file will not be generated.
 ]0;shayla@shayla-vm: ~shayla@shayla-vm:~$ exit
 exit
  
 Script done on Wed 07 Jun 2017 12:24:01 PM EDT

```

```

shayla@shayla-vm:~$ sudo apt-get purge chromium-browser
 [sudo] password for shayla: 
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 The following packages were automatically installed and are no longer required:
   linux-headers-4.4.0-71 linux-headers-4.4.0-71-generic linux-headers-4.4.0-72
   linux-headers-4.4.0-72-generic linux-headers-4.4.0-75
   linux-headers-4.4.0-75-generic linux-headers-4.4.0-77
   linux-headers-4.4.0-77-generic linux-image-4.4.0-71-generic
   linux-image-4.4.0-72-generic linux-image-4.4.0-75-generic
   linux-image-4.4.0-77-generic linux-image-extra-4.4.0-71-generic
   linux-image-extra-4.4.0-72-generic linux-image-extra-4.4.0-75-generic
   linux-image-extra-4.4.0-77-generic
 Use 'sudo apt autoremove' to remove them.
 The following packages will be REMOVED:
   chromium-browser* chromium-browser-l10n*
 0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
 After this operation, 288 MB disk space will be freed.
 Do you want to continue? [Y/n] y
 (Reading database ... 327843 files and directories currently installed.)
 Removing chromium-browser-l10n (59.0.3071.86-0ubuntu0.16.04.1283) ...
 Removing chromium-browser (59.0.3071.86-0ubuntu0.16.04.1283) ...
 Purging configuration files for chromium-browser (59.0.3071.86-0ubuntu0.16.04.1283) ...
 Processing triggers for man-db (2.7.5-1) ...
 Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
 Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
 Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
 Processing triggers for mime-support (3.59ubuntu1) ...
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 shayla@shayla-vm:~$ sudo apt autoremove
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 The following packages will be REMOVED:
   linux-headers-4.4.0-71 linux-headers-4.4.0-71-generic linux-headers-4.4.0-72
   linux-headers-4.4.0-72-generic linux-headers-4.4.0-75
   linux-headers-4.4.0-75-generic linux-headers-4.4.0-77
   linux-headers-4.4.0-77-generic linux-image-4.4.0-71-generic
   linux-image-4.4.0-72-generic linux-image-4.4.0-75-generic
   linux-image-4.4.0-77-generic linux-image-extra-4.4.0-71-generic
   linux-image-extra-4.4.0-72-generic linux-image-extra-4.4.0-75-generic
   linux-image-extra-4.4.0-77-generic
 0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
 After this operation, 954 MB disk space will be freed.
 Do you want to continue? [Y/n] y
 (Reading database ... 327565 files and directories currently installed.)
 Removing linux-headers-4.4.0-71-generic (4.4.0-71.92) ...
 Removing linux-headers-4.4.0-71 (4.4.0-71.92) ...
 Removing linux-headers-4.4.0-72-generic (4.4.0-72.93) ...
 Removing linux-headers-4.4.0-72 (4.4.0-72.93) ...
 Removing linux-headers-4.4.0-75-generic (4.4.0-75.96) ...
 Removing linux-headers-4.4.0-75 (4.4.0-75.96) ...
 Removing linux-headers-4.4.0-77-generic (4.4.0-77.98) ...
 Removing linux-headers-4.4.0-77 (4.4.0-77.98) ...
 Removing linux-image-extra-4.4.0-71-generic (4.4.0-71.92) ...
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
 update-initramfs: Generating /boot/initrd.img-4.4.0-71-generic
 run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
 run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
 run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-79-generic
 Found initrd image: /boot/initrd.img-4.4.0-79-generic
 Found linux image: /boot/vmlinuz-4.4.0-78-generic
 Found initrd image: /boot/initrd.img-4.4.0-78-generic
 Found linux image: /boot/vmlinuz-4.4.0-77-generic
 Found initrd image: /boot/initrd.img-4.4.0-77-generic
 Found linux image: /boot/vmlinuz-4.4.0-75-generic
 Found initrd image: /boot/initrd.img-4.4.0-75-generic
 Found linux image: /boot/vmlinuz-4.4.0-72-generic
 Found initrd image: /boot/initrd.img-4.4.0-72-generic
 Found linux image: /boot/vmlinuz-4.4.0-71-generic
 Found initrd image: /boot/initrd.img-4.4.0-71-generic
 Found memtest86+ image: /boot/memtest86+.elf
 Found memtest86+ image: /boot/memtest86+.bin
 done
 Removing linux-image-4.4.0-71-generic (4.4.0-71.92) ...
 Examining /etc/kernel/postrm.d .
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
 update-initramfs: Deleting /boot/initrd.img-4.4.0-71-generic
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-79-generic
 Found initrd image: /boot/initrd.img-4.4.0-79-generic
 Found linux image: /boot/vmlinuz-4.4.0-78-generic
 Found initrd image: /boot/initrd.img-4.4.0-78-generic
 Found linux image: /boot/vmlinuz-4.4.0-77-generic
 Found initrd image: /boot/initrd.img-4.4.0-77-generic
 Found linux image: /boot/vmlinuz-4.4.0-75-generic
 Found initrd image: /boot/initrd.img-4.4.0-75-generic
 Found linux image: /boot/vmlinuz-4.4.0-72-generic
 Found initrd image: /boot/initrd.img-4.4.0-72-generic
 Found memtest86+ image: /boot/memtest86+.elf
 Found memtest86+ image: /boot/memtest86+.bin
 done
 Removing linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
 update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic
 run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
 run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
 run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-79-generic
 Found initrd image: /boot/initrd.img-4.4.0-79-generic
 Found linux image: /boot/vmlinuz-4.4.0-78-generic
 Found initrd image: /boot/initrd.img-4.4.0-78-generic
 Found linux image: /boot/vmlinuz-4.4.0-77-generic
 Found initrd image: /boot/initrd.img-4.4.0-77-generic
 Found linux image: /boot/vmlinuz-4.4.0-75-generic
 Found initrd image: /boot/initrd.img-4.4.0-75-generic
 Found linux image: /boot/vmlinuz-4.4.0-72-generic
 Found initrd image: /boot/initrd.img-4.4.0-72-generic
 Found memtest86+ image: /boot/memtest86+.elf
 Found memtest86+ image: /boot/memtest86+.bin
 done
 Removing linux-image-4.4.0-72-generic (4.4.0-72.93) ...
 Examining /etc/kernel/postrm.d .
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
 update-initramfs: Deleting /boot/initrd.img-4.4.0-72-generic
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-79-generic
 Found initrd image: /boot/initrd.img-4.4.0-79-generic
 Found linux image: /boot/vmlinuz-4.4.0-78-generic
 Found initrd image: /boot/initrd.img-4.4.0-78-generic
 Found linux image: /boot/vmlinuz-4.4.0-77-generic
 Found initrd image: /boot/initrd.img-4.4.0-77-generic
 Found linux image: /boot/vmlinuz-4.4.0-75-generic
 Found initrd image: /boot/initrd.img-4.4.0-75-generic
 Found memtest86+ image: /boot/memtest86+.elf
 Found memtest86+ image: /boot/memtest86+.bin
 done
 Removing linux-image-extra-4.4.0-75-generic (4.4.0-75.96) ...
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
 update-initramfs: Generating /boot/initrd.img-4.4.0-75-generic
 run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
 run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
 run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-79-generic
 Found initrd image: /boot/initrd.img-4.4.0-79-generic
 Found linux image: /boot/vmlinuz-4.4.0-78-generic
 Found initrd image: /boot/initrd.img-4.4.0-78-generic
 Found linux image: /boot/vmlinuz-4.4.0-77-generic
 Found initrd image: /boot/initrd.img-4.4.0-77-generic
 Found linux image: /boot/vmlinuz-4.4.0-75-generic
 Found initrd image: /boot/initrd.img-4.4.0-75-generic
 Found memtest86+ image: /boot/memtest86+.elf
 Found memtest86+ image: /boot/memtest86+.bin
 done
 Removing linux-image-4.4.0-75-generic (4.4.0-75.96) ...
 Examining /etc/kernel/postrm.d .
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
 update-initramfs: Deleting /boot/initrd.img-4.4.0-75-generic
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-79-generic
 Found initrd image: /boot/initrd.img-4.4.0-79-generic
 Found linux image: /boot/vmlinuz-4.4.0-78-generic
 Found initrd image: /boot/initrd.img-4.4.0-78-generic
 Found linux image: /boot/vmlinuz-4.4.0-77-generic
 Found initrd image: /boot/initrd.img-4.4.0-77-generic
 Found memtest86+ image: /boot/memtest86+.elf
 Found memtest86+ image: /boot/memtest86+.bin
 done
 Removing linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
 update-initramfs: Generating /boot/initrd.img-4.4.0-77-generic
 run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
 run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
 run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-79-generic
 Found initrd image: /boot/initrd.img-4.4.0-79-generic
 Found linux image: /boot/vmlinuz-4.4.0-78-generic
 Found initrd image: /boot/initrd.img-4.4.0-78-generic
 Found linux image: /boot/vmlinuz-4.4.0-77-generic
 Found initrd image: /boot/initrd.img-4.4.0-77-generic
 Found memtest86+ image: /boot/memtest86+.elf
 Found memtest86+ image: /boot/memtest86+.bin
 done
 Removing linux-image-4.4.0-77-generic (4.4.0-77.98) ...
 Examining /etc/kernel/postrm.d .
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
 update-initramfs: Deleting /boot/initrd.img-4.4.0-77-generic
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-79-generic
 Found initrd image: /boot/initrd.img-4.4.0-79-generic
 Found linux image: /boot/vmlinuz-4.4.0-78-generic
 Found initrd image: /boot/initrd.img-4.4.0-78-generic
 Found memtest86+ image: /boot/memtest86+.elf
 Found memtest86+ image: /boot/memtest86+.bin
 done
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 shayla@shayla-vm:~$ sudo apt install chromium-browser
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 The following additional packages will be installed:
   chromium-browser-l10n
 Suggested packages:
   webaccounts-chromium-extension unity-chromium-extension adobe-flashplugin
 The following NEW packages will be installed:
   chromium-browser chromium-browser-l10n
 0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
 Need to get 0 B/66.5 MB of archives.
 After this operation, 288 MB of additional disk space will be used.
 Do you want to continue? [Y/n] y
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 Selecting previously unselected package chromium-browser.
 (Reading database ... 197591 files and directories currently installed.)
 Preparing to unpack .../chromium-browser_59.0.3071.86-0ubuntu0.16.04.1283_i386.deb ...
 Unpacking chromium-browser (59.0.3071.86-0ubuntu0.16.04.1283) ...
 Selecting previously unselected package chromium-browser-l10n.
 Preparing to unpack .../chromium-browser-l10n_59.0.3071.86-0ubuntu0.16.04.1283_all.deb ...
 Unpacking chromium-browser-l10n (59.0.3071.86-0ubuntu0.16.04.1283) ...
 Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
 Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
 Processing triggers for mime-support (3.59ubuntu1) ...
 Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
 Processing triggers for man-db (2.7.5-1) ...
 Setting up chromium-browser (59.0.3071.86-0ubuntu0.16.04.1283) ...
 Setting up chromium-browser-l10n (59.0.3071.86-0ubuntu0.16.04.1283) ...
 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 shayla@shayla-vm:~$ chromium-browser
 Received signal 11 SEGV_MAPERR 0000031d9a20
 #0 0x0000b75c8ee3 base::debug::StackTrace::StackTrace()
 #1 0x0000b75c8767 base::debug::StackTrace::StackTrace()
 #2 0x0000b75c92fe <unknown>
 #3 0x0000b7713c20 ([vdso]+0xc1f)
 #4 0x0000811b7c1c <unknown>
 #5 0x0000811b89d8 <unknown>
 #6 0x000080ec02e8 <unknown>
 #7 0x000080eb85c3 <unknown>
 #8 0x000080ebba72 <unknown>
 #9 0x0000b2bb299c BrowserContextKeyedServiceFactory::BuildServiceInstanceFor()
 #10 0x0000b3270146 KeyedServiceFactory::GetServiceForContext()
 #11 0x000080ebbb66 <unknown>
 #12 0x000080dfde3e <unknown>
 #13 0x000080dfe738 <unknown>
 #14 0x000081a7725e <unknown>
 #15 0x000080de8dc6 <unknown>
 #16 0x000080f6a5e2 <unknown>
 #17 0x000080f6aac5 <unknown>
 #18 0x0000b509bfcc content::StoragePartitionImplMap::Get()
 #19 0x0000b4d35259 <unknown>
 #20 0x0000b4d35ba7 content::BrowserContext::GetStoragePartition()
 #21 0x0000b4d35dc7 content::BrowserContext::GetDefaultStoragePartition()
 #22 0x000080f6799e <unknown>
 #23 0x000080f68284 <unknown>
 #24 0x000080f68641 <unknown>
 #25 0x000080f69537 <unknown>
 #26 0x000080f697ab <unknown>
 #27 0x000080dedba3 <unknown>
 #28 0x000080df34bd <unknown>
 #29 0x000080df378c <unknown>
 #30 0x000081ac6be0 <unknown>
 #31 0x000081030148 <unknown>
 #32 0x00008103108c <unknown>
 #33 0x0000b4d390d9 content::BrowserMainLoop::PreMainMessageLoopRun()
 #34 0x0000b5093657 content::StartupTaskRunner::RunAllTasksNow()
 #35 0x0000b4d3a76e content::BrowserMainLoop::CreateStartupTasks()
 #36 0x0000b4d3f7a3 <unknown>
 #37 0x0000b4d38252 content::BrowserMain()
 #38 0x0000b54755ee <unknown>
 #39 0x0000b01c1adb service_manager::Main()
 #40 0x0000b5474140 content::ContentMain()
 #41 0x000080958ab7 <unknown>
 #42 0x00008095708b <unknown>
 #43 0x0000b0311637 __libc_start_main
 #44 0x0000809588fe <unknown>
   gs: 00000033  fs: 00000000  es: 0000007b  ds: 0000007b
  edi: 84c2f76c esi: 84c2f5d0 ebp: bfed1958 esp: bfed1820
  ebx: 84c2f418 edx: 00000006 ecx: 00000026 eax: bfed1970
  trp: 0000000e err: 00000004  ip: 811b7c1c  cs: 00000073
  efl: 00210282 usp: bfed1820  ss: 0000007b
 [end of stack trace]
 Calling _exit(1). Core file will not be generated.
 shayla@shayla-vm:~$

```

---

### Post by valvegrid on 2017-06-07
Thanks for the reply, I'm glad I'm not alone. I'm just wondering if it's a 32 bit problem.

I've just downloaded a copy of 16.04.02 MATE 64 bit ready to install if there's not resolution soon, but I'll be patient first.

---

### Post by cariboo on 2017-06-07
Try creating a new user profile, instructions here:

[https://www.chromium.org/developers/creating-and-using-profiles](https://www.chromium.org/developers/creating-and-using-profiles)

to see if the problem persists.

---

### Post by valvegrid on 2017-06-07
> **cariboo said:**
> Try creating a new user profile, instructions here:

[https://www.chromium.org/developers/creating-and-using-profiles](https://www.chromium.org/developers/creating-and-using-profiles)

to see if the problem persists.

No, still the same, I did try that first because I had a problem some time ago with a faulty extension.

I'm just wondering if it's something to do with flashplayer because what it's looking for in the first couple of lines is

```
--ppapi-flash-path=/usr/lib/adobe-flashplugin/libpepflashplayer.so --ppapi-flash-version=
Received signal 11 SEGV_MAPERR 000002f5df78
```

Then it seems to go all downhill after that.

Edit: I've just notice my profile says Ubuntu 12.04, that is probably the last time I used the forum for help :) just shows how good Linux is.

---

### Post by 0skillz on 2017-06-07
> **cariboo said:**
> Try creating a new user profile, instructions here:

[https://www.chromium.org/developers/creating-and-using-profiles](https://www.chromium.org/developers/creating-and-using-profiles)

to see if the problem persists.

nope!

my chrome-dev-profile folder filled up with files but no browser window appears.

```

shayla@shayla-vm:~$ chromium-browser --user-data-dir=/home/shayla/chrome-dev-profile/
Received signal 11 SEGV_MAPERR 0000031d9a20
#0 0x0000b767aee3 base::debug::StackTrace::StackTrace()
#1 0x0000b767a767 base::debug::StackTrace::StackTrace()
#2 0x0000b767b2fe <unknown>
#3 0x0000b77c5c20 ([vdso]+0xc1f)
#4 0x0000811d4c1c <unknown>
#5 0x0000811d59d8 <unknown>
#6 0x000080edd2e8 <unknown>
#7 0x000080ed55c3 <unknown>
#8 0x000080ed8a72 <unknown>
#9 0x0000b2c6499c BrowserContextKeyedServiceFactory::BuildServiceInstanceFor()
#10 0x0000b3322146 KeyedServiceFactory::GetServiceForContext()
#11 0x000080ed8b66 <unknown>
#12 0x000080e1ae3e <unknown>
#13 0x000080e1b738 <unknown>
#14 0x000081a9425e <unknown>
#15 0x000080e05dc6 <unknown>
#16 0x000080f875e2 <unknown>
#17 0x000080f87ac5 <unknown>
#18 0x0000b514dfcc content::StoragePartitionImplMap::Get()
#19 0x0000b4de7259 <unknown>
#20 0x0000b4de7ba7 content::BrowserContext::GetStoragePartition()
#21 0x0000b4de7dc7 content::BrowserContext::GetDefaultStoragePartition()
#22 0x000080f8499e <unknown>
#23 0x000080f85284 <unknown>
#24 0x000080f85641 <unknown>
#25 0x000080f86537 <unknown>
#26 0x000080f867ab <unknown>
#27 0x000080e0aba3 <unknown>
#28 0x000080e104bd <unknown>
#29 0x000080e1078c <unknown>
#30 0x000081ae3be0 <unknown>
#31 0x00008104d148 <unknown>
#32 0x00008104e08c <unknown>
#33 0x0000b4deb0d9 content::BrowserMainLoop::PreMainMessageLoopRun()
#34 0x0000b5145657 content::StartupTaskRunner::RunAllTasksNow()
#35 0x0000b4dec76e content::BrowserMainLoop::CreateStartupTasks()
#36 0x0000b4df17a3 <unknown>
#37 0x0000b4dea252 content::BrowserMain()
#38 0x0000b55275ee <unknown>
#39 0x0000b0273adb service_manager::Main()
#40 0x0000b5526140 content::ContentMain()
#41 0x000080975ab7 <unknown>
#42 0x00008097408b <unknown>
#43 0x0000b03c3637 __libc_start_main
#44 0x0000809758fe <unknown>
  gs: 00000033  fs: 00000000  es: 0000007b  ds: 0000007b
 edi: 84ad043c esi: 84ad02a0 ebp: bfbaa458 esp: bfbaa320
 ebx: 84ad00e8 edx: 00000006 ecx: 00000026 eax: bfbaa470
 trp: 0000000e err: 00000004  ip: 811d4c1c  cs: 00000073
 efl: 00210282 usp: bfbaa320  ss: 0000007b
[end of stack trace]
Calling _exit(1). Core file will not be generated.
shayla@shayla-vm:~$ 

```

---

### Post by valvegrid on 2017-06-08
You know what, I'm not going to mess with it any more, I'm going to stick Ubuntu MATE 16.04 LTS 64 bit and be done with it. I was going to do that sometime ago but never got around to it, so I've got no excuses now.

Thanks for those that tried to help and I hope you find a resolution 0skill.[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=2069367")

I'll mark this as resolved, as it will be when the new install is complete.

---

### Post by dvdasuaje1475963 on 2017-06-09
> **valvegrid said:**
> You know what, I'm not going to mess with it any more, I'm going to stick Ubuntu MATE 16.04 LTS 64 bit and be done with it. I was going to do that sometime ago but never got around to it, so I've got no excuses now.

Thanks for those that tried to help and I hope you find a resolution 0skill.

I'll mark this as resolved, as it will be when the new install is complete.

Hi everybody 

please reopen,

thanks

---

### Post by valvegrid on 2017-06-09
> **dvdasuaje1475963 said:**
> Hi everybody 

please reopen,

thanks

Just for you ;)

I must say it works perfectly OK in 16.04LTS.

---

### Post by 0skillz on 2017-06-09
ok... so I found that apt has a log.  I was thinking that chromium  stopped working for me the same day I found this post but I must be  wrong because my apt log doesn't support that.  It definitely happened  after some software updates that asked me to reboot, so I did.

/var/log/apt/history.log
```

Start-Date: 2017-06-01  14:18:57
Commandline: aptdaemon role='role-commit-packages' sender=':1.1631'
Upgrade:  libldap-2.4-2:i386 (2.4.42+dfsg-2ubuntu3.1, 2.4.42+dfsg-2ubuntu3.2),  libsndfile1:i386 (1.0.25-10, 1.0.25-10ubuntu0.16.04.1)
End-Date: 2017-06-01  14:19:02

Start-Date: 2017-06-06  12:11:51
Commandline: aptdaemon role='role-commit-packages' sender=':1.2691'
Upgrade:  isc-dhcp-common:i386 (4.3.3-5ubuntu12.6, 4.3.3-5ubuntu12.7),  libtasn1-6:i386 (4.7-3ubuntu0.16.04.1, 4.7-3ubuntu0.16.04.2),  isc-dhcp-client:i386 (4.3.3-5ubuntu12.6, 4.3.3-5ubuntu12.7)
End-Date: 2017-06-06  12:11:58

```

and if it might be helpful, /var/log/apt/term.log:
```

Log started: 2017-06-01  14:18:57
(Reading database ... 
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
(Reading database ... 295337 files and directories currently installed.)
Preparing to unpack .../libldap-2.4-2_2.4.42+dfsg-2ubuntu3.2_i386.deb ...
Unpacking libldap-2.4-2:i386 (2.4.42+dfsg-2ubuntu3.2) over (2.4.42+dfsg-2ubuntu3.1) ...
Preparing to unpack .../libsndfile1_1.0.25-10ubuntu0.16.04.1_i386.deb ...
Unpacking libsndfile1:i386 (1.0.25-10ubuntu0.16.04.1) over (1.0.25-10) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Setting up libldap-2.4-2:i386 (2.4.42+dfsg-2ubuntu3.2) ...
Setting up libsndfile1:i386 (1.0.25-10ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Log ended: 2017-06-01  14:19:02

Log started: 2017-06-06  12:11:51
(Reading database ... 
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
(Reading database ... 295337 files and directories currently installed.)
Preparing to unpack .../isc-dhcp-client_4.3.3-5ubuntu12.7_i386.deb ...
Unpacking isc-dhcp-client (4.3.3-5ubuntu12.7) over (4.3.3-5ubuntu12.6) ...
Preparing to unpack .../isc-dhcp-common_4.3.3-5ubuntu12.7_i386.deb ...
Unpacking isc-dhcp-common (4.3.3-5ubuntu12.7) over (4.3.3-5ubuntu12.6) ...
Preparing to unpack .../libtasn1-6_4.7-3ubuntu0.16.04.2_i386.deb ...
Unpacking libtasn1-6:i386 (4.7-3ubuntu0.16.04.2) over (4.7-3ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Setting up isc-dhcp-client (4.3.3-5ubuntu12.7) ...
Setting up isc-dhcp-common (4.3.3-5ubuntu12.7) ...
Setting up libtasn1-6:i386 (4.7-3ubuntu0.16.04.2) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Log ended: 2017-06-06  12:11:58

```

I'm  not sure what other logs might be helpful in figuring this out, not  sure if I'll have time to dig into this more this weekend or not, but in  case it helps anyone figured I should post my logs.  The old laptop I  have with Xubuntu 16.04 32 bit on it is pretty much a duplicate install  of the VM where I've lost the ability to run Chromium... and I would  rather not risk losing Chromium on the laptop by doing software updates.

---

### Post by valvegrid on 2017-06-09
I agree, I did an update in the morning before I went to work and turned the computer on in the afternoon and found Chrome Browser not working, so I would say it was definitely and update that messed it up.

Having said that I have got a small Toshiba Netbook that I've had for years and that has got Ubuntu 14.04LTS using the MATE desktop and there's no problem on that running Chrome.

I'm not sure if there's any relevance, but on the desktop I was running Ubuntu 14.04LTS and using fallback to use a different desktop and not Unity which I hated, it might be a red herring, I just don't know.

---

### Post by monkeybrain20122 on 2017-06-09
> **valvegrid said:**
> I agree, I did an update in the morning before I went to work and turned the computer on in the afternoon and found Chrome Browser not working, so I would say it was definitely and update that messed it up.

Having said that I have got a small Toshiba Netbook that I've had for years and that has got Ubuntu 14.04LTS using the MATE desktop and there's no problem on that running Chrome.

I'm not sure if there's any relevance, but on the desktop I was running Ubuntu 14.04LTS and using fallback to use a different desktop and not Unity which I hated, it might be a red herring, I just don't know.


What are you talking about? Chrome or Chromium? The two are different. I have not had any problem with Chrome but Chromium is poorly maintained perpetual beta (or alpha)  so yes, it does experience problems from time to time.

---

### Post by valvegrid on 2017-06-10
> **monkeybrain20122 said:**
> What are you talking about? Chrome or Chromium? The two are different. I have not had any problem with Chrome but Chromium is poorly maintained perpetual beta (or alpha)  so yes, it does experience problems from time to time.

What is says in the title.

---

### Post by vasa1 on 2017-06-10
> **valvegrid said:**
> What is says in the title.
I think the question was raised by your mentioning "Chrome Browser."
> **valvegrid said:**
> I agree, I did an update in the morning before I went to work and turned the computer on in the afternoon and found Chrome Browser not working, so I would say it was definitely and update that messed it up.

Having said that I have got a small Toshiba Netbook that I've had for years and that has got Ubuntu 14.04LTS using the MATE desktop and there's no problem on that running Chrome.

I'm not sure if there's any relevance, but on the desktop I was running Ubuntu 14.04LTS and using fallback to use a different desktop and not Unity which I hated, it might be a red herring, I just don't know.
So let's, all of us, be a little careful. Thanks

---

### Post by 0skillz on 2017-06-11
just updating with some more details and what i've found today, still not working for me on Xubuntu 16.04 LTS 32 bit virtual machine.

This  is specifically where/how I've been getting Chromium that has stopped  working and the source my previous terminal pastes with errors.
[https://chromium.woolyss.com/#ubuntu](https://chromium.woolyss.com/#ubuntu)

This  morning I made a new VM with a fresh install of Xubuntu 16.04 32 bit  LTS this morning... and it fails exactly as I've seen before.

Then  I made a new VM with a fresh install of Xubuntu 17.04 32 bit and  Chromium worked fine.  Chromium version 59.0.3071.86 32 bit.  I assume  it's the same version as what's failing for me on Xubuntu 16.04 32 bit  LTS, not sure how I could confirm since Chromium won't launch for me  there.

Upgrading my old dual core laptop to a non-LTS is  something I really do not want to do if/when I do a software update that  kills Chromium there as well.  That laptop mainly runs youtube videos  all day and firefox does not do that as well as Chromium does so using  Firefox doesn't work for my case either.

I also tried Chromium 32 bit (x86) from here:
[https://download-chromium.appspot.com/?platform=Linux&type=snapshots](https://download-chromium.appspot.com/?platform=Linux&type=snapshots)
it fails on Xubuntu 16.04 32 bit LTS too:
```
shayla@shayla-vm:~/Desktop/chrome-linux$ ./chrome
[15720:15720:0611/075516:FATAL:browser_main_loop.cc(221)]  Running without the SUID sandbox! See  https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md  for more information on developing with the sandbox on.
#0 0x000080a0d8aa base::debug::StackTrace::StackTrace()
#1 0x000080a2516d logging::LogMessage::~LogMessage()
#2 0x0000838120fd content::BrowserMainLoop::EarlyInitialization()
#3 0x0000835a4476 content::BrowserMainRunnerImpl::Initialize()
#4 0x0000835a3f38 content::BrowserMain()
#5 0x0000809d16e2 content::RunNamedProcessTypeMain()
#6 0x0000809d2392 content::ContentMainRunnerImpl::Run()
#7 0x0000809d0c72 content::ContentMain()
#8 0x0000804ca3ca ChromeMain
#9 0x0000804ca378 main
#10 0x0000b6130637 __libc_start_main
#11 0x0000804ca27d <unknown>

Aborted (core dumped)
shayla@shayla-vm:~/Desktop/chrome-linux$ ./chrome-wrapper
[15725:15725:0611/075633:FATAL:browser_main_loop.cc(221)]  Running without the SUID sandbox! See  https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md  for more information on developing with the sandbox on.
#0 0x00008099f8aa base::debug::StackTrace::StackTrace()
#1 0x0000809b716d logging::LogMessage::~LogMessage()
#2 0x0000837a40fd content::BrowserMainLoop::EarlyInitialization()
#3 0x000083536476 content::BrowserMainRunnerImpl::Initialize()
#4 0x000083535f38 content::BrowserMain()
#5 0x0000809636e2 content::RunNamedProcessTypeMain()
#6 0x000080964392 content::ContentMainRunnerImpl::Run()
#7 0x000080962c72 content::ContentMain()
#8 0x00008045c3ca ChromeMain
#9 0x00008045c378 main
#10 0x0000b61f2637 __libc_start_main
#11 0x00008045c27d <unknown>

Aborted (core dumped)
shayla@shayla-vm:~/Desktop/chrome-linux$ 


```

It's  entirely possible that I just don't know what I'm doing with that one  though and have not tried it on the fresh install of Xubuntu 17.04 32 bit.

sped up desktop recording to show:
[https://www.youtube.com/watch?v=4dcrQrjNV1o](https://www.youtube.com/watch?v=4dcrQrjNV1o)

---

### Post by dvdasuaje1475963 on 2017-06-11
> **valvegrid said:**
> Just for you ;)

I must say it works perfectly OK in 16.04LTS.

Thanks a lot, I'm working on Ubuntu 16.04LTS also
chromium-browser
Using PPAPI flash.```

 --ppapi-flash-path=/usr/lib/adobe-flashplugin/libpepflashplayer.so --ppapi-flash-version=
Received signal 11 SEGV_MAPERR 0000031d9a20
#0 0x0000b7587ee3 base::debug::StackTrace::StackTrace()
#1 0x0000b7587767 base::debug::StackTrace::StackTrace()
#2 0x0000b75882fe <unknown>
#3 0x0000b76e3c20 ([vdso]+0xc1f)
#4 0x00008120ac1c <unknown>
#5 0x00008120b9d8 <unknown>
#6 0x000080f132e8 <unknown>
#7 0x000080f0b5c3 <unknown>
#8 0x000080f0ea72 <unknown>
#9 0x0000b2b7199c BrowserContextKeyedServiceFactory::BuildServiceInstanceFor()
#10 0x0000b322f146 KeyedServiceFactory::GetServiceForContext()
#11 0x000080f0eb66 <unknown>
#12 0x000080f00d97 <unknown>
#13 0x000080e42875 <unknown>
#14 0x000080e442f8 <unknown>
#15 0x000080e463ce <unknown>
#16 0x000080e464cf <unknown>
#17 0x000080e4678c <unknown>
#18 0x000081b19be0 <unknown>
#19 0x000081083148 <unknown>
#20 0x00008108408c <unknown>
#21 0x0000b4cf80d9 content::BrowserMainLoop::PreMainMessageLoopRun()
#22 0x0000b5052657 content::StartupTaskRunner::RunAllTasksNow()
#23 0x0000b4cf976e content::BrowserMainLoop::CreateStartupTasks()
#24 0x0000b4cfe7a3 <unknown>
#25 0x0000b4cf7252 content::BrowserMain()
#26 0x0000b54345ee <unknown>
#27 0x0000b0180adb service_manager::Main()
#28 0x0000b5433140 content::ContentMain()
#29 0x0000809abab7 <unknown>
#30 0x0000809aa08b <unknown>
#31 0x0000b02d0637 __libc_start_main
#32 0x0000809ab8fe <unknown>
  gs: 00000033  fs: 00000000  es: 0000007b  ds: 0000007b
 edi: 839b9bdc esi: 839b9a40 ebp: bff87168 esp: bff87030
 ebx: 839b9888 edx: 00000006 ecx: 00000026 eax: bff87180
 trp: 0000000e err: 00000004  ip: 8120ac1c  cs: 00000073
 efl: 00210286 usp: bff87030  ss: 0000007b
[end of stack trace]
Calling _exit(1). Core file will not be generated.
```
:p

---

### Post by 0skillz on 2017-06-15
I just received an update for the chromium-browser (that i get from here [https://chromium.woolyss.com/#ubuntu](https://chromium.woolyss.com/#ubuntu)) and all is well again!
[COLOR=#757575][FONT=Roboto]Version 59.0.3071.86 (Developer Build) Built on Ubuntu , running on Ubuntu 16.04 (32-bit)[/FONT][/COLOR]

I had been getting by with an older version of chromium from somewhere else (couldn't get flash to work in that, didn't try very hard) but did some more searching just now and found this: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1697496](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1697496) - looks related to me.

---

