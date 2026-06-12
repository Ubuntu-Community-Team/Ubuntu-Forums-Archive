---
title: "Ubuntu 14.04 - Can't perform security updates"
date: 2015-05-26
forum: General Help
---

### Post by carmen2012 on 2015-05-26
I have been unable to update my version of Ubuntu for perhaps the last month.  Below is the error message that I receive.  I have emptied my trash and run sudo apt-get clean but still get the error message.

Any help would really be greatly appreciated.

***********************************************************************

When I try and run software update, I get the following message:

Not enough free disk space.  The update needs a total of83.6 M free space on disk '/ boot'.  Please free at least an additional 20.4 M of disk space on '/boot'.  Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by sandyd on 2015-05-26
Sounds like your boot partition is full

Can you post the output of the following:
```

ls -l /boot
apt-get -s autoremove
```

---

### Post by carmen2012 on 2015-05-26
Thank you for your response, here is the output from these commands

administrator@M91:~$ ls -l /boot
total 160312
-rw-r--r-- 1 root root  1164967 Jan 13 12:12 abi-3.13.0-45-generic
-rw-r--r-- 1 root root  1164852 Mar 10 13:43 abi-3.13.0-46-generic
-rw-r--r-- 1 root root  1164723 Mar 12 04:52 abi-3.13.0-48-generic
-rw-r--r-- 1 root root  1164723 Apr 10 14:05 abi-3.13.0-49-generic
-rw-r--r-- 1 root root   165748 Jan 13 12:12 config-3.13.0-45-generic
-rw-r--r-- 1 root root   165748 Mar 10 13:43 config-3.13.0-46-generic
-rw-r--r-- 1 root root   165773 Mar 12 04:52 config-3.13.0-48-generic
-rw-r--r-- 1 root root   165773 Apr 10 14:05 config-3.13.0-49-generic
drwxr-xr-x 5 root root     1024 Apr 20 07:12 grub
-rw-r--r-- 1 root root 30193257 Feb 25 14:50 initrd.img-3.13.0-45-generic
-rw-r--r-- 1 root root 30195161 Mar 20 12:58 initrd.img-3.13.0-46-generic
-rw-r--r-- 1 root root 30206790 Apr  9 14:27 initrd.img-3.13.0-48-generic
-rw-r--r-- 1 root root 30202741 Apr 20 07:33 initrd.img-3.13.0-49-generic
drwx------ 2 root root    12288 Aug 15  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3389258 Jan 13 12:12 System.map-3.13.0-45-generic
-rw------- 1 root root  3389458 Mar 10 13:43 System.map-3.13.0-46-generic
-rw------- 1 root root  3389235 Mar 12 04:52 System.map-3.13.0-48-generic
-rw------- 1 root root  3389437 Apr 10 14:05 System.map-3.13.0-49-generic
-rw------- 1 root root  5814112 Jan 13 12:12 vmlinuz-3.13.0-45-generic
-rw------- 1 root root  5814592 Mar 10 13:43 vmlinuz-3.13.0-46-generic
-rw------- 1 root root  5815680 Mar 12 04:52 vmlinuz-3.13.0-48-generic
-rw------- 1 root root  5815392 Apr 10 14:05 vmlinuz-3.13.0-49-generic
administrator@M91:~$ apt-get -s autoremove
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Also keep in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
administrator@M91:~$ ^C
administrator@M91:~$

---

### Post by sandyd on 2015-05-26
Hmm, since you interrupted apt, it doesn't seem to want to remove the old kernels.

Can you post the output of
```

dpkg -l | grep -i "linux-image-\|linux-signed\|linux-tools"
```

---

### Post by carmen2012 on 2015-05-26
Here is the output of the second command that you requested.  You mentioned that I "interrupted apt", could you advise what that means.  I'm not sure how I would have done unless it was by accident as I'm not sure what that means.

administrator@M91:~$ dpkg -l | grep -i "linux-image-\|linux-signed\|linux-tools"
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.49.56                                        amd64        Generic Linux kernel image
administrator@M91:~$

---

### Post by sandyd on 2015-05-26
Apt got interrupted because your boot partition had no more space

Try
```

sudo dpkg -r linux-image-3.13.0-45-generic linux-image-3.13.0-46-generic linux-image-3.13.0-48-generic linux-image-extra-3.13.0-45-generic linux-image-extra-3.13.0-46-generic linux-image-extra-3.13.0-48-generic
sudo update-grub
sudo apt-get -f install

```

---

### Post by SeijiSensei on 2015-05-27
[This problem]("http://ubuntuforums.org/showthread.php?t=2278674") has gotten out of hand.  This is the second posting just today. Maybe it's time for a sticky on the subject.

---

### Post by carmen2012 on 2015-05-27
> **sandyd said:**
> Apt got interrupted because your boot partition had no more space

Try
```

sudo dpkg -r linux-image-3.13.0-45-generic linux-image-3.13.0-46-generic linux-image-3.13.0-48-generic linux-image-extra-3.13.0-45-generic linux-image-extra-3.13.0-46-generic linux-image-extra-3.13.0-48-generic
sudo update-grub
sudo apt-get -f install

```

Thank you Sandyd, this command did fix the issue.

@[COLOR=#000000]SeijiSensei I do agree with you in that this is an issue.  I've had this issue for many months now.  Some time back, someone on the forum gave me a command to run which cleaned up space.  That command has worked everytime with the exception of this week which is why I did end up making this post.  It is a bit disappointing that Ubuntu has become difficult to update.  I consider myself a novice and have really enjoyed earlier versions of this OS where you would just click on the software update icon and the OS would just take care of everything.

Having to run commands I don't understand is also a bit unnerving, but I do trust the mods that are offering up the commands and I do appreciate their time and efforts.[/COLOR]

---

