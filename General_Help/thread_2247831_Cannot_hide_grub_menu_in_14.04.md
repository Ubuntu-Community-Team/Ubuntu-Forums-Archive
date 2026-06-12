---
title: "Cannot hide grub menu in 14.04"
date: 2014-10-10
forum: General Help
---

### Post by koelsch on 2014-10-10
Installed 14.04 with full disk encryption, no dual-boot (only ubuntu 14.04), three kernels are on the system (the newest is 3.13.0-37.64), and I cannot hide the grub boot menu. After the initial install, it worked fine, but since first update and upgrade it shows the grub menu and I cannot hide the grub menu anymore. 

The following actions did NOT result in getting rid of the problem: 

(1) 
making the folling changes in /etc/default/grub 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0.0
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""
(same for GRUB_TIMEOUT=0.0) 
and adding 
GRUB_DISABLE_OS_PROBER="true"
(following, e.g., this thread: [http://askubuntu.com/questions/469347/how-to-hide-grub-menu-in-ubuntu-14-04](http://askubuntu.com/questions/469347/how-to-hide-grub-menu-in-ubuntu-14-04)) 

(2) 
using 
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
 sudo apt-get update 
sudo apt-get install grub-customizer 
(following, e.g., [http://askubuntu.com/questions/117525/hide-grub2-menu-unless-you-hold-down-shift-key-how-to-make-this-happen](http://askubuntu.com/questions/117525/hide-grub2-menu-unless-you-hold-down-shift-key-how-to-make-this-happen)) 

(3) 
make the following changes in /etc/grub.d/10_linux 
replace 
list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
with 
# Get the current kernel version: kernelvers=`uname -r` # Remove the local version and architecture: kernelvers=${kernelvers%%-?*} list=`for i in /boot/vmlinuz$kernelvers-* ; do
(folling this thread: [http://www.linuxplanet.com/linuxplanet/tutorials/6991/1](http://www.linuxplanet.com/linuxplanet/tutorials/6991/1)) 

(4)
change 
quick_boot="1" to quick_boot="0"
in 
/etc/grub.d/30_os_prober
(following this thread: [http://askubuntu.com/questions/469347/how-to-hide-grub-menu-in-ubuntu-14-04](http://askubuntu.com/questions/469347/how-to-hide-grub-menu-in-ubuntu-14-04)) 

(5) 
save the menu style and timeout values before os-prober changes them, and to restore them afterwards by creating two files ([**25_pre-os-prober**]("https://gist.github.com/LeahCim/9332432#file-25_pre-os-prober")                                 
     
and [**35_post-os-prober**) ]("https://gist.github.com/LeahCim/9332432#file-35_post-os-prober")in /etc/grub.d 
(following this thread: [https://gist.github.com/LeahCim/9332432](https://gist.github.com/LeahCim/9332432)) 

(6) 
An attempt to downgrade grub to the last non-beta version was not successful. 

Ah, and yes: I did not forget to 
sudo update-grub

WHAT's WRONG HERE? 
Is it a bug of the beta-version of grub 2.02 that comes with 14.04? (really clever by the devlopers to not provide an option to downgrade, so that their work really has an impact on how others spend their time!) 
OR does it have to do with the full disk encryption? 

I am OUT OF IDEAS now, PLEASE HELP!!!

---

### Post by Dennis N on 2014-10-10
I have used this set up to hide the menu, but there is a catch.

The relevant part of /etc/default/grub:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

This has a 5 sec (visible) countdown - press ESC key within that 5 seconds, the menu appears; press nothing and the default OS boots (no grub menu seen). OS_PROBER has to be disabled. If OS_PROBER detects another OS, and GRUB_TIMEOUT=0, it inserts a stanza into grub.cfg setting the timeout back to 10. So, I created and used a custom menu entry to dual-boot my other OS (that is the catch).

I have no idea what the role of encryption plays here. Never have used it.

---

### Post by koelsch on 2014-10-13
Hi Dennis, thanks for the reply! Unfortunately no luck, have made your changes, but the boot menu still appears, no countdown shows, and even after about 1 min nothing happens.

I have edited my post and speficied that I do not use a dual boot (i.e., I only have ubuntu 14.04 on my thinkpad x1 carbon). 

Moreover, I have specified that after the initial install, it worked fine, but since the first update and upgrade it shows the grub menu and I cannot hide the grub menu anymore.

I have copied /etc/default/grub and /etc/grub.d from a dell latitude E5430 with ubuntu 14.04 (same kernel), on which everthing works fine, but on the thinkpad it still shows the menu.

The only differences I can think of are the full disk encryption and the screen resolution (which should probably not matter). 

I think that the grub beta-version is seriously buggy. 

Or does anyone have any other ideas? CHEERS!!

---

### Post by Ulf_Dunkel on 2014-12-11
I use these settings:

GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY=true

---

