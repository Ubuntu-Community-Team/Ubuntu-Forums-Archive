---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-02-17
forum: General Help
---

### Post by alppuccino on 2017-02-17
I am trying to use the command ```
sudo apt-get -f install
``` and it keeps returning with this error:

```
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-genericrun-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-62-generic_4.4.0-62.83_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-59-generic_4.4.0-59.80_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Kindly advise.

Thanks in advance :)

---

### Post by ajgreeny on 2017-02-17
Try running command ```
sudo apt-get clean
```to remove cached packages from /var/cache/apt/archives which could be corrupt, then try reinstalling the three packages mentioned in your error with ```
sudo apt-get install --reinstall initramfs-tools linux-image-4.4.0-62-generic_4.4.0-62.83_amd64.deb linux-image-4.4.0-59-generic_4.4.0-59.80_amd64.deb
```
Come back again if that does not help.

---

### Post by alppuccino on 2017-02-17
Hi ajgreeny,
                Thanks for the reply. I did both commands and the second command outputted this 
```
E: Couldn't find any package by glob 'linux-image-4.4.0-62-generic_4.4.0-62.83_amd64.deb'E: Couldn't find any package by regex 'linux-image-4.4.0-62-generic_4.4.0-62.83_amd64.deb'
E: Unable to locate package linux-image-4.4.0-59-generic_4.4.0-59.80_amd64.deb
E: Couldn't find any package by glob 'linux-image-4.4.0-59-generic_4.4.0-59.80_amd64.deb'
E: Couldn't find any package by regex 'linux-image-4.4.0-59-generic_4.4.0-59.80_amd64.deb'
```

---

### Post by ajgreeny on 2017-02-17
Whoops! My bad.

It should have been just **linux-image 4.4.0-59-generic** and **linux-image 4.4.0-62-generic** without the ending part of **_4.4.0-62.83_amd64.deb** of each of those.

Sorry about that so try again; I am assuming from your comment that the **initramfs-tools** did reinstall OK?

---

### Post by alppuccino on 2017-02-17
Hi ajgreeny,
               I tried the same commands again but without the ending part of **_4.4.0-62.83_amd64.deb**.

It output this: 
```
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Sorry I am very newbie at this, and have never done this before.
Thanks for the reply.

---

### Post by alppuccino on 2017-02-17
I will actually post more of the error, sorry I cut it in half.

```
The following packages have unmet dependencies: initramfs-tools : Depends: initramfs-tools-core (= 0.122ubuntu8.8) but 0.122ubuntu8.5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by alppuccino on 2017-02-17
OK ajgreeny,
                I have gotten somewhere with your previous post;

> [COLOR=#000000]Try running command
[/COLOR][COLOR=#000000]
```
sudo apt-get clean
```[/COLOR]
[COLOR=#000000]
to remove cached packages from /var/cache/apt/archives which could be corrupt, then try reinstalling the three packages mentioned in your error with
[/COLOR]
```
[COLOR=#000000]sudo apt-get install --reinstall initramfs-tools linux-image-4.4.0-62-generic_4.4.0-62.83_amd64.deb linux-image-4.4.0-59-generic_4.4.0-59.80_amd64.deb[/COLOR]
```
[COLOR=#000000]
Come back again if that does not help.[/COLOR]

I tried it again with the same command and without the **[COLOR=#000000][FONT=&amp]_4.4.0-62.83_amd64.deb[/FONT][/COLOR]**[COLOR=#000000][FONT=&amp].

This time it says

[/FONT][/COLOR]```
You might want to run 'apt-get -f install' to correct these:The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-core (= 0.122ubuntu8.8) but 0.122ubuntu8.5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```[COLOR=#000000][FONT=&amp]

Does this provide any more/enough information?

[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-02-17
Have you run the command ```
sudo apt-get update && sudo apt-get upgrade
``` before trying all those other commands, as it looks as if you have not got the most recent package list in your system and therefore it is possible the OS is not fully updated.
Run the update/upgrade command and then try the other commands again.

Once again, sorry for that omission, but I assumed, probably wrongly, that you would do that automatically.
That is one of the problems of being a long time Ubuntu user; I tend to forget that new users will not do this if not told to do so.

---

### Post by alppuccino on 2017-02-17
It's okay haha. I am only 14 and trying to learn it so I can hopefully do something with my life lol...

Anyways, I do that and it outputs yet again ANOTHER error (ffs):

```
The following packages have unmet dependencies: linux-image-extra-4.4.0-59-generic : Depends: linux-image-4.4.0-59-generic but it is not installed
 linux-image-extra-4.4.0-62-generic : Depends: linux-image-4.4.0-62-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-62-generic but it is not installed
                       Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.



```

Thanks for replying :).

---

### Post by alppuccino on 2017-02-17
P.S: When I do ```
[COLOR=#000000][FONT=&amp]sudo apt-get update && sudo apt-get upgrade[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp] it does all of the shenanigans with installing it and outputs:

[/FONT][/COLOR]```
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-59-generic_4.4.0-59.80_amd64.deb (--unpack): cannot copy extracted data for './boot/System.map-4.4.0-59-generic' to '/boot/System.map-4.4.0-59-generic.dpkg-new': failed to write (No space left on device)
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
Preparing to unpack .../libapt-pkg5.0_1.2.19_amd64.deb ...
Unpacking libapt-pkg5.0:amd64 (1.2.19) over (1.2.15ubuntu0.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-62-generic_4.4.0-62.83_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-59-generic_4.4.0-59.80_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ajgreeny on 2017-02-17
Ah!
No space left on device error suggests we need to dig a bit deeper.

Show us the output of ```
df -h
```and we might be able to figure this out a bit more.

---

### Post by alppuccino on 2017-02-17
This sounds good :D

```

Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
tmpfs           3.2G  353M  2.8G  11% /run
/dev/sda5       220G   78G  132G  37% /
tmpfs            16G   28K   16G   1% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
/dev/sda1       230M  228M     0 100% /boot
tmpfs           3.2G     0  3.2G   0% /run/user/1001
tmpfs           3.2G     0  3.2G   0% /run/user/1009

```

---

### Post by ajgreeny on 2017-02-17
So you have a separate /boot partition; do you use LVM partitioning or encryption?

---

