---
title: "vmware problems"
date: 2007-01-10
forum: General Help
---

### Post by twonole on 2007-01-10
could someone help me install vmware this is what i'm getting


[QUOTE]twonole@Margret-M-1:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Setup is unable to find the "gcc" program on your machine.  Please make sure it
is installed.  Do you want to specify the location of this program by hand?
[yes]

What is the location of the "gcc" program on your machine?
[QUOTE]

---

### Post by hikaricore on 2007-01-10
Have you installed: build-essential ?

```
sudo aptitude install build-essential
```

This should take care of the gcc problem.  :)

---

### Post by twonole on 2007-01-10
it's just not installing anything and going into vmware setup
:confused: :mad: ](*,)

---

### Post by 0xDEFACE on 2007-01-10
try install linux headers:
```

$ sudo apt-get install linux-headers-`uname -r`
```

it must to help you.

After installing, run vmware-config.pl again, kernel modul vmmon have to compile successfully...

GL!

---

