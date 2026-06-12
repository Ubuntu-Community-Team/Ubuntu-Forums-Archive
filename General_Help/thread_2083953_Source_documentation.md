---
title: "Source documentation?"
date: 2012-11-14
forum: General Help
---

### Post by markling on 2012-11-14
Linux reference documents often ask the reader to refer to 'Documentation', usually with a path like 'Documentation/Such-and-such'.

But I can never find the files I'm told I should refer to.

E.g. the O'Reilly book - Linux Device Drivers - says one of the first things you should do before doing anything it says in the book is refer to 'Documentation/Changes'. But I can't find any such file.

Where do I find this Documentation?

---

### Post by codemaniac on 2012-11-14
> **markling said:**
> Linux reference documents often ask the reader to refer to 'Documentation', usually with a path like 'Documentation/Such-and-such'.

But I can never find the files I'm told I should refer to.

E.g. the O'Reilly book - Linux Device Drivers - says one of the first things you should do before doing anything it says in the book is refer to 'Documentation/Changes'. But I can't find any such file.

Where do I find this Documentation?

For almost every utility or application that is shipped with Linux or any *nix flavor ,has an documentation .
A man page (short for manual page) is online software documentation, serving as content for the man system, for an entity typically encountered in Unix or a Unix-like operating system.

see 
```
man man
```

---

### Post by raja.genupula on 2012-11-14
Every packages will have its Documentation or Manual if its really necessary and if not they will put enough information in README file as I know .

---

### Post by bab1 on 2012-11-14
> **markling said:**
> Linux reference documents often ask the reader to refer to 'Documentation', usually with a path like 'Documentation/Such-and-such'.

But I can never find the files I'm told I should refer to.

E.g. the O'Reilly book - Linux Device Drivers - says one of the first things you should do before doing anything it says in the book is refer to 'Documentation/Changes'. But I can't find any such file.

Where do I find this Documentation?
If you are looking for the changes from one version to another in Ubuntu then you should search for that specific package [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://packages.ubuntu.com/"). Each package has a change log link to the latest documetation.

If you are looking at specific drivers or apps that are not packaged in .deb format you should look for the driver changelog included in the download (tar.gz).

---

### Post by markling on 2012-11-14
Thank you for your suggestions.

The information I'm looking for is not in the man pages, Codemaniac.

I'm not looking for documentation for a specific package, Raja. I'm looking for local documentation in directories where text books say I should find it.

And while the example I gave above does suggest I'm looking for changes, Bab1, I'm looking for a single file listing all changes that I have been told I can find in a particular place. I suspect doing what the text book tells me - to look up all changes - would take to long if I did as you suggest and seek them all out individually. Plus I wouldn't know what I was looking for, or when I had checked all I needed to check, or where to find it.

---

### Post by markling on 2012-11-14
To recap.

I'm looking for Documentation that text books say I should be there. But I can't find it.

Linux journal says:

[INDENT]The file Documentation/devices.txt in the kernel source tree lists all of the official device numbers, including all the minor numbers for the misc driver.

[http://www.linuxjournal.com/article/2920](http://www.linuxjournal.com/article/2920)[/INDENT]

But I can't find this directory.

I can find a Documentation directory in the following location: /usr/src/linux-headers-2.6.35-22/Documentation

This location has many subdirectories, but no actual documentation files, and certainly no file called devices.txt. In fact I can't find a file called devices.txt anywhere.

Similarly, The Linux Documentation Project refers to a location called linux/Documentation/kbuild/modules.txt in its section on compiling kernel modules. It says you should read this file before going further:

[INDENT]2.2. Compiling Kernel Modules

To learn more on how to compile modules which are not part of the official kernel (such as all the examples you'll find in this guide), see file linux/Documentation/kbuild/modules.txt

..
Additional details about Makefiles for kernel modules are available in linux/Documentation/kbuild/makefiles.txt. Be sure to read this and the related files before starting to hack Makefiles. It'll probably save you lots of work.

[http://www.tldp.org/LDP/lkmpg/2.6/html/x181.html](http://www.tldp.org/LDP/lkmpg/2.6/html/x181.html)
[/INDENT]

But I can't find it.

The beginning of the O'Reilly book 'Linux Device Drivers' refers the reader to Documentation/devices.txt before going any further:

[INDENT]3.2.3. Dynamic Allocation of Major Numbers

Some major device numbers are statically assigned to the most common devices. A list of those devices can be found in Documentation/devices.txt within the kernel source tree.

[http://www.makelinux.net/ldd3/chp-3-sect-2](http://www.makelinux.net/ldd3/chp-3-sect-2)
[/INDENT]

But the file isn't there.

Elsewhere, documenation on the driver for the Intel Hardware Random Number Generator refers the reader to Documentation/hw_random.txt:
 
[INDENT]CONFIG_HW_RANDOM: Intel/AMD/VIA HW Random Number Generator support

To compile this driver as a module, choose M here: the module will be called rng-core. This provides a device that's usually called /dev/hw_random, and which exposes one of possibly several hardware random number generators.

These hardware random number generators do not feed directly into the kernel's random number generator. That is usually handled by the "rngd" daemon. Documentation/hw_random.txt has more information.

[http://cateee.net/lkddb/web-lkddb/HW_RANDOM.html](http://cateee.net/lkddb/web-lkddb/HW_RANDOM.html)
[/INDENT]

This file isn't there either, though it is recommended in other places as well, e.g.:

[INDENT]Hardware Random Number Generator (RNG) configuration

These hardware random number generators do not feed directly
  17          into the kernel's random number generator.  That is usually
  18          handled by the "rngd" daemon.  Documentation/hw_random.txt
  19          has more information.

[http://lxr.linux.no/linux/drivers/char/hw_random/Kconfig](http://lxr.linux.no/linux/drivers/char/hw_random/Kconfig)
[/INDENT]

My local Documentation directory appears to contain a lot of Makefiles. I thought perhaps I could get them to turn into documentation if I sprinkled magic water on them or something.

But I can't even learn how to deal with them because the man page for 'make' says to look in another place that doesn't appear to be there:

[INDENT]This  man  page  is an extract of the documentation of GNU make.  It is
       updated only occasionally, because the GNU project does not use  nroff.
       For  complete,  current documentation, refer to the Info file make.info
       which is made from the Texinfo source file make.texi.
[/INDENT]

I have found online source that corresponds closely with the references:

[http://lxr.linux.no/linux+v2.6.35.3/Documentation/](http://lxr.linux.no/linux+v2.6.35.3/Documentation/)

But this is for version v2.6.35.3. I'm on version v2.6.35.32. Seeing as the kernel reference I was reading was pretty specific about the differences that can occure between different versions and making sure you are up to date with the right ones, I can't trust this source. Neither does it have the Documentation files I'm looking for. And I would prefer not to have to rely on online documentation. If its local, I would like to see it.

Is there something else I need to do to see, or open or install these missing documentation files?

---

### Post by Cheesemill on 2012-11-14
Have you actually downloaded the kernel source? In your first example above you are looking in the kernel headers source, not the kernel source.

The full source for your current kernel can be downloaded simply by running
```
apt-get source linux-image-`uname -r`
```This will download an archive containing the kernel source into the current working directory.

---

### Post by markling on 2012-11-14
Thank you, Cheesemill. This looks the ticket.

---

