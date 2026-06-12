---
title: "How to rollback kernel 16.04.2?"
date: 2017-02-21
forum: General Help
---

### Post by linuxthunder on 2017-02-21
Greetings,

I'm running Ubuntu 16.04.2 with the recent upgrade and I decided to opt in for the newer kernel for the hardware stack by adding this command:


sudo apt install --install-recommends xserver-xorg-hwe-16.04


This installed a 4.8 kernel and I'm wondering if someone can help me revert these changes and go back to the stable 4.4 kernel permanently?

Thanks!

---

### Post by #&amp;thj^% on 2017-02-21
How to Uninstall:

If you don’t like the new X stack...you can remove it via commands:

```
sudo apt remove xserver-xorg-core-hwe-16.04 xserver-xorg-input-all-hwe-16.04 linux-generic-hwe-16.04 xserver-xorg-video-all-hwe-16.04
```

You’ll see the command also removes the ubuntu-desktop package. Don’t worry. The following commands will install it back.

to install the original xserver-xorg via commands:

```
sudo apt install xserver-xorg-core
```
This is for Ubuntu DE
```
sudo apt install ubuntu-desktop xserver-xorg libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
```

If you want to remove the new kernel 4.8, reboot and select boot with old 4.4 kernel (grub -> Advanced Options), 

To list all kernels excluding the current booted:

```
dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)
```
**WARNING**: Although I have tested this many times on my systems with perfect results your mileage may vary.
_So make sure you have a good back-up for what you don't want to lose_...just for a mishap.:D
Good Luck;)

---

### Post by Bashing-om on 2017-02-21
linuxthunder; Sure - doable.

However the process "can" be a long one - 
install the 4.4 kernel and components
make sure you are able to boot the 4.4 kernel and all functions on your system with this kernel installed
remove the HWE components . That clean up may take a bit of effort .

We start this process by installing the 4.4 kernel:
```

df -h ## make sure we have operational head room - 200 Megs to spare where ever boot is?
sudo apt install --install-recommends linux-generic xserver-xorg-core xserver-xorg xserver-xorg-video-all xserver-xorg-input-all libwayland-egl1-mesa

```

Reboot the system to grub's boot menu and select the 4.4 kernel ( 4.4.0-63-generic ) .
Now IF all is functional on this kernel we remove the HWE packaging:
```

sudo apt purge linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial

```
Next we check to see what else is on the system that we need to also remove.
Post back - between code tags - the result of terminal commands:
```

dpkg -l | grep linux-
ls -al /boot/

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

From here we finalize the cleanup - depending on what is .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by linuxthunder on 2017-02-21
Thank you for the instructions!  Is the Ubuntu DE the "developer edition?"  I'm not using that.  Thanks

---

### Post by linuxthunder on 2017-02-21
Ok, thanks for this tutorial as well.  I did not remove the previous 4.4 kernel when I upgraded to 4.8.  So could I just boot into the older kernel and then remove what I added?  

Thanks

---

### Post by #&amp;thj^% on 2017-02-21
> **linuxthunder said:**
> Thank you for the instructions!  Is the Ubuntu DE the "developer edition?"  I'm not using that.  Thanks

No... it is Ubuntu with Unity as the Desktop Session. So this [DE=Desktop Environment].
So did everything go okay then?
It also would not hurt if you ran this code after you downgrade:
```
sudo apt --purge autoremove
```
If you need any more help just post back here. (On the same topic of course):)

---

### Post by linuxthunder on 2017-02-21
Thanks for the information.  I'm confused because there are two different instructions in the thread.  I'm not sure which one to choose or if they both achieve the same outcome?

---

### Post by #&amp;thj^% on 2017-02-21
I only know for sure about "my" method...(This should make good sense)
But you can pick your poison here...as Bashing-om is a **very trusted** user here in the forums.
But yes they both achieve the same outcome.
If you follow Bashing-om's post...Give him the output from the terminal he asked for:
```
df -h
```
Before proceeding with the rest of his instructions.

---

### Post by linuxthunder on 2017-02-21
I completely understand!  One question before proceeding.  When I boot into the grub menu and choose the old kernel to boot into, will this change the default kernel to the 4.4 so I don't have to boot into grub every time?  I guess I'm asking how do I know it will make the 4.4 kernel the default kernel in the grub config file.  Thanks

---

### Post by Bashing-om on 2017-02-21
linuxthunder; Well.

> **linuxthunder said:**
> I completely understand!  One question before proceeding.  When I boot into the grub menu and choose the old kernel to boot into, will this change the default kernel to the 4.4 so I don't have to boot into grub every time?  I guess I'm asking how do I know it will make the 4.4 kernel the default kernel in the grub config file.  Thanks

The short answer. the system is smart ; with scripts, hooks and ladders.
when a new kernel is installed grub gets updated
when kernels are removed - grub gets updated.
In the event that there is a failure - this is ubuntu - it is always fixable .
There can be times one has to tell grub ( GRand Unified Bootloader ) what to do . rare !

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2017-02-21
We will get there>  Its all a process.
But this part in my 1st thread:
```
linux-generic-hwe-16.04
```
Removes (Uninstalls) The 4.8 kernel..so it "should" default back to the 4.4 kernel

---

### Post by linuxthunder on 2017-02-21
This what I was afraid of.  I cannot get into grub menu on boot.  I've tried 10 times holding down the shift key and it just goes to the ubuntu login screen.  Any suggestions?

---

### Post by #&amp;thj^% on 2017-02-21
> **linuxthunder said:**
> This what I was afraid of.  I cannot get into grub menu on boot.  I've tried 10 times holding down the shift key and it just goes to the ubuntu login screen.  Any suggestions?
Are you posting this from the same machine?

---

### Post by linuxthunder on 2017-02-21
1fallen, I am posting this from the same machine.  Since you were the first that responded I followed your instructions exactly.  Tried to reboot into grub to change kernels but I can't get to the menu.  I'm logged in now to the desktop which is working so perhaps there is another way to remove the kernel?

uname -r shows 4.8.0-36-generic

Please let me know the next steps.  Thanks

```
rc  linux-image-4.4.0-31-generic                4.4.0-31.50                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-57-generic                4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic                4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-63-generic                4.4.0-63.84                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
```

Above is what your command shows.

---

### Post by Bashing-om on 2017-02-21
linuxthunder; Well ;

Strange things can happen .
as to :
> 
Tried to reboot into grub to change kernels but I can't get to the menu. 
 EFI endowed machine ? Such that it is the escape key that grub looks for .

bk

The dpkg output says that 4.8 is no longer installed . Have you rebooted such that initramfs no longer sees the 4.8 kernel ?
We can see what grub has set to boot :
```

ls -al /vmlinuz* /initrd.img*

```

see where we go from here .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2017-02-21
Can you please run this:
```
sudo apt --purge autoremove && sudo update-grub
```
Paste back the output from the above here...so I can see what is going on.

---

### Post by linuxthunder on 2017-02-21
[COLOR=#000000]dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)


Is what I ran to show the above output which excludes the currently running kernel so 4.8 is the one I am currently using.

[/COLOR]

> **1fallen said:**
> Can you please run this:
```
sudo apt --purge autoremove && sudo update-grub
```
Paste back the output from the above here...so I can see what is going on.

Won't this remove all the 4.4 kernels that I have installed?  I'm currently on the desktop with 4.8 running.

> **Bashing-om said:**
> linuxthunder; Well ;

Strange things can happen .
as to :
EFI endowed machine ? Such that it is the escape key that grub looks for .

bk

The dpkg output says that 4.8 is no longer installed . Have you rebooted such that initramfs no longer sees the 4.8 kernel ?
We can see what grub has set to boot :
```

ls -al /vmlinuz* /initrd.img*

```

see where we go from here .
[INDENT][INDENT]we can do that
[/INDENT]
[/INDENT]


ls -al /vmlinuz* /initrd.img*
lrwxrwxrwx 1 root root 32 Feb 21 15:36 /initrd.img -> boot/initrd.img-4.4.0-63-generic
lrwxrwxrwx 1 root root 32 Feb 18 10:29 /initrd.img.old -> boot/initrd.img-4.8.0-36-generic
lrwxrwxrwx 1 root root 29 Feb 21 15:36 /vmlinuz -> boot/vmlinuz-4.4.0-63-generic
lrwxrwxrwx 1 root root 29 Feb 18 10:29 /vmlinuz.old -> boot/vmlinuz-4.8.0-36-generic

---

### Post by deadflowr on 2017-02-21
Reboot as Bashing-om has stated. And when the first screen goes blank, press the Shift key or the Esc key to get the grub menu.
You may need to go into the Advanced Options to select the older kernel.
Then boot the older kernel.


Accessing the grub menu depends on the BIOS setting,
so
older BIOS settings used the Shift key
and the newer BIOS (UEFI) uses the Esc key.

Hope that helps


The first screen means the very first screen that shows when you start the machine.

---

### Post by linuxthunder on 2017-02-21
I was able to get to grub by holding escape but it is a bash prompt with a list of possible commands.  Do you know what I enter to get to a kernel boot menu?

---

### Post by #&amp;thj^% on 2017-02-21
It would be very helpful here if you could show us what you see...Via: copy and paste.
As it stands I have no idea where you are in the grub status.
If you are where I think you are, Try this for the code:
```
normal
```
This should Return to the standard "grub>" mode if possible.

---

### Post by linuxthunder on 2017-02-21
Ok, I finally got into grub and booted to 4.4 kernel, so I am close.

```
ls -al /vmlinuz* /initrd.img*
lrwxrwxrwx 1 root root 32 Feb 21 15:36 /initrd.img -> boot/initrd.img-4.4.0-63-generic
lrwxrwxrwx 1 root root 32 Feb 18 10:29 /initrd.img.old -> boot/initrd.img-4.8.0-36-generic
lrwxrwxrwx 1 root root 29 Feb 21 15:36 /vmlinuz -> boot/vmlinuz-4.4.0-63-generic
lrwxrwxrwx 1 root root 29 Feb 18 10:29 /vmlinuz.old -> boot/vmlinuz-4.8.0-36-generic
```

It looks like 4.8 is still there.  What should I do at this point?



Here is the output from bash's recommendation:

```
dpkg -l | grep linux-ii  linux-base                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                              1.157.8                                       all          Firmware for Linux kernel drivers
ii  linux-generic                               4.4.0.63.67                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-63                      4.4.0-63.84                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-63-generic              4.4.0-63.84                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-36                      4.8.0-36.36~16.04.1                           all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-36-generic              4.8.0-36.36~16.04.1                           amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                       4.4.0.63.67                                   amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-31-generic                4.4.0-31.50                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-57-generic                4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-63-generic                4.4.0-63.84                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-36-generic                4.8.0-36.36~16.04.1                           amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic          4.4.0-31.50                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-57-generic          4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-63-generic          4.4.0-63.84                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-36-generic          4.8.0-36.36~16.04.1                           amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-generic                         4.4.0.63.67                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-63.84                                   amd64        Linux Kernel Headers for development
ii  linux-signed-generic                        4.4.0.63.67                                   amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-4.4.0-57-generic         4.4.0-57.78                                   amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-63-generic         4.4.0-63.84                                   amd64        Signed kernel image generic
ii  linux-signed-image-generic                  4.4.0.63.67                                   amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies

ls -al /boot/
total 108276
drwxr-xr-x  4 root root     4096 Feb 21 16:56 .
drwxr-xr-x 25 root root     4096 Feb 21 15:36 ..
-rw-r--r--  1 root root  1245512 Feb  1 14:39 abi-4.4.0-63-generic
-rw-r--r--  1 root root  1407843 Feb  5 06:32 abi-4.8.0-36-generic
-rw-r--r--  1 root root   190247 Feb  1 14:39 config-4.4.0-63-generic
-rw-r--r--  1 root root   199575 Feb  5 06:32 config-4.8.0-36-generic
drwx------  3 root root     4096 Dec 31  1969 efi
drwxr-xr-x  5 root root     4096 Feb 21 16:57 grub
-rw-r--r--  1 root root 37714621 Feb 21 15:36 initrd.img-4.4.0-63-generic
-rw-r--r--  1 root root 40096004 Feb 18 10:29 initrd.img-4.8.0-36-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3883990 Feb  1 14:39 System.map-4.4.0-63-generic
-rw-------  1 root root  4060748 Feb  5 06:32 System.map-4.8.0-36-generic
-rw-------  1 root root  7087088 Feb  1 14:39 vmlinuz-4.4.0-63-generic
-rw-------  1 root root  7089016 Feb 21 15:36 vmlinuz-4.4.0-63-generic.efi.signed
-rw-------  1 root root  7297312 Feb  5 06:32 vmlinuz-4.8.0-36-generic
```

---

### Post by #&amp;thj^% on 2017-02-21
Great!... now lets get rid of that kernel:
```
sudo apt-get remove linux-image-4.8.0-36-generic linux-image-extra-4.8.0-36-generic linux-headers-4.8.0-36 linux-headers-4.8.0-36-generic
```
Post any Errors here if any. Before doing the next command.
Now lets manually update grub....I would like to see this return...so can you paste back the results of the follwing:
```
sudo update-grub
```
I would like to see that you are in good shape..and not leave you with problems.;)

---

### Post by linuxthunder on 2017-02-21
We did it!  Thanks so much for your help and patience.

The issue was when I booted, holding down escape rapidly moved me from the grub boot menu to the grub command prompt and I was stuck.  I had to just press escape quickly with a single click to bring up the advanced options so I could boot to the older kernel.  If I had just done that right this would have been quicker.

One last question.  I'm hoping I am now "back to where I was" before adding the new hardware stack and kernel?  Will my 16.04.2 machine continue to receive kernel updates and regular updates?

Thanks again!

---

### Post by #&amp;thj^% on 2017-02-21
Very Nice...Good Job! ;)
I would though strongly suggest that you run this next if you have not done so already.
```
sudo apt autoremove
```
We need to keep this tidy...to prevent future problems.
you can also run a simulation or dry run to see what is being removed without removing anything via:
```
sudo apt autoremove -s 
```
Edit: Yes it will still continue to receive kernel updates and regular updates
Kind regards

---

### Post by linuxthunder on 2017-02-21
Great.  I did autoremove and everything looks great now.  Thanks again!

---

### Post by Bashing-om on 2017-02-21
linuxthunder; Uh Huh .

See it is all a process - in learning .
> 
 I'm hoping I am now "back to where I was" before adding the new hardware stack and kernel? Will my 16.04.2 machine continue to receive kernel updates and regular updates?

Yes, this:
> 
ii  linux-generic
ii  linux-headers-generic
ii  linux-image-generic
ii  linux-signed-image-generic

says you are in good shape .

However, you removed toooo much - are you comfortable not having a backup kernel ? If so await the next kernel update.

lastly now for clean up :
Once more:
```
sudo apt autoremove

```
then I like it squeaky clean on my system. I get rid of the 'rc' ( removed but config files remain) marked packages,

While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
Now let’s remove all the packages marked as rc and call this a job well done ( 1fallen gets the cookies ) .

[INDENT][INDENT]nothing but a thing
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2017-02-21
> **Bashing-om said:**
>  ( 1fallen gets the cookies ) .[INDENT][INDENT]nothing but a thing
[/INDENT]
[/INDENT]

Ole friend... you know I will share my cookies....split 50/50.:)
You just got to love this little community here.
Opps we can't forget deadflowr gets her share also.;)

---

### Post by linuxthunder on 2017-02-22
> **Bashing-om said:**
> linuxthunder; Uh Huh .

See it is all a process - in learning .

Yes, this:

says you are in good shape .

However, you removed toooo much - are you comfortable not having a backup kernel ? If so await the next kernel update.

lastly now for clean up :
Once more:
```
sudo apt autoremove

```
then I like it squeaky clean on my system. I get rid of the 'rc' ( removed but config files remain) marked packages,

While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
Now let’s remove all the packages marked as rc and call this a job well done ( 1fallen gets the cookies ) .
[INDENT][INDENT]nothing but a thing
[/INDENT]
[/INDENT]


Thanks for the all the information.  Interestingly, I did an apt dist-upgrade this morning and it installed a new kernel!

ls -al /vmlinuz* /initrd.img*
lrwxrwxrwx 1 root root 32 Feb 22 10:43 /initrd.img -> boot/initrd.img-4.4.0-64-generic
lrwxrwxrwx 1 root root 32 Feb 21 08:45 /initrd.img.old -> boot/initrd.img-4.4.0-63-generic
lrwxrwxrwx 1 root root 29 Feb 22 10:43 /vmlinuz -> boot/vmlinuz-4.4.0-64-generic
lrwxrwxrwx 1 root root 29 Feb 21 08:45 /vmlinuz.old -> boot/vmlinuz-4.4.0-63-generic

Now I have a backup kernel as you suggest.

Do you still recommend the dpkg purge command above?

Thanks

---

### Post by deadflowr on 2017-02-22
> Do you still recommend the dpkg purge command above?
Only if you have any rc'd kernel packages in your dpkg -l output.
And, really, only if you want.
The packages listed with rc are actually removed except for some documentation files, which in all are quite small in size, usually only a few kb at most.

---

### Post by Bashing-om on 2017-02-22
@ linuxthunder; Uh Huh .

> **deadflowr said:**
> Only if you have any rc'd kernel packages in your dpkg -l output.
And, really, only if you want.
The packages listed with rc are actually removed except for some documentation files, which in all are quite small in size, usually only a few kb at most.

+1 -- As I said I like it squeaky clean; all clutter removed .. but it is such a small thing If you are not in the terminal alla the time and look'n at things, will not matter in the least . 

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by linuxthunder on 2017-02-22
> **Bashing-om said:**
> @ linuxthunder; Uh Huh .



+1 -- As I said I like it squeaky clean; all clutter removed .. but it is such a small thing If you are not in the terminal alla the time and look'n at things, will not matter in the least . 
[INDENT][INDENT]'buntu[INDENT][INDENT][INDENT]you can have it your way
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Ok, everything is squeaky clean now.  Thanks Bash!

---

### Post by Bashing-om on 2017-02-22
linuxthunder; Great !

We do good work !

And it is
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

