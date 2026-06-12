---
title: "Multiple problems after fresh install"
date: 2013-11-15
forum: General Help
---

### Post by valdrin-qunaj on 2013-11-15
I did a fresh install of ubuntu 13.10 and at first everything seemed to be working fine, but now some problems are starting to rise up.

Every time i reboot ubuntu i am getting a "System program problem detected". I have no idea what is causing this problem, the only thing i can do is send the report but i have no idea how i can see the report myself.

Every time i reboot my keyboard layout will be switched to qwerty(English keyboard layout) while on the top right corner it clearly says that i am on the Belgian keyboard layout and not the English one. There is a "Be" logo highlighted and not the "En" logo. However if re click the "Be" logo the keyboard switches from qwerty to azerty (from English to Belgian keyboard layout)

I am having problems starting matlab and other programs from the terminal. When i installed matlab, all i had to do was type matlab and the program would start fine (I created the link manually). Then this wouldn't work anymore, i had to type matlab& to get control of the terminal back. Same thing happened to other programs like "kate", before just typing kate would work fine but later on i had to type kate& to get control back over the terminal and if I would close the terminal both Matlab and Kate would close down as well. Now the problem with Matlab has gotten even worse, first i have to sudo su and then i have to type matlab& for it to start properly, matlab never had any access problems and now they popped up out of nowhere.

---

### Post by ian-weisser on 2013-11-15
Well, you clearly have some permissions issues there.

You can usually find the problem report in /var/crash

---

### Post by valdrin-qunaj on 2013-11-16
> **ian-weisser said:**
> Well, you clearly have some permissions issues there.

You can usually find the problem report in /var/crash
OK so i managed to find the crash report but i cannot make much out of it. Also how do i clear the crash reports, since i don't really know which is from which.

```
ProblemType: CrashArchitecture: amd64
Date: Mon Nov 11 06:06:21 2013
DistroRelease: Ubuntu 13.10
ExecutablePath: /sbin/wpa_supplicant
ExecutableTimestamp: 1375973240
ProcCmdline: /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
ProcCwd: /
ProcEnviron: 
ProcMaps:
 00400000-0055f000 r-xp 00000000 08:05 1310953                            /sbin/wpa_supplicant
 0075e000-0075f000 r--p 0015e000 08:05 1310953                            /sbin/wpa_supplicant
 0075f000-00761000 rw-p 0015f000 08:05 1310953                            /sbin/wpa_supplicant
 02752000-02773000 rw-p 00000000 00:00 0                                  [heap]
 02773000-02794000 rw-p 00000000 00:00 0                                  [heap]
 7fcc4b00e000-7fcc4b015000 r-xp 00000000 08:05 2363356                    /lib/x86_64-linux-gnu/librt-2.17.so
 7fcc4b015000-7fcc4b214000 ---p 00007000 08:05 2363356                    /lib/x86_64-linux-gnu/librt-2.17.so
 7fcc4b214000-7fcc4b215000 r--p 00006000 08:05 2363356                    /lib/x86_64-linux-gnu/librt-2.17.so
 7fcc4b215000-7fcc4b216000 rw-p 00007000 08:05 2363356                    /lib/x86_64-linux-gnu/librt-2.17.so
 7fcc4b216000-7fcc4b22e000 r-xp 00000000 08:05 2363391                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fcc4b22e000-7fcc4b42d000 ---p 00018000 08:05 2363391                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fcc4b42d000-7fcc4b42e000 r--p 00017000 08:05 2363391                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fcc4b42e000-7fcc4b42f000 rw-p 00018000 08:05 2363391                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fcc4b42f000-7fcc4b532000 r-xp 00000000 08:05 2363284                    /lib/x86_64-linux-gnu/libm-2.17.so
 7fcc4b532000-7fcc4b731000 ---p 00103000 08:05 2363284                    /lib/x86_64-linux-gnu/libm-2.17.so
 7fcc4b731000-7fcc4b732000 r--p 00102000 08:05 2363284                    /lib/x86_64-linux-gnu/libm-2.17.so
 7fcc4b732000-7fcc4b733000 rw-p 00103000 08:05 2363284                    /lib/x86_64-linux-gnu/libm-2.17.so
 7fcc4b733000-7fcc4b74a000 r-xp 00000000 08:05 2363348                    /lib/x86_64-linux-gnu/libpthread-2.17.so
 7fcc4b74a000-7fcc4b94a000 ---p 00017000 08:05 2363348                    /lib/x86_64-linux-gnu/libpthread-2.17.so
 7fcc4b94a000-7fcc4b94b000 r--p 00017000 08:05 2363348                    /lib/x86_64-linux-gnu/libpthread-2.17.so
 7fcc4b94b000-7fcc4b94c000 rw-p 00018000 08:05 2363348                    /lib/x86_64-linux-gnu/libpthread-2.17.so
 7fcc4b94c000-7fcc4b950000 rw-p 00000000 00:00 0 
 7fcc4b950000-7fcc4bb0d000 r-xp 00000000 08:05 2363233                    /lib/x86_64-linux-gnu/libc-2.17.so
 7fcc4bb0d000-7fcc4bd0d000 ---p 001bd000 08:05 2363233                    /lib/x86_64-linux-gnu/libc-2.17.so
 7fcc4bd0d000-7fcc4bd11000 r--p 001bd000 08:05 2363233                    /lib/x86_64-linux-gnu/libc-2.17.so
 7fcc4bd11000-7fcc4bd13000 rw-p 001c1000 08:05 2363233                    /lib/x86_64-linux-gnu/libc-2.17.so
 7fcc4bd13000-7fcc4bd18000 rw-p 00000000 00:00 0 
 7fcc4bd18000-7fcc4bd5c000 r-xp 00000000 08:05 2363245                    /lib/x86_64-linux-gnu/libdbus-1.so.3.7.4
 7fcc4bd5c000-7fcc4bf5b000 ---p 00044000 08:05 2363245                    /lib/x86_64-linux-gnu/libdbus-1.so.3.7.4
 7fcc4bf5b000-7fcc4bf5c000 r--p 00043000 08:05 2363245                    /lib/x86_64-linux-gnu/libdbus-1.so.3.7.4
 7fcc4bf5c000-7fcc4bf5d000 rw-p 00044000 08:05 2363245                    /lib/x86_64-linux-gnu/libdbus-1.so.3.7.4
 7fcc4bf5d000-7fcc4c10f000 r-xp 00000000 08:05 2363243                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fcc4c10f000-7fcc4c30f000 ---p 001b2000 08:05 2363243                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fcc4c30f000-7fcc4c32a000 r--p 001b2000 08:05 2363243                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fcc4c32a000-7fcc4c335000 rw-p 001cd000 08:05 2363243                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fcc4c335000-7fcc4c339000 rw-p 00000000 00:00 0 
 7fcc4c339000-7fcc4c38d000 r-xp 00000000 08:05 2363364                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fcc4c38d000-7fcc4c58d000 ---p 00054000 08:05 2363364                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fcc4c58d000-7fcc4c590000 r--p 00054000 08:05 2363364                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fcc4c590000-7fcc4c596000 rw-p 00057000 08:05 2363364                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fcc4c596000-7fcc4c597000 rw-p 00000000 00:00 0 
 7fcc4c597000-7fcc4c5a1000 r-xp 00000000 08:05 2363333                    /lib/x86_64-linux-gnu/libpcsclite.so.1.0.0
 7fcc4c5a1000-7fcc4c7a0000 ---p 0000a000 08:05 2363333                    /lib/x86_64-linux-gnu/libpcsclite.so.1.0.0
 7fcc4c7a0000-7fcc4c7a1000 r--p 00009000 08:05 2363333                    /lib/x86_64-linux-gnu/libpcsclite.so.1.0.0
 7fcc4c7a1000-7fcc4c7a2000 rw-p 0000a000 08:05 2363333                    /lib/x86_64-linux-gnu/libpcsclite.so.1.0.0
 7fcc4c7a2000-7fcc4c7a5000 r-xp 00000000 08:05 2363248                    /lib/x86_64-linux-gnu/libdl-2.17.so
 7fcc4c7a5000-7fcc4c9a4000 ---p 00003000 08:05 2363248                    /lib/x86_64-linux-gnu/libdl-2.17.so
 7fcc4c9a4000-7fcc4c9a5000 r--p 00002000 08:05 2363248                    /lib/x86_64-linux-gnu/libdl-2.17.so
 7fcc4c9a5000-7fcc4c9a6000 rw-p 00003000 08:05 2363248                    /lib/x86_64-linux-gnu/libdl-2.17.so
 7fcc4c9a6000-7fcc4c9ab000 r-xp 00000000 08:05 2363302                    /lib/x86_64-linux-gnu/libnl-genl-3.so.200.12.1
 7fcc4c9ab000-7fcc4cbaa000 ---p 00005000 08:05 2363302                    /lib/x86_64-linux-gnu/libnl-genl-3.so.200.12.1
 7fcc4cbaa000-7fcc4cbab000 r--p 00004000 08:05 2363302                    /lib/x86_64-linux-gnu/libnl-genl-3.so.200.12.1
 7fcc4cbab000-7fcc4cbac000 rw-p 00005000 08:05 2363302                    /lib/x86_64-linux-gnu/libnl-genl-3.so.200.12.1
 7fcc4cbac000-7fcc4cbc4000 r-xp 00000000 08:05 2363300                    /lib/x86_64-linux-gnu/libnl-3.so.200.12.1
 7fcc4cbc4000-7fcc4cdc3000 ---p 00018000 08:05 2363300                    /lib/x86_64-linux-gnu/libnl-3.so.200.12.1
 7fcc4cdc3000-7fcc4cdc5000 r--p 00017000 08:05 2363300                    /lib/x86_64-linux-gnu/libnl-3.so.200.12.1
 7fcc4cdc5000-7fcc4cdc6000 rw-p 00019000 08:05 2363300                    /lib/x86_64-linux-gnu/libnl-3.so.200.12.1
 7fcc4cdc6000-7fcc4cde9000 r-xp 00000000 08:05 2363209                    /lib/x86_64-linux-gnu/ld-2.17.so
 7fcc4cfc4000-7fcc4cfcb000 rw-p 00000000 00:00 0 
 7fcc4cfe6000-7fcc4cfe8000 rw-p 00000000 00:00 0 
 7fcc4cfe8000-7fcc4cfe9000 r--p 00022000 08:05 2363209                    /lib/x86_64-linux-gnu/ld-2.17.so
 7fcc4cfe9000-7fcc4cfeb000 rw-p 00023000 08:05 2363209                    /lib/x86_64-linux-gnu/ld-2.17.so
 7fffaf60c000-7fffaf62d000 rw-p 00000000 00:00 0                          [stack]
 7fffaf668000-7fffaf66a000 r-xp 00000000 00:00 0                          [vdso]
 ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
ProcStatus:
 Name:    wpa_supplicant
 State:    S (sleeping)
 Tgid:    739
 Pid:    739
 PPid:    1
 TracerPid:    0
 Uid:    0    0    0    0
 Gid:    0    0    0    0
 FDSize:    64
 Groups:    0 
 VmPeak:       32448 kB
 VmSize:       32444 kB
 VmLck:           0 kB
 VmPin:           0 kB
 VmHWM:        2656 kB
 VmRSS:        2656 kB
 VmData:         364 kB
 VmStk:         136 kB
 VmExe:        1404 kB
 VmLib:        5684 kB
 VmPTE:          80 kB
 VmSwap:           0 kB
 Threads:    1
 SigQ:    0/46425
 SigPnd:    0000000000000000
 ShdPnd:    0000000000000000
 SigBlk:    0000000000000000
 SigIgn:    0000000000000000
 SigCgt:    0000000190004003
 CapInh:    0000000000000000
 CapPrm:    0000001fffffffff
 CapEff:    0000001fffffffff
 CapBnd:    0000001fffffffff
 Seccomp:    0
 Cpus_allowed:    ff
 Cpus_allowed_list:    0-7
 Mems_allowed:    00000000,00000001
 Mems_allowed_list:    0
 voluntary_ctxt_switches:    2548
 nonvoluntary_ctxt_switches:    68
Signal: 11
Uname: Linux 3.11.0-12-generic x86_64
UserGroups: 
CoreDump: base64
 H4sICAAAAAAC/0NvcmVEdW1wAA==
 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****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EmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEmSJEn6fw==
 7VwLeFTVtT5nJk8SmGhR4q2WqRcUDAkTLiLIayYk5EQChpeiiElIAonNY0xmAvTaEhqwmQ5owEfBCiSCCgoYpVcRUQeCQCxoIHwVLV6DYj8C1sYXIiBz9zl7rZlzdmYItnzf7b2uX4d19mvttddee+291zlAIBAIBAKBQCAQCAQCgUAgEAgEAoFAIBAIBAKBQCAQCAQCgUAgEAgEAoFAIBAIBAKBQCAQCAQCgUAgEAgEAoFAIBAIBAKBQCAQCAQCgUAgEAgEAoFAIBAIBAKBQCAQCAQCgUAgEAgEAoFAIBAIBAKBQCAQCAQCgUAgEAgEAoFAIBAIBAKBQCAQCAQCgUAgEAgEAoFAIBAIBAKBQCAQCAQCgUAgEAgEAoFAIBAIBAKBQCAQCISL4abP2ybsXyhJCctmv+Bn9O7XDmlpEe1LeflcIY3tnCs4fXn3IQM/sd7U7bwc+Uh7eXr4I7x8xcpVWrrTy9Mon7TUKN8fobwJaITEfzaoVwf8wgLqVQtplM/2EE8nQn+lUG3lWLdJpX8Q0mvZT+vvtW+0+k2CvMgP9SFBepVQjv1XC/ppEuRtEuVdJsgL5Xp5IwR5ZSkob2l1vkFfyA/pWsgPyCvMZ87DPL14B/TPmNskq9S6nfOPA/2I+qrZwcut0D5HoK++YuSP6UpBP5rMuulFfVa+M0UbqR9QXM/zvwb5O5cZ7ccJ7eyXuH4mneT2aYL+Z7JfAvs1QD9oN05Ivwr6Qn2WfdFmWG8oX/tbXC/JH/DyQP6KeZr+GsKkcT7qQ+hHD9QnhyzFg9zYT28oT3jYqJ96SEdDGue3NN+sccJ0NHC2Luf1YyT+U+dALUO9XMw+VNSAfcoBSY3rzvm1UX+qnteGqIdybPmG14+H8tKWQxPW6vRiBhohKqyC89n7vnE+xPLN/8X1jf2hX8T6aAcx0GzCn3j91t3VJrFLtZ6oH70+9elL0WepTg+onzMgXyfkY7kd6PLTfLw4jrT94I+Eer5a3k8M2FH6cqP/aQjTH/L1jZ6olWd9x/vDdjZW3qBrV7SG998p8LdB+bBnjP5ab4/6+pJgX85mrv/iZuM8qO1VevRRg97keNAnVm6/n6/D9lJOpUbOB/WM833XcD6+vEeM9bHfPKF/lFfs/0lhPTihf1+J2yiHAOxfesRYH/udIfS/vffhkOO3LZhnGJ/1Ps4nB/gh33D9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
ApportVersion: 2.12.5-0ubuntu2.1
Dependencies:
 adduser 3.113+nmu3ubuntu2
 apt-utils 0.9.9.1~ubuntu3
 base-passwd 3.5.26
 busybox-initramfs 1:1.20.0-8.1ubuntu1
 coreutils 8.20-3ubuntu5
 cpio 2.11+dfsg-1ubuntu1
 dbus 1.6.12-0ubuntu10
 debconf 1.5.50ubuntu1
 debconf-i18n 1.5.50ubuntu1
 debianutils 4.4
 dpkg 1.16.12ubuntu1
 e2fslibs 1.42.8-1ubuntu1
 e2fsprogs 1.42.8-1ubuntu1
 findutils 4.4.2-6ubuntu1
 gcc-4.8-base 4.8.1-10ubuntu8
 ifupdown 0.7.44ubuntu3
 initramfs-tools 0.103ubuntu1
 initramfs-tools-bin 0.103ubuntu1
 initscripts 2.88dsf-41ubuntu3
 insserv 1.14.0-5ubuntu2
 iproute2 3.10.0-1ubuntu1
 isc-dhcp-client 4.2.4-7ubuntu8
 isc-dhcp-common 4.2.4-7ubuntu8
 klibc-utils 2.0.1-3.1ubuntu2
 kmod 9-3ubuntu1
 libacl1 2.2.52-1
 libapparmor1 2.8.0-0ubuntu31
 libapt-inst1.5 0.9.9.1~ubuntu3
 libapt-pkg4.12 0.9.9.1~ubuntu3
 libattr1 1:2.4.47-1
 libaudit-common 1:2.2.2-1ubuntu4
 libaudit1 1:2.2.2-1ubuntu4
 libblkid1 2.20.1-5.1ubuntu9
 libbz2-1.0 1.0.6-4
 libc6 2.17-93ubuntu4
 libcap2 1:2.22-1.2ubuntu2
 libcomerr2 1.42.8-1ubuntu1
 libdb5.1 5.1.29-7
 libdbus-1-3 1.6.12-0ubuntu10
 libdrm2 2.4.46-1
 libexpat1 2.1.0-4
 libgcc1 1:4.8.1-10ubuntu8
 libgpm2 1.20.4-6.1
 libjson-c2 0.11-2ubuntu1
 libjson0 0.11-2ubuntu1
 libklibc 2.0.1-3.1ubuntu2
 libkmod2 9-3ubuntu1
 liblocale-gettext-perl 1.05-7build2
 liblzma5 5.1.1alpha+20120614-2ubuntu1
 libmount1 2.20.1-5.1ubuntu9
 libncurses5 5.9+20130608-1ubuntu1
 libnih-dbus1 1.0.3-4ubuntu16
 libnih1 1.0.3-4ubuntu16
 libnl-3-200 3.2.16-0ubuntu1
 libnl-genl-3-200 3.2.16-0ubuntu1
 libpam-modules 1.1.3-8ubuntu3
 libpam-modules-bin 1.1.3-8ubuntu3
 libpam-systemd 204-0ubuntu19
 libpam0g 1.1.3-8ubuntu3
 libpci3 1:3.1.9-6ubuntu9
 libpcre3 1:8.31-2
 libpcsclite1 1.8.6-3ubuntu1b1
 libplymouth2 0.8.8-0ubuntu8
 libpng12-0 1.2.49-4ubuntu1
 libreadline5 5.2+dfsg-2
 libselinux1 2.1.13-2
 libsemanage-common 2.1.10-2
 libsemanage1 2.1.10-2
 libsepol1 2.1.9-2
 libslang2 2.2.4-15ubuntu1
 libss2 1.42.8-1ubuntu1
 libssl1.0.0 1.0.1e-3ubuntu1
 libstdc++6 4.8.1-10ubuntu8
 libsystemd-daemon0 204-0ubuntu19
 libsystemd-login0 204-0ubuntu19
 libtext-charwidth-perl 0.04-7build2
 libtext-iconv-perl 1.7-5build1
 libtext-wrapi18n-perl 0.06-7
 libtinfo5 5.9+20130608-1ubuntu1
 libudev1 204-0ubuntu19
 libusb-1.0-0 2:1.0.16-3
 libustr-1.0-1 1.0.4-3ubuntu1
 libuuid1 2.20.1-5.1ubuntu9
 libxtables10 1.4.18-1.1ubuntu1
 lsb-base 4.1+Debian11ubuntu4
 makedev 2.3.1-93ubuntu1
 module-init-tools 9-3ubuntu1
 mount 2.20.1-5.1ubuntu9
 mountall 2.52
 multiarch-support 2.17-93ubuntu4
 netbase 5.1
 passwd 1:4.1.5.1-1ubuntu6
 pciutils 1:3.1.9-6ubuntu9
 perl-base 5.14.2-21build1
 plymouth 0.8.8-0ubuntu8
 plymouth-theme-ubuntu-text 0.8.8-0ubuntu8
 psmisc 22.20-1ubuntu2
 readline-common 6.2-9ubuntu1
 sensible-utils 0.0.9
 systemd-services 204-0ubuntu19
 sysv-rc 2.88dsf-41ubuntu3
 sysvinit-utils 2.88dsf-41ubuntu3
 tar 1.26+dfsg-8
 tzdata 2013g-0ubuntu1
 udev 204-0ubuntu19
 upstart 1.10-0ubuntu7
 usbutils 1:007-2
 util-linux 2.20.1-5.1ubuntu9
 uuid-runtime 2.20.1-5.1ubuntu9
 zlib1g 1:1.2.8.dfsg-1ubuntu1
Disassembly:
 => 0x4b1880:    mov    (%r12),%rbx
    0x4b1884:    jne    0x4b192e
    0x4b188a:    jmpq   0x4b17dc
    0x4b188f:    nop
    0x4b1890:    callq  0x407fa0 <__errno_location@plt>
    0x4b1895:    mov    (%rax),%r11d
    0x4b1898:    mov    %rax,0x10(%rsp)
    0x4b189d:    mov    %r11d,%edi
    0x4b18a0:    mov    %r11d,0x1c(%rsp)
    0x4b18a5:    callq  0x407b70 <strerror@plt>
    0x4b18aa:    mov    0x10(%rsp),%rdx
    0x4b18af:    mov    %rax,%r8
    0x4b18b2:    mov    $0x520e18,%esi
    0x4b18b7:    xor    %eax,%eax
    0x4b18b9:    mov    $0x3,%edi
    0x4b18be:    mov    (%rdx),%ecx
InstallationDate: Installed on 2013-11-10 (0 days ago)
InstallationMedia: Ubuntu 13.10 "Saucy Salamander" - Release amd64 (20131016.1)
MarkForUpload: True
Package: wpasupplicant 1.0-3ubuntu2
PackageArchitecture: amd64
ProcVersionSignature: Ubuntu 3.11.0-13.20-generic 3.11.6
Registers:
 rax            0x7fffaf62ab40    140736135867200
 rbx            0x18    24
 rcx            0x0    0
 rdx            0x3    3
 rsi            0x7ffffffd    2147483645
 rdi            0x7fffaf62ab98    140736135867288
 rbp            0x7fcc4c32dbb0    0x7fcc4c32dbb0
 rsp            0x7fffaf62ab20    0x7fffaf62ab20
 r8             0x7fffaf62aba3    140736135867299
 r9             0x7fcc4b99e134    140515418431796
 r10            0x0    0
 r11            0x275793e    41253182
 r12            0x25    37
 r13            0x2    2
 r14            0x0    0
 r15            0x7fcc4c32dbc0    140515428457408
 rip            0x4b1880    0x4b1880
 eflags         0x10212    [ AF IF RF ]
 cs             0x33    51
 ss             0x2b    43
 ds             0x0    0
 es             0x0    0
 fs             0x0    0
 gs             0x0    0
SegvAnalysis:
 Segfault happened at: 0x4b1880:    mov    (%r12),%rbx
 PC (0x004b1880) ok
 source "(%r12)" (0x00000025) not located in a known VMA region (needed readable region)!
 destination "%rbx" ok
SegvReason: reading NULL VMA
SourcePackage: wpa
Stacktrace:
 #0  0x00000000004b1880 in ?? ()
 No symbol table info available.
 #1  0x00000000004148c9 in ?? ()
 No symbol table info available.
 #2  0x0000000000433f07 in ?? ()
 No symbol table info available.
 #3  0x000000000042cac2 in ?? ()
 No symbol table info available.
 #4  0x00000000004d0891 in ?? ()
 No symbol table info available.
 #5  0x00000000004e1409 in ?? ()
 No symbol table info available.
 #6  0x00007fcc4cbba9fa in nl_recvmsgs_report () from /lib/x86_64-linux-gnu/libnl-3.so.200
 No symbol table info available.
 #7  0x00007fcc4cbbad79 in nl_recvmsgs () from /lib/x86_64-linux-gnu/libnl-3.so.200
 No symbol table info available.
 #8  0x00000000004d665c in ?? ()
 No symbol table info available.
 #9  0x0000000000415964 in ?? ()
 No symbol table info available.
 #10 0x000000000041603e in ?? ()
 No symbol table info available.
 #11 0x00000000004cce99 in ?? ()
 No symbol table info available.
 #12 0x000000000040df2d in ?? ()
 No symbol table info available.
 #13 0x00007fcc4b971de5 in __libc_start_main (main=0x40dc20, argc=8, ubp_av=0x7fffaf62bb88, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7fffaf62bb78) at libc-start.c:260
         result = <optimized out>
         unwind_buf = {cancel_jmp_buf = {{jmp_buf = {0, -8515961597007056115, 4251511, 140736135871360, 0, 0, 8515854761950884621, 8523534132167095053}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x4e74e0, 0x7fffaf62bb88}, data = {prev = 0x0, cleanup = 0x0, canceltype = 5141728}}}
         not_first_call = <optimized out>
 #14 0x000000000040dfa0 in ?? ()
 No symbol table info available.
StacktraceAddressSignature: /sbin/wpa_supplicant:11:x86_64:/sbin/wpa_supplicant+b1880:/sbin/wpa_supplicant+148c9:/sbin/wpa_supplicant+33f07:/sbin/wpa_supplicant+2cac2:/sbin/wpa_supplicant+d0891:/sbin/wpa_supplicant+e1409:/lib/x86_64-linux-gnu/libnl-3.so.200.12.1+e9fa:/lib/x86_64-linux-gnu/libnl-3.so.200.12.1+ed79:/sbin/wpa_supplicant+d665c:/sbin/wpa_supplicant+15964:/sbin/wpa_supplicant+1603e:/sbin/wpa_supplicant+cce99:/sbin/wpa_supplicant+df2d:/lib/x86_64-linux-gnu/libc-2.17.so+21de5:/sbin/wpa_supplicant+dfa0
StacktraceTop:
 ?? ()
 ?? ()
 ?? ()
 ?? ()
 ?? ()
Tags:  saucy
ThreadStacktrace:
 .
 Thread 1 (Thread 0x7fcc4cfc4740 (LWP 739)):
 #0  0x00000000004b1880 in ?? ()
 No symbol table info available.
 #1  0x00000000004148c9 in ?? ()
 No symbol table info available.
 #2  0x0000000000433f07 in ?? ()
 No symbol table info available.
 #3  0x000000000042cac2 in ?? ()
 No symbol table info available.
 #4  0x00000000004d0891 in ?? ()
 No symbol table info available.
 #5  0x00000000004e1409 in ?? ()
 No symbol table info available.
 #6  0x00007fcc4cbba9fa in nl_recvmsgs_report () from /lib/x86_64-linux-gnu/libnl-3.so.200
 No symbol table info available.
 #7  0x00007fcc4cbbad79 in nl_recvmsgs () from /lib/x86_64-linux-gnu/libnl-3.so.200
 No symbol table info available.
 #8  0x00000000004d665c in ?? ()
 No symbol table info available.
 #9  0x0000000000415964 in ?? ()
 No symbol table info available.
 #10 0x000000000041603e in ?? ()
 No symbol table info available.
 #11 0x00000000004cce99 in ?? ()
 No symbol table info available.
 #12 0x000000000040df2d in ?? ()
 No symbol table info available.
 #13 0x00007fcc4b971de5 in __libc_start_main (main=0x40dc20, argc=8, ubp_av=0x7fffaf62bb88, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7fffaf62bb78) at libc-start.c:260
         result = <optimized out>
         unwind_buf = {cancel_jmp_buf = {{jmp_buf = {0, -8515961597007056115, 4251511, 140736135871360, 0, 0, 8515854761950884621, 8523534132167095053}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x4e74e0, 0x7fffaf62bb88}, data = {prev = 0x0, cleanup = 0x0, canceltype = 5141728}}}
         not_first_call = <optimized out>
 #14 0x000000000040dfa0 in ?? ()
 No symbol table info available.
Title: wpa_supplicant crashed with SIGSEGV
UpgradeStatus: No upgrade log present (probably fresh install)



```

```
ProblemType: KernelOopsAnnotation: This occured during a previous suspend and prevented it from resuming properly.
Architecture: amd64
Date: Wed Nov 13 14:29:22 2013
DistroRelease: Ubuntu 13.10
ExecutablePath: /usr/share/apport/apportcheckresume
ExecutableTimestamp: 1382617300
Failure: suspend/resume
InterpreterPath: /usr/bin/python3.3
Package: linux-image-3.11.0-13-generic
ProcCmdline: /usr/bin/python3 /usr/share/apport/apportcheckresume
ProcCwd: /
ProcEnviron:
 TERM=linux
 PATH=(custom, no user)
ProcMaps:
 00400000-0071d000 r-xp 00000000 08:05 132055                             /usr/bin/python3.3
 0091c000-0091d000 r--p 0031c000 08:05 132055                             /usr/bin/python3.3
 0091d000-009b6000 rw-p 0031d000 08:05 132055                             /usr/bin/python3.3
 009b6000-009d3000 rw-p 00000000 00:00 0 
 01178000-01415000 rw-p 00000000 00:00 0                                  [heap]
 7fafa384c000-7fafa390c000 rw-p 00000000 00:00 0 
 7fafa390c000-7fafa3921000 r-xp 00000000 08:05 2363258                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fafa3921000-7fafa3b20000 ---p 00015000 08:05 2363258                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fafa3b20000-7fafa3b21000 r--p 00014000 08:05 2363258                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fafa3b21000-7fafa3b22000 rw-p 00015000 08:05 2363258                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fafa3b22000-7fafa3c08000 r-xp 00000000 08:05 139728                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.18
 7fafa3c08000-7fafa3e07000 ---p 000e6000 08:05 139728                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.18
 7fafa3e07000-7fafa3e0f000 r--p 000e5000 08:05 139728                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.18
 7fafa3e0f000-7fafa3e11000 rw-p 000ed000 08:05 139728                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.18
 7fafa3e11000-7fafa3e26000 rw-p 00000000 00:00 0 
 7fafa3e26000-7fafa3f5b000 r-xp 00000000 08:05 138971                     /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7fafa3f5b000-7fafa415b000 ---p 00135000 08:05 138971                     /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7fafa415b000-7fafa415f000 r--p 00135000 08:05 138971                     /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7fafa415f000-7fafa4160000 rw-p 00139000 08:05 138971                     /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7fafa4160000-7fafa4161000 rw-p 00000000 00:00 0 
 7fafa4161000-7fafa41a6000 r-xp 00000000 08:05 138303                     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-x86_64-linux-gnu.so
 7fafa41a6000-7fafa43a5000 ---p 00045000 08:05 138303                     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-x86_64-linux-gnu.so
 7fafa43a5000-7fafa43a7000 r--p 00044000 08:05 138303                     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-x86_64-linux-gnu.so
 7fafa43a7000-7fafa43af000 rw-p 00046000 08:05 138303                     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-x86_64-linux-gnu.so
 7fafa43af000-7fafa43be000 r-xp 00000000 08:05 2363232                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fafa43be000-7fafa45bd000 ---p 0000f000 08:05 2363232                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fafa45bd000-7fafa45be000 r--p 0000e000 08:05 2363232                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fafa45be000-7fafa45bf000 rw-p 0000f000 08:05 2363232                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fafa45bf000-7fafa45c2000 r-xp 00000000 08:05 394943                     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-x86_64-linux-gnu.so
 7fafa45c2000-7fafa47c1000 ---p 00003000 08:05 394943                     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-x86_64-linux-gnu.so
 7fafa47c1000-7fafa47c2000 r--p 00002000 08:05 394943                     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-x86_64-linux-gnu.so
 7fafa47c2000-7fafa47c3000 rw-p 00003000 08:05 394943                     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-x86_64-linux-gnu.so
 7fafa47c3000-7fafa4883000 rw-p 00000000 00:00 0 
 7fafa4883000-7fafa48d7000 r-xp 00000000 08:05 2363364                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fafa48d7000-7fafa4ad7000 ---p 00054000 08:05 2363364                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fafa4ad7000-7fafa4ada000 r--p 00054000 08:05 2363364                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fafa4ada000-7fafa4ae0000 rw-p 00057000 08:05 2363364                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fafa4ae0000-7fafa4ae1000 rw-p 00000000 00:00 0 
 7fafa4ae1000-7fafa4af1000 r-xp 00000000 08:05 394966                     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-x86_64-linux-gnu.so
 7fafa4af1000-7fafa4cf0000 ---p 00010000 08:05 394966                     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-x86_64-linux-gnu.so
 7fafa4cf0000-7fafa4cf1000 r--p 0000f000 08:05 394966                     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-x86_64-linux-gnu.so
 7fafa4cf1000-7fafa4cf4000 rw-p 00010000 08:05 394966                     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-x86_64-linux-gnu.so
 7fafa4cf4000-7fafa4e74000 rw-p 00000000 00:00 0 
 7fafa4e74000-7fafa5026000 r-xp 00000000 08:05 2363243                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fafa5026000-7fafa5226000 ---p 001b2000 08:05 2363243                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fafa5226000-7fafa5241000 r--p 001b2000 08:05 2363243                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fafa5241000-7fafa524c000 rw-p 001cd000 08:05 2363243                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fafa524c000-7fafa5250000 rw-p 00000000 00:00 0 
 7fafa5250000-7fafa5254000 r-xp 00000000 08:05 394959                     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-x86_64-linux-gnu.so
 7fafa5254000-7fafa5453000 ---p 00004000 08:05 394959                     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-x86_64-linux-gnu.so
 7fafa5453000-7fafa5454000 r--p 00003000 08:05 394959                     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-x86_64-linux-gnu.so
 7fafa5454000-7fafa5455000 rw-p 00004000 08:05 394959                     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-x86_64-linux-gnu.so
 7fafa5455000-7fafa5536000 rw-p 00000000 00:00 0 
 7fafa5536000-7fafa5542000 r-xp 00000000 08:05 2363309                    /lib/x86_64-linux-gnu/libnss_files-2.17.so
 7fafa5542000-7fafa5741000 ---p 0000c000 08:05 2363309                    /lib/x86_64-linux-gnu/libnss_files-2.17.so
 7fafa5741000-7fafa5742000 r--p 0000b000 08:05 2363309                    /lib/x86_64-linux-gnu/libnss_files-2.17.so
 7fafa5742000-7fafa5743000 rw-p 0000c000 08:05 2363309                    /lib/x86_64-linux-gnu/libnss_files-2.17.so
 7fafa5743000-7fafa574e000 r-xp 00000000 08:05 2363313                    /lib/x86_64-linux-gnu/libnss_nis-2.17.so
 7fafa574e000-7fafa594d000 ---p 0000b000 08:05 2363313                    /lib/x86_64-linux-gnu/libnss_nis-2.17.so
 7fafa594d000-7fafa594e000 r--p 0000a000 08:05 2363313                    /lib/x86_64-linux-gnu/libnss_nis-2.17.so
 7fafa594e000-7fafa594f000 rw-p 0000b000 08:05 2363313                    /lib/x86_64-linux-gnu/libnss_nis-2.17.so
 7fafa594f000-7fafa5966000 r-xp 00000000 08:05 2363303                    /lib/x86_64-linux-gnu/libnsl-2.17.so
 7fafa5966000-7fafa5b65000 ---p 00017000 08:05 2363303                    /lib/x86_64-linux-gnu/libnsl-2.17.so
 7fafa5b65000-7fafa5b66000 r--p 00016000 08:05 2363303                    /lib/x86_64-linux-gnu/libnsl-2.17.so
 7fafa5b66000-7fafa5b67000 rw-p 00017000 08:05 2363303                    /lib/x86_64-linux-gnu/libnsl-2.17.so
 7fafa5b67000-7fafa5b69000 rw-p 00000000 00:00 0 
 7fafa5b69000-7fafa5b71000 r-xp 00000000 08:05 2363305                    /lib/x86_64-linux-gnu/libnss_compat-2.17.so
 7fafa5b71000-7fafa5d70000 ---p 00008000 08:05 2363305                    /lib/x86_64-linux-gnu/libnss_compat-2.17.so
 7fafa5d70000-7fafa5d71000 r--p 00007000 08:05 2363305                    /lib/x86_64-linux-gnu/libnss_compat-2.17.so
 7fafa5d71000-7fafa5d72000 rw-p 00008000 08:05 2363305                    /lib/x86_64-linux-gnu/libnss_compat-2.17.so
 7fafa5d72000-7fafa5df2000 rw-p 00000000 00:00 0 
 7fafa5df2000-7fafa5ef5000 r-xp 00000000 08:05 2363284                    /lib/x86_64-linux-gnu/libm-2.17.so
 7fafa5ef5000-7fafa60f4000 ---p 00103000 08:05 2363284                    /lib/x86_64-linux-gnu/libm-2.17.so
 7fafa60f4000-7fafa60f5000 r--p 00102000 08:05 2363284                    /lib/x86_64-linux-gnu/libm-2.17.so
 7fafa60f5000-7fafa60f6000 rw-p 00103000 08:05 2363284                    /lib/x86_64-linux-gnu/libm-2.17.so
 7fafa60f6000-7fafa610e000 r-xp 00000000 08:05 2363391                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fafa610e000-7fafa630d000 ---p 00018000 08:05 2363391                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fafa630d000-7fafa630e000 r--p 00017000 08:05 2363391                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fafa630e000-7fafa630f000 rw-p 00018000 08:05 2363391                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fafa630f000-7fafa6336000 r-xp 00000000 08:05 2363253                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7fafa6336000-7fafa6536000 ---p 00027000 08:05 2363253                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7fafa6536000-7fafa6538000 r--p 00027000 08:05 2363253                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7fafa6538000-7fafa6539000 rw-p 00029000 08:05 2363253                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7fafa6539000-7fafa653b000 r-xp 00000000 08:05 2363383                    /lib/x86_64-linux-gnu/libutil-2.17.so
 7fafa653b000-7fafa673a000 ---p 00002000 08:05 2363383                    /lib/x86_64-linux-gnu/libutil-2.17.so
 7fafa673a000-7fafa673b000 r--p 00001000 08:05 2363383                    /lib/x86_64-linux-gnu/libutil-2.17.so
 7fafa673b000-7fafa673c000 rw-p 00002000 08:05 2363383                    /lib/x86_64-linux-gnu/libutil-2.17.so
 7fafa673c000-7fafa673f000 r-xp 00000000 08:05 2363248                    /lib/x86_64-linux-gnu/libdl-2.17.so
 7fafa673f000-7fafa693e000 ---p 00003000 08:05 2363248                    /lib/x86_64-linux-gnu/libdl-2.17.so
 7fafa693e000-7fafa693f000 r--p 00002000 08:05 2363248                    /lib/x86_64-linux-gnu/libdl-2.17.so
 7fafa693f000-7fafa6940000 rw-p 00003000 08:05 2363248                    /lib/x86_64-linux-gnu/libdl-2.17.so
 7fafa6940000-7fafa6afd000 r-xp 00000000 08:05 2363233                    /lib/x86_64-linux-gnu/libc-2.17.so
 7fafa6afd000-7fafa6cfd000 ---p 001bd000 08:05 2363233                    /lib/x86_64-linux-gnu/libc-2.17.so
 7fafa6cfd000-7fafa6d01000 r--p 001bd000 08:05 2363233                    /lib/x86_64-linux-gnu/libc-2.17.so
 7fafa6d01000-7fafa6d03000 rw-p 001c1000 08:05 2363233                    /lib/x86_64-linux-gnu/libc-2.17.so
 7fafa6d03000-7fafa6d08000 rw-p 00000000 00:00 0 
 7fafa6d08000-7fafa6d1f000 r-xp 00000000 08:05 2363348                    /lib/x86_64-linux-gnu/libpthread-2.17.so
 7fafa6d1f000-7fafa6f1f000 ---p 00017000 08:05 2363348                    /lib/x86_64-linux-gnu/libpthread-2.17.so
 7fafa6f1f000-7fafa6f20000 r--p 00017000 08:05 2363348                    /lib/x86_64-linux-gnu/libpthread-2.17.so
 7fafa6f20000-7fafa6f21000 rw-p 00018000 08:05 2363348                    /lib/x86_64-linux-gnu/libpthread-2.17.so
 7fafa6f21000-7fafa6f25000 rw-p 00000000 00:00 0 
 7fafa6f25000-7fafa6f48000 r-xp 00000000 08:05 2363209                    /lib/x86_64-linux-gnu/ld-2.17.so
 7fafa6f73000-7fafa6ff3000 rw-p 00000000 00:00 0 
 7fafa7024000-7fafa7129000 rw-p 00000000 00:00 0 
 7fafa7145000-7fafa7147000 rw-p 00000000 00:00 0 
 7fafa7147000-7fafa7148000 r--p 00022000 08:05 2363209                    /lib/x86_64-linux-gnu/ld-2.17.so
 7fafa7148000-7fafa714a000 rw-p 00023000 08:05 2363209                    /lib/x86_64-linux-gnu/ld-2.17.so
 7fffff2d9000-7fffff2fa000 rw-p 00000000 00:00 0                          [stack]
 7fffff3fd000-7fffff3ff000 r-xp 00000000 00:00 0                          [vdso]
 ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
ProcStatus:
 Name:    apportcheckresu
 State:    R (running)
 Tgid:    951
 Pid:    951
 PPid:    911
 TracerPid:    0
 Uid:    0    0    0    0
 Gid:    0    0    0    0
 FDSize:    64
 Groups:    0 
 VmPeak:       64620 kB
 VmSize:       64620 kB
 VmLck:           0 kB
 VmPin:           0 kB
 VmHWM:       14580 kB
 VmRSS:       14580 kB
 VmData:        9000 kB
 VmStk:         136 kB
 VmExe:        3188 kB
 VmLib:        8276 kB
 VmPTE:         136 kB
 VmSwap:           0 kB
 Threads:    1
 SigQ:    0/46425
 SigPnd:    0000000000000000
 ShdPnd:    0000000000000000
 SigBlk:    0000000000000000
 SigIgn:    0000000001001000
 SigCgt:    0000000180000002
 CapInh:    0000000000000000
 CapPrm:    0000001fffffffff
 CapEff:    0000001fffffffff
 CapBnd:    0000001fffffffff
 Seccomp:    0
 Cpus_allowed:    ff
 Cpus_allowed_list:    0-7
 Mems_allowed:    00000000,00000001
 Mems_allowed_list:    0
 voluntary_ctxt_switches:    47
 nonvoluntary_ctxt_switches:    1
SleepLog:
 Initial commandline parameters: 
 Mon Nov 11 04:42:42 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  1 
 isofs                  39815  1 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  6 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  1 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  3 
 snd                    69141  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  7 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4919212    1043424          0     193212    3558016
 -/+ buffers/cache:    1167984    4794652
 Swap:      6137852       4576    6133276
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 04:42:43 CET 2013: performing suspend
 Mon Nov 11 04:44:36 CET 2013: Awake.
 Mon Nov 11 04:44:36 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 04:44:38 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:06:05 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  3 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  8 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4463032    1499604          0     200604    2920812
 -/+ buffers/cache:    1341616    4621020
 Swap:      6137852       4576    6133276
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:06:05 CET 2013: performing suspend
 Mon Nov 11 06:06:17 CET 2013: Awake.
 Mon Nov 11 06:06:17 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:06:19 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:06:39 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4475648    1486988          0     200972    2925876
 -/+ buffers/cache:    1348800    4613836
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:06:39 CET 2013: performing suspend
 Mon Nov 11 06:06:49 CET 2013: Awake.
 Mon Nov 11 06:06:49 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:06:50 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:07:11 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4505452    1457184          0     201136    2920684
 -/+ buffers/cache:    1383632    4579004
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:07:11 CET 2013: performing suspend
 Mon Nov 11 06:07:21 CET 2013: Awake.
 Mon Nov 11 06:07:21 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:07:23 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:07:43 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4524660    1437976          0     201280    2933248
 -/+ buffers/cache:    1390132    4572504
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:07:43 CET 2013: performing suspend
 Mon Nov 11 06:07:53 CET 2013: Awake.
 Mon Nov 11 06:07:53 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:07:54 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:08:14 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4531532    1431104          0     201460    2935232
 -/+ buffers/cache:    1394840    4567796
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:08:15 CET 2013: performing suspend
 Mon Nov 11 06:08:25 CET 2013: Awake.
 Mon Nov 11 06:08:25 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:08:26 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:08:47 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4535824    1426812          0     201624    2935424
 -/+ buffers/cache:    1398776    4563860
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:08:47 CET 2013: performing suspend
 Mon Nov 11 06:08:58 CET 2013: Awake.
 Mon Nov 11 06:08:58 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:08:59 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:09:20 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4538028    1424608          0     201776    2931660
 -/+ buffers/cache:    1404592    4558044
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:09:20 CET 2013: performing suspend
 Mon Nov 11 06:09:30 CET 2013: Awake.
 Mon Nov 11 06:09:30 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:09:31 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:09:51 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4542132    1420504          0     201904    2931208
 -/+ buffers/cache:    1409020    4553616
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:09:51 CET 2013: performing suspend
 Mon Nov 11 06:10:02 CET 2013: Awake.
 Mon Nov 11 06:10:02 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:10:03 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:10:24 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4552696    1409940          0     202100    2936344
 -/+ buffers/cache:    1414252    4548384
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:10:24 CET 2013: performing suspend
 Mon Nov 11 06:10:34 CET 2013: Awake.
 Mon Nov 11 06:10:34 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:10:35 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:10:56 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4570444    1392192          0     202296    2947140
 -/+ buffers/cache:    1421008    4541628
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:10:56 CET 2013: performing suspend
 Mon Nov 11 06:11:08 CET 2013: Awake.
 Mon Nov 11 06:11:08 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:11:09 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:11:30 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4570080    1392556          0     202500    2958456
 -/+ buffers/cache:    1409124    4553512
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:11:30 CET 2013: performing suspend
 Mon Nov 11 06:11:40 CET 2013: Awake.
 Mon Nov 11 06:11:40 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:11:41 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:12:01 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4589988    1372648          0     202696    2954552
 -/+ buffers/cache:    1432740    4529896
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:12:02 CET 2013: performing suspend
 Mon Nov 11 06:12:11 CET 2013: Awake.
 Mon Nov 11 06:12:11 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:12:12 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:12:33 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4598544    1364092          0     202888    2957588
 -/+ buffers/cache:    1438068    4524568
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:12:34 CET 2013: performing suspend
 Mon Nov 11 06:12:43 CET 2013: Awake.
 Mon Nov 11 06:12:43 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:12:44 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:13:05 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4600908    1361728          0     203032    2958500
 -/+ buffers/cache:    1439376    4523260
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:13:05 CET 2013: performing suspend
 Mon Nov 11 06:13:15 CET 2013: Awake.
 Mon Nov 11 06:13:15 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:13:17 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:13:37 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4572156    1390480          0     203168    2949224
 -/+ buffers/cache:    1419764    4542872
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:13:37 CET 2013: performing suspend
 Mon Nov 11 06:13:48 CET 2013: Awake.
 Mon Nov 11 06:13:48 CET 2013: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0x80 (128)
  APM_level    = 128
 
 /dev/sda:
  setting standby to 36 (3 minutes)
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Mon Nov 11 06:13:49 CET 2013: Finished.
 Initial commandline parameters: 
 Mon Nov 11 06:14:10 CET 2013: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux Aspire 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 nls_utf8               12557  0 
 isofs                  39815  0 
 hid_generic            12548  0 
 usbhid                 53014  0 
 hid                   101512  2 hid_generic,usbhid
 bnep                   19564  2 
 parport_pc             32701  0 
 ppdev                  17671  0 
 rfcomm                 69070  0 
 bluetooth             371874  10 bnep,rfcomm
 x86_pkg_temp_thermal    14162  0 
 intel_powerclamp       14705  0 
 coretemp               13435  0 
 kvm_intel             138538  0 
 kvm                   431315  1 kvm_intel
 binfmt_misc            17468  1 
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13259  0 
 aesni_intel            55624  0 
 aes_x86_64             17131  1 aesni_intel
 lrw                    13257  1 aesni_intel
 gf128mul               14951  1 lrw
 glue_helper            13990  1 aesni_intel
 ablk_helper            13597  1 aesni_intel
 joydev                 17377  0 
 cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 acer_wmi               32522  0 
 sparse_keymap          13948  1 acer_wmi
 uvcvideo               80885  0 
 snd_hda_codec_hdmi     41276  1 
 arc4                   12608  2 
 snd_hda_codec_realtek    51465  1 
 videobuf2_vmalloc      13216  1 uvcvideo
 videobuf2_memops       13362  1 videobuf2_vmalloc
 videobuf2_core         40469  1 uvcvideo
 videodev              133390  2 uvcvideo,videobuf2_core
 ath9k                 151173  0 
 ath9k_common           13859  1 ath9k
 ath9k_hw              444645  2 ath9k_common,ath9k
 ath                    23827  3 ath9k_common,ath9k,ath9k_hw
 mac80211              596969  1 ath9k
 cfg80211              479757  3 ath,ath9k,mac80211
 snd_hda_intel          48171  8 
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 radeon               1402449  2 
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 microcode              23518  0 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 ttm                    83995  1 radeon
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30095  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29433  2 snd_pcm,snd_seq
 i915                  655752  4 
 snd                    69141  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 drm_kms_helper         52651  2 i915,radeon
 drm                   296739  9 ttm,i915,drm_kms_helper,radeon
 i2c_algo_bit           13413  2 i915,radeon
 wmi                    19070  1 acer_wmi
 lpc_ich                21080  0 
 mei_me                 18421  0 
 mei                    77692  1 mei_me
 video                  19318  2 i915,acer_wmi
 psmouse                97626  0 
 serio_raw              13413  0 
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42299  3 lp,ppdev,parport_pc
 ums_realtek            18029  0 
 usb_storage            62062  1 ums_realtek
 ahci                   25819  3 
 libahci                31898  1 ahci
 atl1c                  46056  0 
              total       used       free     shared    buffers     cached
 Mem:       5962636    4576560    1386076          0     203336    2953064
 -/+ buffers/cache:    1420160    4542476
 Swap:      6137852       4572    6133280
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon Nov 11 06:14:11 CET 2013: performing suspend
 
```

---

### Post by coldraven on 2013-11-16
I solved the 13.10 problems by reverting to 12.04. :)
Maybe it is just my particular hardware but 13.10 was just too buggy to get any work done.

---

### Post by valdrin-qunaj on 2013-11-16
> **coldraven said:**
> I solved the 13.10 problems by reverting to 12.04. :)
Maybe it is just my particular hardware but 13.10 was just too buggy to get any work done.
do i have to re-install Ubuntu to downgrade to 12.04 or is there another way to downgrade from 13.10 to 12.04? Also if there is another distro that you would recommend instead of Ubuntu that is more stable and more suitable for development and work?

---

### Post by ian-weisser on 2013-11-16
> **valdrin-qunaj said:**
> OK so i managed to find the crash report but i cannot make much out of it. Also how do i clear the crash reports, since i don't really know which is from which.[/CODE]

The reports have a lot of information...but nobody is born knowing how to read them. It's a learned skill.

Determining which report is from which crash is not difficult - each report's title is descriptive and timestamped.

If you really want to clear them, I suppose you can delete the crash report.
However, do realize that the system is really trying to tell you about important problems.


[QUOTE=valdrin-qunaj;12849301]
ProblemType: CrashArchitecture: amd64
Date: Mon Nov 11 06:06:21 2013
DistroRelease: Ubuntu 13.10
ProcCmdline: /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
[...]
Title: wpa_supplicant crashed with SIGSEGV


That one, for example, is a crash report by wpa_supplicant. That's part of your wireless networking.
When this crash occurred on Nov 11, your wireless network probably dropped.
If this crash report was transmitted to daisy.ubuntu.com, then it automatically opened a bug report with most of the information a developer needs to figure out the problem.

You can, if you wish, go to launchpad.net, look for that generated bug report, and see if a developer has worked the issue yet...and if they have any questions for you.


> **valdrin-qunaj said:**
> 
ProblemType: KernelOopsAnnotation: This occured during a previous suspend and prevented it from resuming properly.
Architecture: amd64
Date: Wed Nov 13 14:29:22 2013
DistroRelease: Ubuntu 13.10
[...]
Package: linux-image-3.11.0-13-generic
ProcCmdline: /usr/bin/python3 /usr/share/apport/apportcheckresume


That one is a kernel crash. Unrecoverable system failure. It occurred while trying to resume from suspend.
This particular report was generated upon reboot, since the crash reporter needs the kernel to function.
Again, if the crash report was transmitted to daisy.ubuntu.com, a new bug report was opened on the issue.

Short of reinstalling 12.04, you can always boot into an older kernel (using GRUB)...or a newer kernel, since -13-generic has since been superseded by -14-generic. Another simple workaround is to avoid using suspend until the bug is fixed.

Lots of Ubuntu volunteers work hard to test each version of Ubuntu before release. They don't have access to your specific hardware or configurations, so they do the best they can. The stability of Ubuntu to most users, measured by the number of crashes reported, has significantly improved over the last couple years (source: [http://errors.ubuntu.com](http://errors.ubuntu.com)). I'm sorry about your experience, but do please understand that most users do not experience the problems you are having.

---

### Post by valdrin-qunaj on 2013-11-16
> **ian-weisser said:**
> [QUOTE=valdrin-qunaj;12849301]OK so i managed to find the crash report but i cannot make much out of it. Also how do i clear the crash reports, since i don't really know which is from which.[/CODE]

The reports have a lot of information...but nobody is born knowing how to read them. It's a learned skill.

Determining which report is from which crash is not difficult - each report's title is descriptive and timestamped.

If you really want to clear them, I suppose you can delete the crash report.
However, do realize that the system is really trying to tell you about important problems.




That one, for example, is a crash report by wpa_supplicant. That's part of your wireless networking.
When this crash occurred on Nov 11, your wireless network probably dropped.
If this crash report was transmitted to daisy.ubuntu.com, then it automatically opened a bug report with most of the information a developer needs to figure out the problem.

You can, if you wish, go to launchpad.net, look for that generated bug report, and see if a developer has worked the issue yet...and if they have any questions for you.




That one is a kernel crash. Unrecoverable system failure. It occurred while trying to resume from suspend.
This particular report was generated upon reboot, since the crash reporter needs the kernel to function.
Again, if the crash report was transmitted to daisy.ubuntu.com, a new bug report was opened on the issue.

Short of reinstalling 12.04, you can always boot into an older kernel (using GRUB)...or a newer kernel, since -13-generic has since been superseded by -14-generic. Another simple workaround is to avoid using suspend until the bug is fixed.

Lots of Ubuntu volunteers work hard to test each version of Ubuntu before release. They don't have access to your specific hardware or configurations, so they do the best they can. The stability of Ubuntu to most users, measured by the number of crashes reported, has significantly improved over the last couple years (source: [http://errors.ubuntu.com](http://errors.ubuntu.com)). I'm sorry about your experience, but do please understand that most users do not experience the problems you are having.
Do you know why i am having these terminal problems? Problems with permission? And what is the difference between matlab and matab& when u type it in the terminal. Why is it that when u close the terminal, matlab will be closed automatically?

---

### Post by ian-weisser on 2013-11-16
> **valdrin-qunaj said:**
> 
Do you know why i am having these terminal problems? Problems with permission? And what is the difference between matlab and matab& when u type it in the terminal. Why is it that when u close the terminal, matlab will be closed automatically?

That's an apparently different issue from those crash reports.
Software doesn't usually go around re-permissioning files and applications. Users tend to be the most common culprit there. Inserting **sudo** (or **gksudo**) into a copy command, for example, may unintentionally change lots of ownerships and permissions. Wander this forum anytime, and you will find a thread started by somebody who did that and broke their data or an application or something they need to fix.

The specific answer to your question is that when you use a terminal to open an application, that application is the * child* of that terminal *parent*. When you close the parent, you orphan the child...and the system stops, closes, and cleans up orphans.

The way to open an application without that happening is to tell the desktop-manager process to open the application for you. That makes the desktop-manager process the parent instead of a terminal window. That's what desktop links do. When you open your file manager and click on an application, the file manager tells the desktop-manager (via dbus) that you want the desktop-manager to run the application on the desktop. 

The character '&' moves an application to the background of the parent terminal...but it's still a child of that terminal.

Did that answer your question?

---

