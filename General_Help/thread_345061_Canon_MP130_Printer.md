---
title: "Canon MP130 Printer"
date: 2007-01-23
forum: General Help
---

### Post by topgun553 on 2007-01-23
Can someone please help me get my printer to work with ubuntu 6.06 LTS?

I have been all over doing all sorts of tests and I can't seem to get it to work. Linuxprinting.org doesn't even have my printer listed.
So far the best I have gotten it to do was to print in black and white with the ip1500 driver.

---

### Post by mexlinux on 2007-01-23
You can try Turboprint:
[http://www.turboprint.de/english.html]("http://www.turboprint.de/english.html")

---

### Post by Jedi Penguin on 2007-03-19
No need go to turbo print. The Canon MP130 uses the Canon iP1500 drivers. 
Just install the iP1500 drivers from this forum: 

[http://www.ubuntuforums.org/showthread.php?t=93265](http://www.ubuntuforums.org/showthread.php?t=93265)

The steps are:

edit the source file:** /etc/apt/sources.list**

add this line to the bottom of the source.lst: 
> deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

```
sudo apt-get update
```

```
sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
```

Power on and connect your printer. Then just install the printer with the GUI utility:

System > Administration > Printing, Add Printer, Select from List

Choose the **iP1500** driver for the Canon MP130.

---

### Post by Lucifiel on 2007-04-02
Ooh that's a nice method. However, why is it that when I run "sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj", I always get this?

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bjfilter-2.5: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
  pstocanonbj: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
               Depends: libcupsys2 (>= 1.2.3) but 1.2.2-0ubuntu0.6.06 is to be installed

---

