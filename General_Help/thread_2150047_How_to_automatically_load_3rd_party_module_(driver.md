---
title: "How to automatically load 3rd party module (driver) at boot?"
date: 2013-05-30
forum: General Help
---

### Post by Shellbak3 on 2013-05-30
[TABLE]
[TR]
[TD="class: votecell"]     0     down vote          [favorite]("http://askubuntu.com/questions/299676/how-to-install-3rd-party-module-so-that-it-is-loaded-on-boot#")          
              [/TD]
              [TD="class: postcell"]               Ubuntu 12.04

I have a third party module (driver) to go with a frame grabber we purchased.  I've  downloaded the kernel source, followed the vendor's instructions to  compile it, and have the resulting module, "arvdrv.ko", sitting in a  folder.


  The vendor has supplied a script that loads the module into the  kernel and it works when I run it; the module is loaded  and I can "see" the frame grabber using the vendor's supplied app but the module needs to loaded by hand after each boot. The vendor's script does not use modprobe.


  It appears to me that modprobe maintains a list of many modules.  One  can edit /etc/modules to add a module name and it will load at boot but  the module "arvdrv" is not in modprobe's list.


  My questions are how to let modprobe know of the module?
  Does it need to be copied to a new location and if so where? 
Should I use another technique?

      

[/TD]
[/TR]
[/TABLE]

---

### Post by wildmanne39 on 2013-05-31
Hi, please try:
```
sudo su 
echo arvdrv >> /etc/modules 
exit
```
Thanks

---

### Post by Shellbak3 on 2013-05-31
> **Wild Man said:**
> Hi, please try:
```
sudo su 
echo arvdrv >> /etc/modules 
exit
```
Thanks

This does put the module's name in the file and I think it would work if the module were in modprobe's data base but arvdrv.ko is not in modprobe's database - whatever that is.  I had tried this earlier. 

Thanks

EDIT Heres the installation script.

   >  #!/bin/bash

    module=arvdrv.ko
    device=arvdrv
    mode="666"
    group="root"
    
    # invoke insmod with all arguments we got
    # and use a pathname, as newer modutils don't look in . by default
    /sbin/insmod  $module $* || exit 1

    major=`cat /proc/devices | awk "\\$2==\"$device\" {print \\$1}"`

    echo $major 

    # Remove stale nodes and replace them, then give gid and perms
    # Usually the script is shorter, it's scull that has several devices in it.

    rm -f /dev/${device}[0-3]
    mknod /dev/${device}0 c $major 0
    mknod /dev/${device}1 c $major 1
    mknod /dev/${device}2 c $major 2
    mknod /dev/${device}3 c $major 3
    ln -sf ${device}0 /dev/${device}
    chgrp $group /dev/${device}[0-3]
    chmod $mode  /dev/${device}[0-3]

---

### Post by varunendra on 2013-05-31
> **Shellbak3 said:**
> This does put the module's name in the file and I think it would work if the module were in modprobe's data base but arvdrv.ko is not in modprobe's database - whatever that is.  I had tried this earlier.

The script uses 'insmod' (modprobe executes the same thing, only more smartly). Apart from that, I didn't understand most part of the script. But to make the module recognized by the system, generally it needs the following steps -
[LIST=1]
[*]copy it to the /lib/modules/`uname -r`/kernel/drivers/<suitable section>/ directory
[*]run depmod -a
[*]load the module
[*]update initramfs
[/LIST]

Please show us 'modinfo' of the module. For example, if the "arvdrv.ko" file is on your desktop -
```
modinfo ~/Desktop/arvdrv.ko
```

---

### Post by Shellbak3 on 2013-06-01
The output of modinfo is below.

I copied the results of modinfo below.
I copied arvdrv.ko to the pci section of the kernel modules and ran depmod -a.

I then rebooted and arvdrv is in the kernel but the vendor's demo app fails when I run it so I guess their installation script does something that is required.  I have a help request on another topic with them but they are 9 time zones to the east of me so communications are slow.  I'll start a new one for this unless you have some insight as to the problem.

Thanks

```
filename:       /opt/arvoo/module/arvdrv.ko
license:        GPL
author:         Rini van Zetten, ARVOO Engineering B.V.
srcversion:     2B57C48AE50149AAC5B01A1
alias:          pci:v0000104Cd00009065sv000018C9sd00002032bc*sc*i*
alias:          pci:v0000104Cd00009065sv000018C9sd00002031bc*sc*i*
alias:          pci:v000011ABd00006430sv*sd*bc*sc*i*
alias:          pci:v000011ABd00006430sv000018C9sd0000101Abc*sc*i*
alias:          pci:v000011ABd00006430sv000018C9sd00001019bc*sc*i*
alias:          pci:v000011ABd00006430sv000018C9sd00001018bc*sc*i*
alias:          pci:v000011ABd00006430sv000018C9sd00001017bc*sc*i*
alias:          pci:v000011ABd00006430sv000018C9sd00001014bc*sc*i*
alias:          pci:v000011ABd00006430sv000018C9sd00001013bc*sc*i*
alias:          pci:v000011ABd00006430sv000018C9sd00001012bc*sc*i*
alias:          pci:v000011ABd00006430sv000018C9sd00001011bc*sc*i*
alias:          pci:v000011B0d00000200sv000018C9sd00003011bc*sc*i*
alias:          pci:v00001131d00007146sv000018C9sd00002017bc*sc*i*
alias:          pci:v00001131d00007146sv000018C9sd00002016bc*sc*i*
alias:          pci:v00001131d00007146sv000018C9sd00002015bc*sc*i*
alias:          pci:v00001131d00007146sv000018C9sd00002014bc*sc*i*
alias:          pci:v00001131d00007146sv000018C9sd00002013bc*sc*i*
alias:          pci:v00001131d00007146sv000018C9sd00002012bc*sc*i*
alias:          pci:v00001131d00007146sv000018C9sd00002011bc*sc*i*
alias:          pci:v00001131d00007130sv000018C9sd00002021bc*sc*i*
depends:        
vermagic:       3.2.0-41-generic-pae SMP mod_unload modversions 686 
parm:           arvmodmajor:uint
parm:           debug:uint
parm:           arvdrv_nr_devs:uint
```

---

### Post by varunendra on 2013-06-02
> **Shellbak3 said:**
> I'll start a new one for this unless you have some insight as to the problem.

It seems I 'may' be able to do what the script is doing, but I think it is easier to make the script itself run automatically at startup. Please create a backup copy of the script, then in the original one, comment out the /sbin/insmod.... line (because we no more need to load the module manually). It should now look like -
```
#!/bin/bash

module=arvdrv.ko
device=arvdrv
mode="666"
group="root"

# invoke insmod with all arguments we got
# and use a pathname, as newer modutils don't look in . by default
**[COLOR="#FF0000"]#[/COLOR] /sbin/insmod $module $* || exit 1**

major=`cat /proc/devices | awk "\\$2==\"$device\" {print \\$1}"`

echo $major 

# Remove stale nodes and replace them, then give gid and perms
# Usually the script is shorter, it's scull that has several devices in it.

rm -f /dev/${device}[0-3]
mknod /dev/${device}0 c $major 0
mknod /dev/${device}1 c $major 1
mknod /dev/${device}2 c $major 2
mknod /dev/${device}3 c $major 3
ln -sf ${device}0 /dev/${device}
chgrp $group /dev/${device}[0-3]
chmod $mode /dev/${device}[0-3]
```

Now copy it to your home directory. Then insert "**bash <this script's name with full path>**" in the **/etc/rc.local** file just above the "exit 0" line. Recommended way to do this is to open the file as root -
```
gksu gedit /etc/rc.local
```
then add a line "sleep 10 && bash <path to your script>" just above the "exit 0" line in the file. It should look like (the last 2 lines) -
> sleep 10 && bash /home/<your home>/myscript.sh
exit 0
...assuming the name of the script is "**myscript.sh**" and it resides in your '**Home**' directory.
Proofread, save and close the file.

The "sleep 10" command delays the execution of the script by 10 seconds. That should be enough for the device to get ready. You may increase or decrease this time as suitable.

Try this and let me know if it works as expected. Hopefully, it should.

---

### Post by Shellbak3 on 2013-06-03
It didn't work, alas.  I get the same kind of error when I run the demo program.  It just doesn't find the module ...
I'll start another help thread with the vendor. 

Thanks

---

