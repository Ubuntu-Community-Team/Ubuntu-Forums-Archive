---
title: "problems with Intel 915GM on Dell Latitude D610"
date: 2005-04-07
forum: General Help
---

### Post by edoardo on 2005-04-07
Hallo 
my new laptop Dell Latitude D610 comes with an Intel 915GM graphic chipset.

I'd use it either with the internal screen 1400x1050 or with an external Dell montiro 2001FP (1600x1200).

The problem I found is that the chipset is not properly supported under ubuntu's xorg.
Intel has drivers in the form but not for a debian distro.   

with the default driver "i810" the internal panel works only at 1280x1050 and I can't get it to 1400x1050.

with the external monitor, the "i810" driver gets me only at 640x480 and to use 1600x1200 I have to sue the very poorly performing "vesa" driver.

I tried googling but with no luck.

Hints anyone ?

---

### Post by edoardo on 2005-04-07
attached X logs on starting up with i810 and vesa drivers, with internal and external monitors

---

### Post by cdhotfire on 2005-04-07
Have you tried converting the rpm into deb?
If not then download the rpm
[ftp://aiedownload.intel.com/df-support/8211/eng/dri-i915-v1.1-20041217.i386.rpm]("ftp://aiedownload.intel.com/df-support/8211/eng/dri-i915-v1.1-20041217.i386.rpm")
then:
```

$ cd /where ever u put it/

```
then
```

$ sudo alien dri-i915-v1.1-20041217.i386.rpm

```
should make a file called dri-i915_v1.1-20041218_i386.deb, then
```

$ sudo dpkg -i dri-i915_v1.1-20041218_i386.deb

```
should install the package.

Hope this works. Let me know how it works out, have never tried it.:???:

---

### Post by Darrena on 2005-04-07
This link talks about getting 1280x800 working on my 700m, the procedure is probably very similar to get your custom resolution working:

[http://www.celifornia.com/documents/dell700m.html](http://www.celifornia.com/documents/dell700m.html)

---

### Post by edoardo on 2005-04-08
[QUOTE=cdhotfire]Have you tried converting the rpm into deb?
If not then download the rpm
[ftp://aiedownload.intel.com/df-support/8211/eng/dri-i915-v1.1-20041217.i386.rpm]("ftp://aiedownload.intel.com/df-support/8211/eng/dri-i915-v1.1-20041217.i386.rpm")
then:
```

$ cd /where ever u put it/

```
then
```

$ sudo alien dri-i915-v1.1-20041217.i386.rpm

```
should make a file called dri-i915_v1.1-20041218_i386.deb, then
```

$ sudo dpkg -i dri-i915_v1.1-20041218_i386.deb

```
should install the package.

Hope this works. Let me know how it works out, have never tried it.:???:[/QUOTE]
 I tried alien (I knew about it as I've used it in the past to try set up the ATI rpms on mepis using another laptop). 
It only installs the tgz containing the drivers to be compiled. 
extracting the tgz and running the install script fails because the system seem not to be set up for compiling modules ... here's the log 

make -C /lib/modules/2.6.10/build SUBDIRS=/mnt/sda5/SHARED/downloads/intel/dripkg/agpgart-2.0 modules
make: *** /lib/modules/2.6.10/build: No such file or directory.  Stop.
make: *** [default] Error 2
Makefile.linux:151: *** Cannot find a kernel config file.  Stop.

---

### Post by edoardo on 2005-04-08
[QUOTE=Darrena]This link talks about getting 1280x800 working on my 700m, the procedure is probably very similar to get your custom resolution working:

[http://www.celifornia.com/documents/dell700m.html](http://www.celifornia.com/documents/dell700m.html)[/QUOTE]
 Darrena, thanks for the suggestion.
I tried the script and ... suprise my bios does not list a 1400x1050 mode
(output below) 

root@4[855resolution]# ./855resolution -l
855resolution version 0.3, by Alain Poirier

Chipset: Unknown (0x25908086)
VBIOS type: 2
VBIOS Version: 3412

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 60 : 400x772, 8 bits/pixel
Mode 61 : 400x772, 16 bits/pixel
Mode 62 : 400x772, 32 bits/pixel
Mode 63 : 512x771, 8 bits/pixel
Mode 64 : 512x771, 16 bits/pixel
Mode 65 : 512x771, 32 bits/pixel
Mode 66 : 400x772, 8 bits/pixel
Mode 67 : 400x772, 16 bits/pixel
Mode 68 : 400x772, 32 bits/pixel

---

### Post by edoardo on 2005-04-08
BTW, I already checked that I have the latest bios according to the Dell ebsite,
and for sure in windows resolutions are perfect :(

---

### Post by cdhotfire on 2005-04-09
what was the problem with the alien?

i tried converting and worked fined, then trying installing it also went fine.:-?

---

### Post by edoardo on 2005-04-09
[QUOTE=cdhotfire]what was the problem with the alien?

i tried converting and worked fined, then trying installing it also went fine.:-?[/QUOTE]
the problem was not with alein itself, alien worked fine for me this time as well as the last time with ati,
the problem was that the package only contains the drivers to be compiled and compilation fails for me :( :(
debian spoiled me and I'm used to install binaries, I'd need someone to package the intel binary drivers on some deb (non-free) repository :) :)

---

### Post by cdhotfire on 2005-04-09
```
sudo alien dri-i915-v1.1-20041217.i386.rpm
```

what does this give u?

---

### Post by stomljen on 2005-04-16
855resolution has been ported to th 915GM chipset:

[http://www.geocities.com/stomljen](http://www.geocities.com/stomljen)

---

### Post by edoardo on 2005-04-18
[QUOTE=stomljen]855resolution has been ported to th 915GM chipset:

[http://www.geocities.com/stomljen](http://www.geocities.com/stomljen)[/QUOTE]


thanks will try that!

---

### Post by shakin on 2005-04-18
[QUOTE=edoardo]thanks will try that![/QUOTE]

It worked for me and I wrote a how-to about the whole thing. Note that I have an i915 card in my desktop, but it's the same chip as yours and the how-to should work for you as well.

[HOW TO: Configuring Xorg for use with Intel i810 and higher video cards](http://www.ubuntuforums.org/showthread.php?t=27029&highlight=i810)

---

### Post by edoardo on 2005-04-19
Stomljen, that was great!

root@3[915resolution]# ./915resolution -l
Intel 915GM VBIOS Hack : version 0.1

Chipset: 915GM

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
...

I chose to overwrite the (for me) unused mode 3c
setting it to 1400 x 1050
and I now can use my Dell 610 internal LCD at its native resolution!
this works using the VESA driver in both Ubuntu 5.04 and Mepis 3.3

kool.
now for my next step is to be able to use the i810 driver to get better performance. but for now at least office and development work is good.

cheers

---

