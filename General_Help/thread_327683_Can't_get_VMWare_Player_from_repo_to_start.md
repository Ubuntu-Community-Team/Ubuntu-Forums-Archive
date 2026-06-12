---
title: "Can't get VMWare Player from repo to start"
date: 2006-12-29
forum: General Help
---

### Post by derrick1985 on 2006-12-29
Hi, 

I installed VMware player from the multiverse repo and when I try to start it, I get this error:

derrick@derrick-desktop:~$ vmplayer
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(vmplayer:19507): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

(vmplayer:19507): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
derrick@derrick-desktop:~$

Any ideas to get this working?

---

### Post by derrick1985 on 2006-12-30
Anyone?

---

### Post by derrick1985 on 2006-12-31
Please, anyone? I also tried compiling the latest version from source and got the same error.

---

### Post by broughcut on 2007-01-05
I don't know why this is suddenly broke. however:

```
$  sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
$ sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
```

will fix it.

---

### Post by derrick1985 on 2007-01-09
> **broughcut said:**
> I don't know why this is suddenly broke. however:

```
$  sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
$ sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
```

will fix it.

I'm afraid that it didn't fix it. Here is the output

derrick@derrick-desktop:~$ sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0' to `/usr/lib/libpng12.so.0': No such file or directory
derrick@derrick-desktop:~$ sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
derrick@derrick-desktop:~$

Any other ideas?

---

### Post by derrick1985 on 2007-01-09
Ok, I kind got it to work all of a sudden. Running in console and doing it with sudo works, but no 3D accel. It wants GCC 4.2, but only 4.1.2 is installed which I think is what the problem is.

Is Edgy going to get GCC 4.2?

This is what I get running sudo vmplayer

derrick@derrick-desktop:~$ sudo vmplayer
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(vmplayer:30281): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

(vmplayer:30281): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
derrick@derrick-desktop:~$

---

### Post by broughcut on 2007-01-12
> ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0' to `/usr/lib/libpng12.so.0': No such file or directory

sorry, I was using vmwareserver when I posted that... the path is a little different on your machine:

$  sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/**vmware-player**/lib/libpng12.so.0/libpng12.so.0

you may also need to do this, although you appear to have a 'vmware' folder that Player may be using for libgcc_s.so.1:

$ sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/**vmware-player**/lib/libgcc_s.so.1/libgcc_s.so.1

I am very new at this but had probs with Server and Player and the symbolic link fix resolves this issue. I have Edgy with GCC 4.1.2. (Server under Edgy kept asking me to configure the prog after every boot, I couldn't sort it, so moved to Player -- I think I got it from apt-get as well). I don't appear to have a vmware-player folder, it seems to have installed itself over Server....

---

### Post by nasty canasta on 2007-03-07
thanx broughcut,

very helpfull:)

nc

---

