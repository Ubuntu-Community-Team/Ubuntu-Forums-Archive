---
title: "Battery no longer recognized after 2.6.20-16 update"
date: 2007-05-28
forum: General Help
---

### Post by wblancqu on 2007-05-28
I'm using Acer Travelmate 4001WLMi. Battery perfectly recognized in 2.6.20-15, but no longer after 2.6.20-16 update. Should I wait for a patch? Or is there an easy workaround. TM4000 comes with Smart battery system. Any help would be appreciated.

Thx in advance

---

### Post by Kobalt on 2007-05-28
Can you post the output of ```
acpi -V
```

---

### Post by wblancqu on 2007-05-29
In 2.6.20-15:
```
Battery 1: charging, 63%, 01:14:00 until charged
Thermal 1: ok, 35.0 degrees C
AC Adapter 1: on-line
```

In 2.6.20-16:
```
Thermal 1: ok, 43.0 degrees C
```

Output of: dmesg | grep DSDT (2.6.20-16)
```
[    0.000000] ACPI: DSDT (v001 ACER   Kestrel  0x20021012 MSFT 0x0100000e) @ 0x00000000
[    7.858766] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
```

Any ideas?

---

### Post by wblancqu on 2007-05-29
You can ignore last piece, same output is in 2.6.20-15:

```
[    0.000000] ACPI: DSDT (v001 ACER   Kestrel  0x20021012 MSFT 0x0100000e) @ 0x00000000
[    8.286217] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
```

---

### Post by wblancqu on 2007-05-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Someone committed similar problem with toshiba battery to launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773")

---

### Post by spoilerhead on 2007-06-15
i posted a working solution, plaese confirm if it works for you, too

---

### Post by Freiburg05 on 2007-06-18
Hi!, confirmed! the solution you posted in launchpad worked for me too. Thanks!

---

### Post by spoilerhead on 2007-06-21
it just seems that noone of the kernel maintainers cares.... :(

so a lot of people are without working battery support for 3 weeks now ....

---

### Post by wblancqu on 2007-06-21
Your solution worked for me too. Thanks a lot! Indeed not much of the maintainers seem to care, but what the heck, battery support is working again thanks to your dirty little fix ;):D

---

### Post by spoilerhead on 2007-06-22
it isn't even a "dirty little fix" (well it is if you just copy the module :D) but the patch file i provided simple reverses the patch that broke it, not much voodoo in there.

and yes it helps, but i imagine that there are quite some people out there who just lack the knowledge to fix it on their laptops, and its certainly a regression :-/

---

### Post by iZmu on 2007-06-22
sorry i must be really stupid. How do i get the patch to work?

when i do 
diff -uprN 16/drivers/acpi/i2c_ec.c 15/drivers/acpi/i2c_ec.c

i get this output
diff: 16/drivers/acpi/i2c_ec.c: No such file or directory
diff: 15/drivers/acpi/i2c_ec.c: No such file or directory

can anyone please help me?

---

### Post by spoilerhead on 2007-06-22
thats how you create the patch

you need the kernel source tree

sudo apt-get install linux-source.
then you ahve a linux-source-2.6.20.tar.bz2  in /usr/src

extract it then go into that directory

cat patchfile | patch -p1

and the source tree is patched.


see [https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29]("https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29")

---

### Post by tgoose on 2007-06-24
So without recompiling the kernel I have to use the old kernel for my battery to be recognised? Oh well...

---

### Post by Freiburg05 on 2007-06-27
You can use the "dirty little fix" and just copy the module (15/drivers/acpi/i2c_ec.ko) from the 15 kernel to the 16. It works without recompiling the kernel.

---

### Post by tgoose on 2007-06-30
Oh OK, that's not so bad. Thanks!

---

### Post by jdavros on 2007-06-30
Thanks spoilerhead i've been looking for this fix for a long time :D

---

### Post by spoilerhead on 2007-07-03
still no reaction from the kernel team.... :frown:

---

### Post by bmartin on 2007-07-27
I tried the dirty little fix. It didn't do anything for me. I copied from 2.6.20-15 to 2.6.20-16. The output of acpi -V remained the same:
```
No support for device type: thermal
```
I'm not very keen on recompiling my kernel. I just got this laptop yesterday (Acer Aspire 5050-3785). Is this a different problem?

---

### Post by hayim on 2007-07-30
help!!

I have a similar (?) problem, but worse. My battery is ACTUALLY NOT DETECTED by the kernel!

> hayim@hayimtop:~$ acpi -V
     Thermal 1: ok, 58.0 degrees C


> hayim@hayimtop:~$ cat /proc/acpi/battery/*/state
cat: /proc/acpi/battery/*/state: No such file or directory


>  dmesg|grep acpi
[    4.512000] Time: acpi_pm clocksource has been installed.
[   66.396000] acpi_ec_hc_add: Uninitialized device parent.
[   76.856000] ibm_acpi: ec object not found
[   76.936000] pcc_acpi: loading...
[   77.160000] ACPI Exception (acpi_processor-0235): AE_NOT_FOUND, Evaluating _PSS [20060707]


any ideas?? It works fine, shutsdowns, sleeps, it even dims the screen when i unplug it from AC! But it doesnt *see* the battery.. anywhere

[Although, seems to be running a little hot.. is that coz acpi isnt working properly??]

---

### Post by B-Con on 2007-08-02
Your problem is the same as everyone else's here. None of our kernels detected the battery. Follow the solution [here](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773/comments/15) and you'll be fine.


Just for the stats, I had the same problem and that solution worked for me too. Just another positive testamonial.

---

### Post by saj0577 on 2007-08-22
I know this may sound silly but can someone give me a list of instructions of what to type in the terminal to replace kernel/drivers/acpi/i2c_ec.ko with the one from the -15 kernel.

If someone could do this i would be very grateful and im sure many other people would be as well.

Saj

---

### Post by LittleLebowski on 2007-09-01
I tried copying the patch to /usr/src and the running cat nameofpatch | patch -p1 but that didn't work.  What am  doing wrong?

---

### Post by bmartin on 2007-09-01
I'm trying to fix this problem in the 2.6.22 kernel and there isn't even an i2c_ec.c file to patch. Copying the kernel module over doesn't solve the problem. I've tried fixing the DSDT for my laptop, too. No matter what I do, the battery isn't detected.

---

### Post by LittleLebowski on 2007-09-08
Will someone describe the patching process here?  Please?

---

### Post by B-Con on 2007-09-09
IIRC, all that's required is:

```

$ cd /lib/modules
$ cp 2.6.20-16-generic/kernel/drivers/acpi/i2c_ec.ko ~/Desktop/i2c_ec.ko.backup #Backup
$ sudo cp  2.6.20-15-generic/kernel/drivers/acpi/i2c_ec.ko  2.6.20-16-generic/kernel/drivers/acpi/
$ modprobe i2c_ec.ko

```

---

