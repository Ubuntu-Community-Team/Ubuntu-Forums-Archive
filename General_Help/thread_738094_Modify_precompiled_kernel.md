---
title: "Modify precompiled kernel"
date: 2008-03-28
forum: General Help
---

### Post by bozzochet on 2008-03-28
Hello,
I'm trying to recompile the pre compiled kernel.
I make:

```
cd /usr/src/
sudo apt-get source linux-image-2.6.22.14-generic
cd linux-source-2.6.22-2.6.22
sudo debuild (or sudo debuild -ai386 -b -B for avoiding many .deb that I don't need)
```

And I have the .deb with the linux-image with all the patch and the configuration of the precompiled one, besides of some other packages...

If, instead, I try to make:

```
sudo make xconfig
```

also not changing anything in the configuration (obviously my purpose would be changing something, but I'm making it only to try) when I  compile with debuild I have:

```

...
scripts/kconfig/conf -s arch/i386/Kconfig
  Using /usr/src/linux-source-2.6.22-2.6.22 as source for kernel
  /usr/src/linux-source-2.6.22-2.6.22 is not clean, please run 'make mrproper'
  in the '/usr/src/linux-source-2.6.22-2.6.22' directory.
make[2]: *** [prepare3] Error 1
make[1]: *** [prepare] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.22-2.6.22'
make: *** [/usr/src/linux-source-2.6.22-2.6.22/debian/stamps/stamp-prepare-386] Error 2
debuild: fatal error at line 1247:
debian/rules build failed

```

Also if after `xconfig' I do an:

```

sudo make clean

```

Anyone can say to me where's my problem/error?
Thanks

---

### Post by danwood76 on 2008-03-28
You do need to run the make clean before you build.
That error is saying that you havent.

do this:
```

cd linux-source-2.6.22-2.6.22
sudo make clean
sudo debuild

```
though I have never used debuild to make the kernel, I normally use make-kpkg.
heres a guide that looks pretty good for kernel compilation:
[http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile](http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_compile)

what are you exactly trying to modify?

-- edit --

Just had a thought maybe debuild has a clean option you need to run?

---

### Post by bozzochet on 2008-03-28
Yes, I made also `make clean' but with no difference. I tried also `debuild clean' that is a valid command but however with no success...

I use debuild because is the `standard' way used by manteiners, infact in the source downloaded dir there's a `debian' directory that is the `sign' of the use of debuild...

At the beginning I want only to change the HIGHMEM support in the .config but then I would like to optimize kernel for my computer. The idea is to re-compile the precompiled one kernel for having a .deb package that appear like an upgrade with respect to `standard' precompiled one and so with all the `contour' packages (ubuntu_modules, restricted_modules, backports_modules, ecc..) working...

In the past I tried with make-kpkg (with the method in your link) but I had some problem with the modules produced and I have big package with respect to the precompiled one...
In fact I had this error on installation:

```

Mi preparo a sostituire linux-image-2.6.22-14-server 2.6.22-14.46 (con .../linux-image-2.6.22-14-server_2.6.22-14.51.mactel1_i386.deb) ...
Ok, aborting, since modules for this image already exist.
dpkg: errore processando ../linux-image-2.6.22-14-server_2.6.22-14.51.mactel1_i386.deb (--install):

I translate the parts in Italian:

[COLOR="Red"]I prepare myself to substitute[/COLOR] linux-image-2.6.22-14-server 2.6.22-14.46 ([COLOR="Red"]with[/COLOR] .../linux-image-2.6.22-14-server_2.6.22-14.51.mactel1_i386.deb) ...
Ok, aborting, since modules for this image already exist.
dpkg:[COLOR="Red"] error processing[/COLOR] ../linux-image-2.6.22-14-server_2.6.22-14.51.mactel1_i386.deb (--install):

```

I asked about this problems to the mantainer (Chris Irwin) of the precompiled that I'm using, the mactel one (ppa.launchpad mactel), that has some patch that are indispensable for my MacBook, and his answer was:
> 
I actually use `debuild` to build the kernel. You will need `devscripts`
and `fakeroot` installed to utilize this.

sudo &#65279;apt-get install devscripts fakeroot
apt-get source linux-image-2.6.22-14-generic
sudo apt-get build-dep linux-image-2.6.22-14-generic

(cd to the directory it makes, do your changes, apply mactel patches,
etc etc.)

dch -v 2.6.22-14.XX.YY

(dch creates a new changelog entry. This will make your kernel appear
newer than the ubuntu 14.XX. XX is whatever version ubuntu is now using,
YY would be md1 or something to show it is your increment.

debuild

(debuild builds the packages required. -sa includes the source in the
signed changelog, which is useful if you have a repository you will be
putting it in. -S builds source packages only, which is useful if you
want others to build it themselves or if you have a launchpad ppa)

you should now have a whole wack of packages.


---

### Post by NullHead on 2008-03-28
You could always look at the manual.```
man debuild
```

---

### Post by bozzochet on 2008-03-28
For NullHead:
I read the manual of debuild, it's clear! But there's not the reply to my answer!

---

### Post by dcstar on 2008-03-28
> **bozzochet said:**
> Hello,
I'm trying to recompile the pre compiled kernel.
........
Anyone can say to me where's my problem/error?
Thanks

This is the code I use (and is seems to work fine):

```
make xconfig
make-kpkg clean
make-kpkg --rootcmd fakeroot --initrd --append_to_version -custom --revision $(date +'%d%m%y') kernel_image kernel_headers
```

---

### Post by bozzochet on 2008-03-29
Also for me make-kpkg is working... Is when I'm trying to `recreate' the precompiled package for `integrating' with all the related packages that I've problem...

---

### Post by bozzochet on 2008-03-31
There's another way to recompile the precompiled kernel making it to `seem' an upgrade like the manteiners one?

---

### Post by NullHead on 2008-03-31
Well I do it is how it's explained in my guide for creative x-fi sound cards here: [http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656) You can simply not follow the rest of it witch deals with the actual sound card ... Just follow the kernel section changing the 2.6.22-10 kernel for something else.

EDIT: Basically just use these as root. ```
cp /boot/config-`uname -r` ./.config
``````
make menuconfig
``````
make-kpkg clean
make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

---

### Post by bozzochet on 2008-03-31
> In the past I tried with make-kpkg (with the method in your link) but I had some problem with the modules produced and I have big package with respect to the precompiled one...

Sorry,
I KNOW the way your're suggesting to me (make-kpkg bla,bla,bla), but didn't reply my answer: I DON'T WANT TO CREATE A CUSTOM KERNEL FROM THE BEGINNING, I WANT TO MODIFY THE PRECOMPILED ONE!!! With the command you posted here this seems to be not possible.

Simply: I would to know how a mantainer create the upgrade for the kernel package! This is different from knowing how the mantainer made THE FIRST kernel image package...

I hope I'm clear dispite my poor english...

---

### Post by NullHead on 2008-03-31
> **bozzochet said:**
> Sorry,
I KNOW the way your're suggesting to me (make-kpkg bla,bla,bla), but didn't reply my answer: I DON'T WANT TO CREATE A CUSTOM KERNEL FROM THE BEGINNING, I WANT TO MODIFY THE PRECOMPILED ONE!!! With the command you posted here this seems to be not possible.

Simply: I would to know how a mantainer create the upgrade for the kernel package! This is different from knowing how the mantainer made THE FIRST kernel image package...

I hope I'm clear dispite my poor english...

cp /boot/config-`uname -r` ./.config .... then load the alternate config and you have the same settings as the prebuilt kernel and it's essentially the same thing. I don't think its possible to actually "alter" a pre-compiled kernel as you're trying to do.

So if you want the exact same version number and basic kernel settings and drivers just download the kernel from apt sudo apt-get install kernel-source, and run cp /boot/config-`uname -r` ./.config ... witch will copy the config of the kernel you're currently using. Then when you sudo make menu config, simply go to the bottom of the list in the main section and load the .config as the alternate config. 

This will give you the settings, drivers etc... as an exact copy of the default Ubuntu kernel.

---

### Post by bozzochet on 2008-03-31
Sorry... this gives me the same config but not the same patches of the precompiled kernel...

For having the SAME kernel as precompiled is sufficient to do (tested):

```
apt-get source linux-image-XXXXXXXXXX
cd ./linux-source-XXXXXXXXX
sudo debuild
```

I do know if is possible to `manipulate' precompiled kernel but there should be a way, used by manteiners, for make the upgrade that periodically every user of Ubuntu can download and install.
I want only to know this, the way used by manteiners!!!
...because for example I could want to have the changelog of precompiled package in my kernel package, etc...

I think I'm not too clear with my explanation...

Thanks for help...

---

### Post by danwood76 on 2008-04-01
if you use the make-kpkg method on the same source with the same config you get the same kernel out.
It wont be the same as the one the maintainers do but if your doing a custom kernel thats expected.

---

### Post by bozzochet on 2008-04-01
Sorry, if read the third post of this topic you can read that isn't so...
It's probably a quite equivalent kernel but for the system it doesn't appear as an upgrade...

---

### Post by danwood76 on 2008-04-01
You will get the same kernel, just in a binary form as opposed to a .deb (which actually has the binary form in it)

---

### Post by bozzochet on 2008-04-01
I can believe to you, but I have those problems... If I want the SAME EXACTLY NAME of precompiled one I have problem to install it (upgrading the precompiled), beside of the greater dimension...
However I'm sure that manteiners don't make-kpkg, but debuild also because Chris Irwin said to me...
However thanks...

---

### Post by bozzochet on 2008-04-07
I found that the problem of "not clean directory" is with the files in "debian/config/" dir, but without them the "rules" file doesn't find the rules for compile the package.

I look very hard on web for finding how the recompile a package. All the HOWTO I found tell that you can use dh_make (for creating debian/ directory) only one time, but nobody says how to do after making some changes on config (also for not kernel packages) for recompile it!

Thanks.

---

