---
title: "apt update fails - 'std::runtime_error' what(): random_device::__x86_rdrand(void)"
date: 2018-07-31
forum: General Help
---

### Post by m-dw on 2018-07-31
I'm getting the following error when issuing "sudo apt update" on one of three platforms running different flavours of Ubuntu 18.04. This particular one is on an AsRock Rack motherboard C3758D4I-4L running Ubuntu server.


```
 Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [65.4 kB]
 0% [1 InRelease gpgv 69.9 kB] [3 InRelease 7,779 B/65.4 kB  12%[COLOR=#ff0000]]terminate called after throwing an instance of 'std::runtime_error'
   what():  random_device::__x86_rdrand(void)[/COLOR]
 Aborted


```

I get the same error when running the live CD - for example when trying to add the boot-repair PPA. I have to reboot several times to clear the error. 

I see the following in dmesg (note this output is from the last boot where sudo apt update is currently working normally):

```

david@srvbuntu:~$ dmesg | grep random
[    2.474783] random: fast init done
[    2.483815] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.485149] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.486413] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.487738] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.488976] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.490130] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.491339] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.492485] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.493581] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.494733] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    3.092569] random: crng init done

```

Any ideas? Is this a hardware issue? RAM? 

This

---

