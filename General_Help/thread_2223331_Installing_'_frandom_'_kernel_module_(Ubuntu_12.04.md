---
title: "Installing ' frandom ' kernel module (Ubuntu 12.04)"
date: 2014-05-10
forum: General Help
---

### Post by 0ll0 on 2014-05-10
for Ubuntu 8.10 there exists a **closed** thread with same title: [http://ubuntuforums.org/showthread.php?t=1076959](http://ubuntuforums.org/showthread.php?t=1076959)

here are the slightly different INSTALL instructions for frandom [http://www.billauer.co.il/frandom.html](http://www.billauer.co.il/frandom.html) for Ubuntu 12.04:

after unarchiving the frandom-tarball, # cd to the frandom directory and type 'make'

(all following comands need sudo)
```
install -m 644 frandom.ko /lib/modules/`uname -r`/misc
depmod -a
insmod frandom.ko             # previously this line was 'insmod frandom' which results in "insmod: can't read 'frandom': No such file or directory"

rm /dev/frandom                 # (remove it since this file existed eventhough I had no frandom installed previously) o/w file exists error in next command 
mknod /dev/frandom c 235 11
chmod 444 /dev/frandom

rm /dev/erandom                 # (remove it since this file existed  eventhough I had no frandom installed previously) o/w file exists error  in next command 
mknod /dev/erandom c 235 12
chmod 444 /dev/erandom

nano /etc/modprobe.d/aliases        
# (file will be created since it doesn't exist under U 12.04 and add the line "alias char-major-235 frandom" (without quotes))

nano /etc/rc.local
# and add the line "/sbin/modprobe frandom"  (without quotes)

```

I didn't need to reboot to run the frandom-test-script:

```
./test.sh 
Running tests... This may take up to a minute
Test finished successfully. See frandom-res.txt for results
x@x-E5520:~/Downloads/frandom/frandom-1.1$ more frandom-res.txt
Results of frandom vs. urandom test:
====================================

Sat May 10 17:48:42 CEST 2014

urandom created 22945 kBytes of data
frandom created 229450 kBytes of data

Note that frandom did 10 times as much data!

head --bytes=229450k /dev/frandom > /dev/null

real    0m0.912s
user    0m0.012s
sys    0m0.896s

head --bytes=22945k /dev/urandom > /dev/null

real    0m2.394s
user    0m0.000s
sys    0m2.392s

Platform info:
Linux 3.2.0-61-generic-pae
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
stepping    : 7
microcode    : 0x15
cpu MHz        : 800.000
cache size    : 3072 KB
...
```

***
but after reboot I get

dd if=/dev/frandom of=/dev/sdb2 bs=1M
  dd: opening `/dev/frandom': No such file or directory

modprobe frandom
 WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
 FATAL: Module frandom not found.

I fix this temporarily (I rarely reboot ;) with

cd ~/Downloads/frandom/frandom-1.1
insmod frandom.ko  

then /dev/frandom is known again.

any suggestions on where to put the above mentioned lines "alias char-major-235 frandom" and  "/sbin/modprobe frandom" ?
***

p.s.: I found frandom when I read about [http://sudoeric.com/2011/09/installing-encrypted-arch-linux/](http://sudoeric.com/2011/09/installing-encrypted-arch-linux/)
the pa[FONT=arial]ge rec[/FONT]ommends to write over the entire harddrive with randomized data before encrypting it.

since even 
dd if=/dev/urandom of=/dev/HARDDRIVE
[FONT=arial]is much too slow for bigger drives, I found frandom, which is sadly is not contained in the U 12.04 kernel. it should!
[/FONT]

---

