---
title: "VirtualBox user - why do I have /usr/lib/vmware?"
date: 2015-03-21
forum: General Help
---

### Post by brendonwp on 2015-03-21
I use VirtualBox and not VMWare, so why do I have almost 500MB under /usr/lib/vmware?  Can I delete it?  I've tried apt-get remove vmware and also looked under synaptic for the package, and had no luck

Thanks!

---

### Post by Holger_Gehrke on 2015-03-21
You can use
```

dpkg-query -S "path and name of a file"

```
to find out what package a file belongs to.

---

### Post by dino99 on 2015-03-21
open 'synaptic' to find the related 'vmware' packages installed, and why they are (dependencies)

---

### Post by ajgreeny on 2015-03-21
I also use VBox a lot but have almost nothing on my Xubuntu 14.04.2 related to vmware, and what I do have seem to be xorg packages and are there simply to satisfy the dependencies of the meta-package, xserver-xorg-input-all.

If you do not use vmware I can not figure out why you have 500MB of files in /lib

---

### Post by brendonwp on 2015-03-21
@Holger: Thanks.  I keep getting "no match found":
[FONT=courier new]e.g. dpkg-query: no path found matching pattern /usr/lib/vmware/modules/binary/bld-3.2.0-23-amd64-generic-Ubuntu12.04/objects/vmci.symvers[/FONT]
[FONT=arial]
[FONT=verdana]@9d9 and @aj: Nothing shows up under synaptic for vmware, apart from mouse and display drivers.[/FONT]
[/FONT]

---

### Post by ajgreeny on 2015-03-21
I suggest you try by renaming the **/usr/lib/vmware** folder that contains those 500MB then see if you can restart and run the computer for an extended period.  If you can they can probably be deleted manually; admittedly not really the best way to deal with this, but other than installing vmware and then uninstalling it properly to see if it takes those lib files/folders with it, I have no idea what else to suggest.

Have you ever in the past installed vmware to perhaps compare it with VBox, and these files are a leftover relic of a bad uninstall?

Just out of interest what output does command **locate -i vmware** give you; with 500MB of files on disk I would expect a very long list of files.

---

### Post by Keith_Helms on 2015-03-21
VMWare is proprietary software and is not in the repositories.  To install it you would have to download it from vmware.com.  What is under /usr/lib/vmware?   If you do ls -l /usr/lib/vmware what is listed?

---

### Post by brendonwp on 2015-03-23
Just checked my menu system and I vmware player comes up :mad:  Do I just rm -r the directory then?

 Here is the output of ls -l:

```
 ls -l  /usr/lib/vmwaretotal 88
drwxr-xr-x  2 root root 4096 Oct  4  2012 bin
-rw-r--r--  1 root root  615 Oct  4  2012 config
drwxr-xr-x  2 root root 4096 Oct  4  2012 configurator
drwxr-xr-x  2 root root 4096 Oct  4  2012 floppies
drwxr-xr-x  3 root root 4096 Oct  4  2012 help
drwxr-xr-x  2 root root 4096 Oct  4  2012 icu
drwxr-xr-x  3 root root 4096 Oct  4  2012 include
drwxr-xr-x  2 root root 4096 Oct  4  2012 isoimages
drwxr-xr-x 88 root root 4096 Oct  4  2012 lib
drwxr-xr-x  4 root root 4096 Oct  4  2012 libconf
drwxr-xr-x  3 root root 4096 Oct  4  2012 licenses
drwxr-xr-x  3 root root 4096 Oct  4  2012 messages
drwxr-xr-x  4 root root 4096 Oct  4  2012 modules
drwxr-xr-x  2 root root 4096 Oct  4  2012 resources
drwxr-xr-x  2 root root 4096 Oct  4  2012 scripts
drwxr-xr-x  2 root root 4096 Oct  4  2012 setup
drwxr-xr-x  5 root root 4096 Oct  4  2012 share
drwxr-xr-x  2 root root 4096 Oct  4  2012 symvers
drwxr-xr-x  2 root root 4096 Oct  4  2012 tools-upgraders
-rw-r--r--  1 root root 1206 Oct  4  2012 vixwrapper-product-config.txt
drwxr-xr-x  2 root root 4096 Oct  4  2012 vnckeymap
drwxr-xr-x  2 root root 4096 Oct  4  2012 xkeymap



```

---

### Post by Keith_Helms on 2015-03-23
It's probably better to let vmware uninstall itself, if possible.  That  way you're less likely to have pieces of it lying around in other  directories.

Try
```
sudo vmware-installer --uninstall-product vmware-player
```

---

### Post by brendonwp on 2015-03-24
@Keith - thanks, this did the trick!

---

### Post by Keith_Helms on 2015-03-24
Cool.  Please mark the thread as solved.

---

