---
title: "AppArmor is not working."
date: 2013-08-01
forum: General Help
---

### Post by koda2 on 2013-08-01
I uninstalled AppArmor a few days ago and installed SELinux, but I   uninstalled SELinux because I didn't like it, then I decided to go back   to AppArmor.


I did "sudo apt-get apparmor" and it was installed, now when I do "sudo apparmor_status"

it gives me this:

b0x@ubuntu:~$ sudo apparmor_status
apparmor module is loaded.
apparmor filesystem is not mounted.
b0x@ubuntu:~$ 


How do I fix this?

---

### Post by GwL3eNC on 2013-08-01
Hi,

try to install the utils
sudo apt-get install apparmor-utils

Evtl. it's the matter. We can ask the NSA if we cant solve the problem.

---

### Post by koda2 on 2013-08-01
I downloaded apparmor-utils, and I am still getting the error....

---

### Post by koda2 on 2013-08-01
I tried reinstalling AppArmor to see if this solves the problem, but it hits me back with:

 * Starting AppArmor profiles                                                    * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "start" failed.
 * Reloading AppArmor profiles                                                   * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "reload" failed.

---

### Post by koda2 on 2013-08-01
I'll give you a more info on this problem, 
I'm using ubuntu 13.04 32bit. I installed the selinux just for test.  After I restarted the computer selinux started at permissive mode. Then I  removed the selinux package. I noticed that when I installed selinux it  automatically removed apparmor. So I tried to reinstall apparmor. But I  failed with this message:

  
[LIST]
[*]Starting AppArmor profiles
[*]AppArmor not available as kernel LSM.                                                                                                                   [fail] invoke-rc.d: initscript apparmor, action "start" failed.
[*]Reloading AppArmor profiles
[*]AppArmor not available as kernel LSM.                                                                                                                   [fail] invoke-rc.d: initscript apparmor, action "reload" failed.
[/LIST]
  What can I do now to get apparmor back? Thanks.

---

### Post by matt_symes on 2013-08-01
Hi

Is this a bare metal installation or a virtualised installation ? If virtualised, what virtualisation software are you using ?

What version of Ubuntu ? what kernel version ?

```
cat /etc/lsb-release
uname -a
```

This may allow us to see if it's a known bug.

EDIT: Looks like we cross posted but if you could still answer the questions above.

Kind regards

---

### Post by koda2 on 2013-08-01
cat /etc/lsb-release shows
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"

while uname -a shows
Linux ubuntu 3.2.0-40-generic [#32]("https://www.varnish-cache.org/trac/ticket/64")-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013 i386 GNU/Linux


I tried called the status of AppArmor, and it shows:


b0x@ubuntu:/etc/apparmor.d$ sudo /etc/init.d/apparmor status
 * AppArmor not available as kernel LSM.
   ...fail!

---

### Post by koda2 on 2013-08-01
Also tried restarting..


b0x@ubuntu:/etc/apparmor.d$ sudo /etc/init.d/apparmor restart
 * Reloading AppArmor profiles                                                   * AppArmor not available as kernel LSM.
                                                                         [fail]

---

### Post by koda2 on 2013-08-01
Another problem:

I am researching on this problem very closely and I checked /proc/cmdline and it shows:

b0x@ubuntu:/etc/apparmor.d$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-48-generic-pae root=UUID=[secret key lol] ro quiet splash security=selinux selinux=1 vt.handoff=7

how do I fix this? I uninstalled SELinux, is there something wrong?

---

### Post by GwL3eNC on 2013-08-01
about the old problem:

[http://manpages.ubuntu.com/manpages/precise/en/man7/apparmor.7.html](http://manpages.ubuntu.com/manpages/precise/en/man7/apparmor.7.html)

there is 

 AppArmor supports the Linux kernel's securityfs filesystem, and makes
       available the list of the profiles currently loaded; to mount the
       filesystem:

               # mount -tsecurityfs securityfs /sys/kernel/security
               $ cat /sys/kernel/security/apparmor/profiles
               /usr/bin/mutt
               /usr/bin/gpg

---

### Post by matt_symes on 2013-08-01
Hi

Please post the output of 

```
cat /etc/default/grub
```

Let's see if those selinux commands have been added to that file.

I take it this is a non virtualised installation.

Kind regards

---

### Post by koda2 on 2013-08-01
I have finally solved this problem, AppArmor is all healthy and working without no problems again!

/proc/cmdline contained:
BOOT_IMAGE=/boot/vmlinuz-3.2.0-4-686-pae
root=UUID=26ada0c0-1165-4098-884d-aafd2220c2c6 ro

Adding "apparmor=1 security=apparmor" to GRUB_CMDLINE_LINUX_DEFAULT in
/etc/default/grub and running "sudo update-grub" and "sudo reboot" fixed this issue.
another fix of this problem is:
$ sudo perl -pi -e 's,GRUB_CMDLINE_LINUX="(.*)"$,GRUB_CMDLINE_LINUX="$1 apparmor=1 security=apparmor",' /etc/default/grub
$ sudo update-grub
$ sudo reboot

regards,
koda2

---

### Post by matt_symes on 2013-08-01
Hi

Looking at my kernel configuration...

```
matthew-S206:/home/matthew % grep -i apparmor /boot/config-3.8.0-27-generic
CONFIG_SECURITY_APPARMOR=y
CONFIG_SECURITY_APPARMOR_BOOTPARAM_VALUE=1
CONFIG_DEFAULT_SECURITY_APPARMOR=y
CONFIG_DEFAULT_SECURITY="apparmor"
matthew-S206:/home/matthew % 

```

...it looks like apparmor should just work as long as you remove the selinux options from /etc/default/grub. 

There should be no need to add the apparmor options as they should run automatically. You can check your kernel for the same options.

Kind regards

---

