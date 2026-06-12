---
title: "Kernel upgrade from 4.4.0-24 to 4.4.0-24.43 failed along with dpkg"
date: 2016-06-09
forum: General Help
---

### Post by expatver on 2016-06-09
Checked earlier this evening for upgrades on 16.04 using  Synaptic.  A new kernel appeared 4.4.0-24.43 along with the normal accompanying header files and so forth.  Stock repos. I accepted the upgrade, it downloaded but when it was running the postinst for the kernel it hung. Waited a half hour, then closed Synaptic and rebooted.  On reboot, restarted Synaptic and  ran update again. Got the error message "you must run sudo dpkg --configure -a".  Ran it. dpkg hung on several errors in various files.  Finally force closed dpkg. Rebooted.  Machine boots fine. Synaptic, in history does NOT show the attempted  update. Synaptic also does not  reveal  the 4.4.0-24.43 update as being available  when run again. Uname reveals

uname -a
Linux xxxx-All-Series 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

 First time using Synaptic, I have had the update process hang.  

sudo apt-get update then  sudo apt-get install yields

```
sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcompfaceg1 libetpan17 libpisock9 linux-headers-4.4.0-21
  linux-headers-4.4.0-21-generic linux-image-4.4.0-21-generic
  linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-4.4.0-24-generic (4.4.0-24.43) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-24-generic
vmlinuz(/boot/vmlinuz-4.4.0-24-generic
) points to /boot/vmlinuz-4.4.0-24-generic
 (/boot/vmlinuz-4.4.0-24-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-24-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
```

where it hangs again. 

Any suggestions on what I should do next would be deeply appreciated.

Regards

expat

---

### Post by ventrical on 2016-06-10
Interesting.

 This may not help but I always use:

```

sudo apt-get  dist-upgrade

```

Regards..

---

### Post by expatver on 2016-06-10
Ventrical

Thanks for the suggestion, unfortunately  when I still had a choice of commands it might have helped. 

Where we are now. Decided to try to remove the package

sudo apt-get purge linux-image-4.4.0-24-generic
[sudo] password for : 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


So looks like we are back where we started from

Anyone?

---

### Post by deadflowr on 2016-06-10
Did you run the suggested command: "sudo dpkg --configure -a"?

---

### Post by expatver on 2016-06-10
hi deadflowr
Yes I did. Hangs.

Many thanks

Expat

---

### Post by expatver on 2016-06-10
OK. Solved. 

Resolved my  problem from this thread

[https://askubuntu.com/questions/141370/how-to-fix-a-broken-package-when-apt-get-install-f-does-not-work](https://askubuntu.com/questions/141370/how-to-fix-a-broken-package-when-apt-get-install-f-does-not-work)

I should search  with more detail before posting. Apologies to all on the forum.  This is what worked-

sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get autoremove         this command hung and I had to kill it 
sudo apt-get update

then 
sudo dpkg --remove --force-remove-reinstreq 4.4.0-24-generic

When I executed sudo dpkg --remove, dpkg returned  "did not remove 4.4.0-24-generic package  not installed"

However the machine asked for a reboot after this, all is back to normal. Hope this helps someone else with dpkg hanging.

Note- Always use rm -rf  with care. Typos  will kill you here.

Regards
Expat

---

