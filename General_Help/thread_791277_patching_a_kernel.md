---
title: "patching a kernel"
date: 2008-05-12
forum: General Help
---

### Post by Brando569 on 2008-05-12
im trying to compile the 2.6.25 kernel and patch it with the 2.6.25.2 patch and it keeps on giving me permission errors even if i do it via sudo. heres the parts of my script and the errors i get:

```
echo "what kernel version are you using? linux-2.6.what?"
read kernel_version

echo "what patch are you using? patch-2.6.[kernel version].what?"
read patch_version

#copying kernel source and patches
cd /usr/src
sudo rm -rf linux-2.6.$kernel_versions
sudo cp ~/kernel/kernels/linux-2.6.$kernel_version.tar.bz2 /usr/src
sudo cp ~/kernel/patches/patch-2.6.$kernel_version.$patch_version.bz2 /usr/src

#extracting kernel
sudo tar -xvjf linux-2.6.$kernel_version.tar.bz2
sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.$kernel_version linux
cd linux

#patching kernel
sudo bzcat ../patch-2.6.$kernel_version.$patch_version.bz2 | patch -p1

#making kernel
sudo cp /boot/config-`uname -r` .config && sudo make oldconfig
sudo make xconfig
sudo make-kpkg clean
sudo make-kpkg --initrd kernel_image kernel_headers
```

(extracts kernel to /usr/src/)
linux-2.6.25/virt/kvm/kvm_main.c
patching file Makefile
patch: **** Can't rename file /tmp/poQRRPn9 to Makefile : Permission denied
scripts/kconfig/conf -o arch/x86/Kconfig
(other stuff)
.config:3009:warning: trying to assign nonexistent symbol VIDEO_SAA7134_OSS
*
* Linux Kernel Configuration
*
*
* General setup
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [Y/n/?] y
Local version - append to kernel release (LOCALVERSION) []


also how i can i get rid of the text/console based config and do it all via xconfig? it seems to have something to do with this line: 
sudo cp /boot/config-`uname -r` .config && sudo make oldconfig
but i cant pinpoint whats doing it

thanks

---

### Post by sdennie on 2008-05-12
The permission problem is because only one side of the pipe has root permission on the patch.  Instead of:

```

sudo bzcat ../patch-2.6.$kernel_version.$patch_version.bz2 | patch -p1

```

Try:

```

sudo sh -c "bzcat ../patch-2.6.$kernel_version.$patch_version.bz2 | patch -p1"

```

To get rid of the interactive part of the "make oldconfig" you could just force it to take the defaults with this:

```

sudo cp /boot/config-`uname -r` .config && sudo sh -c "make oldconfig < /dev/null"

```

That basically simulates holding down the enter key and accepting the defaults for that part.

---

### Post by Brando569 on 2008-05-12
awesome thanks i'll try it out

---

