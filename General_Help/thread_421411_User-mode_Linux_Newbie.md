---
title: "User-mode Linux Newbie"
date: 2007-04-24
forum: General Help
---

### Post by regularfry on 2007-04-24
Hi there,

I figure someone out there must have seen this before.  I'm trying to get a Debian Etch UML image running on Dapper (Kubuntu, if that's relevant).  I've created and debootstrapped a disk image, and used that to apt-get linux-source-2.6.18 to provide the kernel source.  Then, following this sequence:

```
make mrproper ARCH=um
make modules ARCH=um
make xconfig ARCH=um # don't change anything here, just save
make linux ARCH=um
sudo make modules_install INSTALL_MOD_PATH=`pwd`/mountpoint ARCH=um
sudo umount mountpoint
```

I then run this:

```
./linux mem=64 ubd0=`pwd`/images/etch/base.img
```

and this happens:

```
Checking that ptrace can change system call numbers...OK
Checking syscall emulation patch for ptrace...OK
Checking advanced syscall emulation patch for ptrace...OK
Checking for tmpfs mount on /dev/shm...OK
Checking PROT_EXEC mmap in /dev/shm/...OK
Checking for the skas3 patch in the host:
  - /proc/mm...not found
  - PTRACE_FAULTINFO...not found
  - PTRACE_LDT...not found
UML running in SKAS0 mode
Mapping memory: Cannot allocate memory
```

And the process terminates.  Has anyone seen this before?  What have I forgotten?  Google doesn't help with this one.

---

### Post by bwhite82 on 2007-04-24
I don't really understand what you're trying to do here, but I thought I'd drop a note anyways. Did you check to see if "mm" was in "/proc"? Because it isn't in that directory for me.

---

### Post by regularfry on 2007-04-25
As far as I can tell, that's not the problem.  /proc/mm will only exist if the host kernel has the right patch (the skas3 patch, to be precise), and my compiled guest kernel has successfully detected that it doesn't, so it's fallen back to skas0 mode, as it should.  The only status line that looks unusual compared to other reports I've seen on the web is the last:
```
Mapping memory: Cannot allocate memory
```
That's the fatal error, and I've got no idea what's causing it.  I'm running this on a box with 1G of RAM and 2G swap, so spinning an extra 64M for a VM really shouldn't be an issue.

---

### Post by regularfry on 2007-04-27
For the record, I was exceptionally dim.  The command line should be:

```
./linux mem=64M ubd0=`pwd`/images/etch/base.img
```

Note the 'M' in the mem parameter.  With that it seems to work.

---

