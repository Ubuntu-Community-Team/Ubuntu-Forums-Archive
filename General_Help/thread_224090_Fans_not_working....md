---
title: "Fans not working..."
date: 2006-07-27
forum: General Help
---

### Post by DeShark on 2006-07-27
Once again my lap is scolding with the heat of my laptop. Why? Well I don't think that the fans have ever turned on since I installed Dapper a few weeks ago. Why it's never worried me before is a question I can't answer but I'm after a quick fix to turn the fans on full blast before my laptop completely melts or before it slows down to a standstill... I'm using a Sony VAIO VGN-A115M. At the moment I don't mind if the fans are on full blast 24/7 just as long as it cools down. I'll look for a more permanent fix once the noise begins to annoy me. Until then... do you have any ideas?

---

### Post by DeShark on 2006-07-27
This is actually worrying me quite a bit... When I run acpi -t I get this...

```
dan@ubuntu:~$ acpi -t
     Battery 1: charging, 95%, 00:49:53 until charged
     Thermal 1: ok, 98.0 degrees C
```

Does that actually mean that my processor is at 98 degrees C? That's a wee bit hot for my comfort... If anyone has *any* ideas... I'm about to install Windows just to save my laptop's life. I'd rather not do that tbh...

---

### Post by philippe_carlo on 2006-07-27
I think most processors have a critical temp between 80 and 90 degrees C. So you're very right to be worried. I'm surprised your BIOS is allowing this to happen. It should just shut down your laptop in order to prevent damage!

Note that there exists a Sony ACPI module for the kernel, maybe you need to load that one? In the mean while, you can use a (normal) fan and direct it to your laptop for minimum cooling.

---

### Post by DeShark on 2006-07-27
Will I have to do anything once I've loaded the module? I loaded sony_acpi... but still no life in my fans. Should I add it to some sort of startup file and restart and see if that does anything? If so... which one?

---

### Post by rebelfallen on 2006-07-27
I am having the same issue so here is a bump.

---

### Post by philippe_carlo on 2006-07-27
Maybe [this]("http://juljas.net/linux/vaiofx240/#acpi") applies to you too? What kernel do you use?

---

### Post by philippe_carlo on 2006-07-27
Actually, what does THE FOLLOWING say?
```

sudo apt-get install acpitool
acpitool -f

```
and what does this say:
```

cat /proc/acpi/sony/fan

```

Also check this:
```

lsmod | grep fan

```
If the last returns nothing, try
```

sudo modprobe fan

```

---

### Post by DeShark on 2006-07-27
```
dan@ubuntu:~$ uname -a
Linux ubuntu 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux
dan@ubuntu:~$ acpitool -f
  Fan            : <not available>
dan@ubuntu:~$ cat /proc/acpi/sony/fan
cat: /proc/acpi/sony/fan: No such file or directory
```

Thanks for your help so far. This is driving me crazy as I can't find anything anywhere online...

---

### Post by philippe_carlo on 2006-07-27
Check my previous message again, I edited it with more instructions. Maybe the fan module just isn't loaded.

---

### Post by DeShark on 2006-07-27
Unfortunately the fan module is loaded...

```
dan@ubuntu:~$ lsmod | grep fan
fan                     4868  0

```

---

### Post by philippe_carlo on 2006-07-27
Darned! Seems like the sony module is screwed up. I think it is supposed to make the  /proc/acpi/sony/fan file. Looking further ...

---

### Post by gesho on 2006-07-27
is there some log file for fans? to see the record whether they've been working or not?

---

### Post by philippe_carlo on 2006-07-27
Just making sure: you do run Dapper with the latest kernel?

---

### Post by DeShark on 2006-07-27
> **philippe_carlo said:**
> Just making sure: you do run Dapper with the latest kernel?

Indeed I do... At least I think 2.6.15-26 is the latest. I've thought about recompiling it, but I'd reeeeally rather not (I've had little success in the past and it's a pretty grueling process to say the least).

---

### Post by philippe_carlo on 2006-07-27
You may want to try and run
```

apt-get install vaiostat-source

```

Next, go to the usr/src directory. Untar 'vaiostat.tar.gz'. Try to compile and load the module. It may work, and it may not. Only one way to find out. You will need to install the kernel headers and development stuff:
```

sudo apt-get install build-essential
sudo apt-get install linux-kernel-headers

```

---

### Post by DeShark on 2006-07-27
> **philippe_carlo said:**
> You may want to try and run
```

apt-get install vaiostat-source

```

Next, go to the usr/src directory. Untar 'vaiostat.tar.gz'. Try to compile and load the module. It may work, and it may not. Only one way to find out. You will need to install the kernel headers and development stuff:
```

sudo apt-get install build-essential
sudo apt-get install linux-kernel-headers

```

I extracted the gz file and entered the dir... read the README which said I should run "make" and then "make install" as root. So I run make and...

```
dan@ubuntu:/usr/src/modules/vaiostat$ make
rm -f build-stamp
[ -x /bin/test ] || plususr=/usr ; \
        $plususr/bin/test -w /include/config || \
                plus='-o include/config/MARKER' ; \
        make -C  SUBDIRS=/usr/src/modules/vaiostat $plus modules
make: *** SUBDIRS=/usr/src/modules/vaiostat: No such file or directory.  Stop.
make: *** [build-stamp] Error 2

```
...it tells me that the directory that I'm working in does not exist.. Don't you love computers :p (P.S. I also tried to run make using sudo... to no avail).

On the plus side, acpi tells me that it's now only 68 degrees inside...

---

### Post by philippe_carlo on 2006-07-27
68 is still pretty hot. Very funny thing we have there happening, let me try this myself (on a Thinkpad, should be interesting).

UPDATE: no good, got same error and messy stuff from compiler when compiling manually. 

Last resort: turning off acpi entirely. Add the following kernel parameters to grub in /boot/grub/menu.lst: noacpi acpi=off
```

...
kernel          /boot/vmlinuz-2.6.15-26-686 noacpi acpi=off
...

```

---

### Post by DeShark on 2006-07-30
Hmm... no luck. Disabling acpi didn't seem to change anything at all I'm afraid. I'm really stuck with this one. It used to work in Fedora I think but I can't stand Rpms... :(

Edit: Actually... disabling acpi did do something... it stopped me from altering the brightness of my screen. This is such a pain. Why can't things just work? sigh...

---

### Post by DeShark on 2006-07-31
Anyone have any ideas please?

---

### Post by DeShark on 2006-08-23
I *still* haven't resolved this problem I'm afraid. Anyone at all have any ideas? Please.

---

### Post by Evil Genius on 2006-11-23
Hi, 

About the problem compiling:

export KSRC=/usr/src/linux 
(Or the directory where you have uncompressed the kernel sources)

then you can compile with "make" or "fakeroot make".

---

