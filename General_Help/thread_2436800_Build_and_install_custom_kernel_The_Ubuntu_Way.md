---
title: "Build and install custom kernel The Ubuntu Way"
date: 2020-02-13
forum: General Help
---

### Post by bulkadhesive on 2020-02-13
I'm attempting to compile a custom kernel 'The Ubuntu Way' to produce a kernel that only includes minor changes and remains as close to the official package as possible.  Unfortunately I've run into some problems along the way.

While there are [many]("http://help.ubuntu.com/community/Kernel/Compile") [sources]("http://wiki.ubuntu.com/KernelTeam/KernelMaintenance") [of]("https://help.ubuntu.com/community/Kernel/Compile") [documentation]("https://www.howtoforge.com/kernel_compilation_ubuntu") that describe how this can be achieved, many of them are severely out of date or provide conflicting information.  The most concise instructions that I've had luck with are Mr. Wimpress' ["Kernel Stuff" notes]("https://launchpad.net/~flexiondotorg/+archive/ubuntu/kernel-stuff").

Attempting to follow the instructions verbatim, I've made some modifications to suit my particular situation.  Specifically


[LIST]
[*]To save polluting the host environment (a 19.10 system), all of the build steps are performed inside a 19.10 LXD container; presumably this has no impact the build process.
[*]The 19.10 repository is cloned (`git clone git://kernel.ubuntu.com/ubuntu/ubuntu-eoan.git`) and a local branch is created to explicitly match the current kernel (`git checkout -b noflr Ubuntu-5.3.0-29.31`) before patching the source or updating `debian.master/changelog`.
[*]`+noflr` is appended to the version in `debian.master/changelog` making the first line `linux (5.3.0-29.31+noflr) eoan; urgency=medium`
[/LIST]

After letting `fakeroot debian/rules clean` and `fakeroot debian/rules binary-headers binary-generic` successfully run to completion, I'm left with the following debs in the parent directory

    ```
linux-buildinfo-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
linux-cloud-tools-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
linux-headers-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
linux-headers-5.3.0-29_5.3.0-29.31+noflr_all.deb
linux-image-unsigned-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
linux-modules-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
linux-modules-extra-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
linux-tools-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
```

Pulling the resulting files out of the container back to the host and attempt to install them results in this error

    ```
$ sudo dpkg -i linux-image-unsigned-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
    dpkg: regarding linux-image-unsigned-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb containing linux-image-unsigned-5.3.0-29-generic:
     linux-image-unsigned-5.3.0-29-generic conflicts with linux-image-5.3.0-29-generic
      linux-image-5.3.0-29-generic (version 5.3.0-29.31) is present and installed.


    dpkg: error processing archive linux-image-unsigned-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb (--install):
     conflicting packages - not installing linux-image-unsigned-5.3.0-29-generic
    Errors were encountered while processing:
     linux-image-unsigned-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
```

Contents of the kernel deb for reference

```
$ dpkg -c linux-image-unsigned-5.3.0-29-generic_5.3.0-29.31+noflr_amd64.deb
    drwxr-xr-x root/root         0 2020-02-13 11:22 ./
    drwxr-xr-x root/root         0 2020-02-13 11:15 ./boot/
    -rw------- root/root  11398016 2020-02-13 11:15 ./boot/vmlinuz-5.3.0-29-generic
    drwxr-xr-x root/root         0 2020-02-13 11:22 ./usr/
    drwxr-xr-x root/root         0 2020-02-13 11:15 ./usr/lib/
    drwxr-xr-x root/root         0 2020-02-13 11:15 ./usr/lib/linux/
    drwxr-xr-x root/root         0 2020-02-13 11:15 ./usr/lib/linux/triggers/
    drwxr-xr-x root/root         0 2020-02-13 11:22 ./usr/share/
    drwxr-xr-x root/root         0 2020-02-13 11:22 ./usr/share/doc/
    drwxr-xr-x root/root         0 2020-02-13 11:22 ./usr/share/doc/linux-image-unsigned-5.3.0-29-generic/
    -rw-r--r-- root/root    172703 2020-02-13 10:59 ./usr/share/doc/linux-image-unsigned-5.3.0-29-generic/changelog.Debian.gz
    -rw-r--r-- root/root      1292 2020-02-13 10:59 ./usr/share/doc/linux-image-unsigned-5.3.0-29-generic/copyright
```

Currently installed `linux-image-` packages for reference

    ```
$ apt list --installed |  grep ^linux-image-

    WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

    linux-image-5.3.0-26-generic/eoan-updates,eoan-security,now 5.3.0-26.28 amd64 [installed,automatic]
    linux-image-5.3.0-29-generic/eoan-updates,eoan-security,now 5.3.0-29.31 amd64 [installed,automatic]
    linux-image-generic/eoan-updates,eoan-security,now 5.3.0.29.33 amd64 [installed,automatic]
```


Questions:

[LIST=1]
[*]What is the cause of the package conflict with the existing `linux-image-5.3.0-29-generic` package?
[*]How do I work around it?
[/LIST]

I would expect the additional version information defined in `debian.master/changelog` (`+noflr` in my case) to be picked up by the build scripts and propagated to all of the build artifacts; the resulting deb package file names (which seems to be working) and the files inside the deb packages (which does not seem to be working).  When compiling the mainline kernel, this appears to be achieved with the `LOCALVERSION` or `CONFIG_LOCALVERSION` variables.  Although I haven't tried setting these values, [BuildYourOwnKernel]("https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel") provides this warning

> do not attempt to use CONFIG_LOCALVERSION as this _will_ break the build.

Any help with the matter is greatly appreciated.

---

### Post by leblutch on 2020-03-12
I am also attempting building custom ubuntu kernel and it's effectively a bit a pain..

I am currently trying your way (debian/rules ..) and will report completion..

---

### Post by leblutch on 2020-03-12
failed at the end (installation) with : 

```

SNIP..

./scripts/zfs-tests.sh -c
/bin/bash: ./scripts/zfs-tests.sh: No such file or directory
Makefile:1527: recipe for target 'all-local' failed
make[3]: [all-local] Error 127 (ignored)
make[3]: Leaving directory '<<DKMSDIR>>/build/zfs/0.8.1/build'
make[2]: Leaving directory '<<DKMSDIR>>/build/zfs/0.8.1/build'
make[1]: Leaving directory '<<DKMSDIR>>/build/zfs/0.8.1/build'
II: dkms-build installing zfs into /home/localadmin/ubuntu-bionic/debian/linux-modules-5.3.0-40-generic/lib/modules/5.3.0-40-generic/kernel/zfs
signing zfs.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:72
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:79
sign-file: /home/localadmin/ubuntu-bionic/debian/build/build-generic/certs/signing_key.pem: No such file or directory
debian/rules.d/2-binary-arch.mk:113: recipe for target 'install-generic' failed
make: *** [install-generic] Error 1
localadmin@aberration:~/ubuntu-bionic$ 

```

---

