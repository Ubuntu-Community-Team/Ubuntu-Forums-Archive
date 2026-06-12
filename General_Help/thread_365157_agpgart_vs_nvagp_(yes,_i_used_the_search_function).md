---
title: "agpgart vs nvagp (yes, i used the search function)"
date: 2007-02-19
forum: General Help
---

### Post by NvAGP on 2007-02-19
Hi there, Im running xubuntu and I am quite happy with it. Now Ive installed latest nvidia drivers and try to use nvagp instead of agpgart because that gave me more performance with my old ubuntu system where that worked without any problems.

Now Ive done the following to stop agpgart from loading and use nvagp

[LIST]
[*]I blacklisted agpgart & nvidia_agp in /etc/modprobe.d/blacklist and blacklist-agp (as some other forumuser suggested in a different thread)
[/LIST]

So lsmod shows me amonst others
[LIST]
[*]nvidia               6830868  22 
[*]agpgart                34888  1 nvidia
[/LIST]
which pretty much shows nvidia driver still uses agpgart.

Yes, Ive configured the xorg.conf to load the nvagp instead with 

Section "Device"
    Identifier     "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Driver         "nvidia"
    Option         "NvAGP" "1"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
EndSection

Im pretty much clueless now of what to try next. Any ideas are really welcome and appreciated. Thanks.

Edit: Oh, I am using this edgy release 6.10 I think. while using 2.6.17-11-generic kernel, if that might help a bit.

---

### Post by yabbadabbadont on 2007-02-19
Actually, I think that the agpgart module gets loaded even though NvAGP is being used.  The only way to tell for sure would be to check your /var/log/Xorg.0.log and ```
/home/bubba $ cat /proc/driver/nvidia/agp/status 
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

```

---

### Post by NvAGP on 2007-02-19
well, in my simple world there is a driver loaded for agp which is agpgart because its shown with lsmod. but if agpgart is loaded how should nvagp be loaded?

---

### Post by yabbadabbadont on 2007-02-19
Run: cat /proc/driver/nvidia/agp/status 

If "Driver:" doesn't say AGPGART, then it is using NvAGP.

---

### Post by thom_raindog on 2007-06-01
Hmm...
my Feisty System does not HAVE that folder. All I have is
/proc/driver/nvidia
which contains the folders /cards and /warning.

Is that supposed to be this way? I use the package nvidia-glx.

---

### Post by yabbadabbadont on 2007-06-01
> **thom_raindog said:**
> Hmm...
my Feisty System does not HAVE that folder. All I have is
/proc/driver/nvidia
which contains the folders /cards and /warning.

Is that supposed to be this way? I use the package nvidia-glx.

You have to be running x-windows when you check it.  You also have to have changed your /etc/X11/xorg.conf to use the nvidia drvier and not the OSS nv driver.  (either manually changed it or using "sudo nvidia-glx-config enable")

```
/proc/driver/nvidia/agp $ cat *
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x 
Registers:       0x1f000217:0x1f000314
Host Bridge:     PCI device 1106:3189
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x 
Registers:       0x1f000217:0x1f000314
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Enabled
/proc/driver/nvidia/agp $ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"

```

---

### Post by thom_raindog on 2007-06-03
I AM running KDE right now (using FF to write this) and I use the nvidia-driver according to xorg.conf.
Still no luck with the /agp thing

---

### Post by yabbadabbadont on 2007-06-03
Do you have the NvAGP option set to 1 in your /etc/X11/xorg.conf?  If so, did you blacklist the agpgart kernel module so that it is not loaded automagically at boot?  You have to do that so that it only gets loaded when the nvidia kernel module pulls it in.  Otherwise agpgart will be used and not nvidia.  You will need to add an entry to the /etc/modprob.d/blacklist file for it and then reboot.
```
/home/daffy $ grep -i nvagp /etc/X11/xorg.conf 
        Option          "NvAGP"         "1"
/home/daffy $ grep agpgart /etc/modprobe.d/blacklist
blacklist agpgart

```

---

### Post by thom_raindog on 2007-06-05
Yes and yes...
None of which impressed my PC in anyway.

According to
```
cat /proc/driver/nvidia/registry
```

my NvAGP is still 3 and my performance is below par.

---

### Post by asymmetric on 2007-06-09
> **NvAGP said:**
> well, in my simple world there is a driver loaded for agp which is agpgart because its shown with lsmod. but if agpgart is loaded how should nvagp be loaded?

if you tipe

```
modinfo nvidia
```

you'll see that the nvidia module depends on agpgart, so i guess it has to be opened anyway ([color=red]thanks [mlalkaka](http://ubuntuforums.org/showpost.php?p=1356397&postcount=11) [/color])

---

### Post by thom_raindog on 2007-06-11
and... how does 
/proc/driver/nvidia/registry
fit in there? It would seem that no matter what you do, it always shows the same (not only in regards to NvAGP btw).

---

### Post by asymmetric on 2007-06-12
you're right on that, even here "cat /proc/driver/nvidia/registry" returns NvAGP : 3

but "cat /proc/driver/nvidia/agp/status" returns
Status:          Enabled
Driver:          NVIDIA

so.. i'm kinda clueless :)

---

### Post by thom_raindog on 2007-06-13
Which does not help me either, seeing that I dont have /proc/driver/nvidia/AGP... (caps used for dramatization)

---

### Post by yabbadabbadont on 2007-06-13
Just out of curiosity, what is your "lspci" output?

---

### Post by thom_raindog on 2007-06-14
lookie here:
[http://www.ubuntuusers.de/paste/11736/]("http://www.ubuntuusers.de/paste/11736/")

---

### Post by yabbadabbadont on 2007-06-15
I don't see an AGP controller listed there anywhere...  just PCI-E.  I would guess that the nvidia driver's built in AGP doesn't support the chipset used by your motherboard.  Check on the nvidia website to see if they have any support/knowledgebase information about your MB/Chipset.

---

### Post by thom_raindog on 2007-06-15
I do indeed use a PCI-E Version of the 7600GT.. do I need to change something to make that really work? I will search for an answer myself, but if you could point me in some direction that would be great...

---

### Post by yabbadabbadont on 2007-06-15
> **thom_raindog said:**
> I do indeed use a PCI-E Version of the 7600GT.. do I need to change something to make that really work? I will search for an answer myself, but if you could point me in some direction that would be great...

It is a PCI-E video card......  not AGP.  AGP settings are meaningless to your card.  :D

---

### Post by thom_raindog on 2007-06-16
Hmm.. so....
I have no way to put things into xorg.conf to tweak the performance?
Can you point me to some file or website where I can read more on nvidia and pci-e?

---

### Post by Rui Pais on 2007-06-16
> **thom_raindog said:**
> Hmm.. so....
I have no way to put things into xorg.conf to tweak the performance?
Can you point me to some file or website where I can read more on nvidia and pci-e?

Hi,
you could edit your xorg.conf and add a line to Section "Device"  (of nvidia you have more then one) with:
```
Option "Coolbits" "1"
```

then when you run nvidia-settings you will have extra options to tweak performance card. 
** USE WITH CARE!! **

---

### Post by thom_raindog on 2007-06-18
Well, that one I knew about, but it's not really what I was looking for.
That's leaning towards overclocking, which I am not planning on doing :)

---

