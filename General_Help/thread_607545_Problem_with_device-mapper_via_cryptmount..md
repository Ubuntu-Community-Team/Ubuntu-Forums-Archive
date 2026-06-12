---
title: "Problem with device-mapper via cryptmount."
date: 2007-11-09
forum: General Help
---

### Post by jamesoc on 2007-11-09
Hello. New to Linux, and I'm diggin' it. Just installed Ubuntu 7.10.

Question:
Using cryptmoun in the terminal; just commanded "cryptmount --prepare storage", and this was the reply:
 
enter password for target "storage": 
/proc/misc: No entry for device-mapper found
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
/proc/misc: No entry for device-mapper found
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver 
failed to initialize device-mapper task
device-mapper target-creation failed for "storage"

Anyone offer any suggestions to a newbie?

Thanks!

---

### Post by rwpenney on 2007-11-11
Hello,

Great news that you're enjoying linux!

The problem that you're having with cryptmount is due to a bug in one of the packages installed in your system. (This bug has already been reported to the Ubuntu maintainers, as bug #106696  in the 'devmapper' package).

You can fix the problem fairly easily if you can replace one of the start-up files used by cryptmount. I have attached two files that I hope will help you, and describe the small change being made to the file that is already installed on your computer.

In order to make fix the bug, you will need to do the following:
  * download 'cryptmount.txt' from this message
  * within a terminal window, type 'sudo mv cryptmount.txt /etc/init.d/cryptmount' to replace the old cryptmount start-up file with the new version
  * type 'sudo chmod 755 /etc/init.d/cryptmount' to check that the start-up file is executable
  * type 'sudo /etc/init.d/cryptmount start' (this should happen automatically next time you reboot your system).

The new start-up file contains two new lines, which are responsible for setting up the device-mapper within the operating system - these are needed by cryptmount in order to work correctly. The attached file 'cryptmount-init.d-patch.txt' shows how the new start-up file differs from the old one - you don't need to install that patch file itself, it's there only for information.

I hope this sorts out the difficulties you've had with cryptmount.

---

### Post by unix4linux on 2007-12-03
Hi, thanks for your post on how to fix this.  I was having the same problem and made the change with the new file and I was able to create my LVMs :-)...

Thanks again!!!

---

### Post by earthforce_1 on 2007-12-29
I was also having the same problem and tried your fix, but regrettably it didn't totally solve my problem.  I now get:
 sudo cryptmount --prepare secret
enter password for target "secret": 
device-mapper: reload ioctl failed: Invalid argument
device-mapper task failed
device-mapper target-creation failed for "secret"

If it matters, I am using the gutsy sparc64 server build, and filed this as bug #178889 in devmapper.
[https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/178889](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/178889)
Any other ideas would be much appreciated!  (I tried again after rebooting the server, no joy...)

---

### Post by shadowfirebird on 2008-03-31
I had exactly the same problem, but just rebooting fixed it.  I didn't change any files or anything.  [Gutsy].

---

### Post by jean david hsu on 2008-06-19
earthforce_1: make sure the partition you are trying to prepare is not already mounted

---

