---
title: "[SOLVED] C header files missing!!!"
date: 2007-07-23
forum: General Help
---

### Post by upthelum on 2007-07-23
Trying to install vmware on xubuntu server. 

root@ubuntu-desktop:~# /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]


** (process:16680): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:16680): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:16686): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:16686): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

It gets as far as this and now i dont know how to procede. Is this a default location it expects to find the files and how can i find/install them?
Thanks...

---

### Post by tszanon on 2007-07-23
If i recall correctly, you must install a package called linux-headers-xxxxxxxxx that matches your running kernel. Something like this:
kernel 2.6.20-amd64 ==> linux-headers-2.6.20-amd64

---

### Post by stchman on 2007-07-23
> **upthelum said:**
> Trying to install vmware on xubuntu server. 

root@ubuntu-desktop:~# /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]


** (process:16680): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:16680): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:16686): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:16686): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

It gets as far as this and now i dont know how to procede. Is this a default location it expects to find the files and how can i find/install them?
Thanks...

In order to compile C/C++ programs using Ubuntu you need to have the build-essential package installed.

sudo apt-get -y install build-essential

The build-essential package contains all the C/C++ header files.

---

### Post by dfreer on 2007-07-23
Do you have build-essential installed?
```
sudo apt-get install build-essential
```
You may also need to install the linux kernel headers (since vmware has to compile modules). This may help you out:
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

EDIT: wow, I'm slow ;) but this command should take care of both suggestions:
```
sudo apt-get install linux-headers-`uname -r` build-essential
```
The uname -r just echo's the current kernel version number, making things easier. Make sure you copy+paste that code, those aren't apostrophes!

---

### Post by upthelum on 2007-07-23
Hey dfreer thanks for the tip about the fake apostrophes, is that the little symbol below Esc?
It worked a treat and i now have a working vmware console in Linux.

Just goes to show it's worth the effort...

---

### Post by dfreer on 2007-07-23
> **upthelum said:**
> Hey dfreer thanks for the tip about the fake apostrophes, is that the little symbol below Esc?
It worked a treat and i now have a working vmware console in Linux.

Just goes to show it's worth the effort...

Yep, that's it! Glad you got it working!

---

### Post by sagarj on 2007-07-31
Thanks..it works

---

### Post by bmccorm2 on 2008-03-02
That worked for me too.  Thanks!!

---

