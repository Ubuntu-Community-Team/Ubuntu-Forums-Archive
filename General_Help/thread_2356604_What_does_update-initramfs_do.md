---
title: "What does update-initramfs do?"
date: 2017-03-24
forum: General Help
---

### Post by John_Patrick_Mason on 2017-03-24
While following the instructions [here]("https://askubuntu.com/questions/458515/how-to-disable-internal-webcam") on how to disable the integrated webcam on my laptop, after typing:

```
sudo update-initramfs
```

and getting an error message about possibly missing firmware in the terminal, when I decided to reboot, after the system had done starting up, I got another series of error messages prompting me to send diagnostic info to Canonical. I'm just wondering whether the update-initramfs command, which I am not familiar with, is to blame.

---

### Post by kyknos12 on 2017-03-25
boot live cd same version to installation pc and try this
sudo mount /dev/sdXY /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -c -k x.x.x-xx-generic
for example if your kernel system 4.4.0-31-generic
update-initramfs -c -k 4.4.0-31-generic

---

### Post by vasa1 on 2017-03-25
> **kyknos12 said:**
> boot live cd same version to installation pc and try this
sudo mount /dev/sdXY /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -c -k x.x.x-xx-generic
for example if your kernel system 4.4.0-31-generic
update-initramfs -c -k 4.4.0-31-generic

Please clarify what you mean by ```
sudo mount /dev/sdXY /mnt
```

---

### Post by kyknos12 on 2017-03-25
Yes i know that but because I wrote from smartphone I did not see the options for code, Just now I saw the options go advanced options, next time I will bare it in mind

---

### Post by John_Patrick_Mason on 2017-03-25
> **kyknos12 said:**
> boot live cd same version to installation pc and try this
sudo mount /dev/sdXY /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -c -k x.x.x-xx-generic
for example if your kernel system 4.4.0-31-generic
update-initramfs -c -k 4.4.0-31-generic

To build slightly on what vasa1 has said, which sda partition should I mount? Cause there's sda, sda1, sda2, sda3, sda4, sda5, and sda6.

Also, what am I doing here? Am I like updating the firmware? Didn't I already do that in the instructions above?

---

### Post by ian-weisser on 2017-03-25
The title of your thread is "What does update-initramfs do?"
One assumes you actually want an answer.

initramfs is a tiny version of the OS that gets loaded by the bootloader, right after the kernel. It lives in RAM, and it provides *just* enough tools and instructions to tell the kernel how to set up the real filesystem, mount the HDD read/write, and start loading all the system services. It includes the stub of init, PID #1. If your initramfs is broken, your boot fails.

update-initramfs is a script that updates initramfs to work with a new kernel. In the Debian universe, you shouldn't need to run this command manually except under very unusual circumstances - a post-install script automatically handles it for you when you install a new kernel package.

---

### Post by John_Patrick_Mason on 2017-03-25
> **ian-weisser said:**
> update-initramfs is a script that updates initramfs to work with a new kernel. In the Debian universe, you shouldn't need to run this command manually except under very unusual circumstances - a post-install script automatically handles it for you when you install a new kernel package.

So in the [instructions]("https://askubuntu.com/questions/458515/how-to-disable-internal-webcam") in the link I provided on how to disable the integrated webcam from AskUbuntu, running the command:

```
sudo update-initramfs
```

can be considered optional, am I right?

If so, how do I reverse the damage (if any) after running sudo update-initramfs. Can I just go in /boot and delete the image that was created when I ran the command?

---

### Post by ian-weisser on 2017-03-25
Changing (updating) the initramfs merely prevents some modules from being loaded. I'm not sure I would call that damage.

DO NOT manually delete initramfs files unless you know what you are doing.  _That_ would be damage. You might make your system un-bootable.

Simply use modprobe to restore the kernel module, then update-initramfs again, then reboot. Your system should be back to where you began before your odyssey.

---

### Post by John_Patrick_Mason on 2017-03-25
> **ian-weisser said:**
> Simply use modprobe to restore the kernel module, then update-initramfs again, then reboot. Your system should be back to where you began before your odyssey.

```
modprobe uvcvideo
```

?

(uvcvideo being the name of the webcam driver.)

---

### Post by kyknos12 on 2017-03-26
> **John_Patrick_Mason said:**
> To build slightly on what vasa1 has said, which sda partition should I mount? Cause there's sda, sda1, sda2, sda3, sda4, sda5, and sda6.

Also, what am I doing here? Am I like updating the firmware? Didn't I already do that in the instructions above?

```
sudo mount /dev/sdX /mnt
``` where your system

---

### Post by John_Patrick_Mason on 2017-03-31
What I need to know is:

1) Is running the command:

```
sudo update-initramfs
```

necessary when following the instructions (first answer) [here]("https://askubuntu.com/questions/458515/how-to-disable-internal-webcam")?

And 2)

How do I re-enable the webcam? Can I delete the .conf file that I created that contains the blacklisted webcam driver and delete the code:

```
install module_name /bin/false
```

from the other .blacklist.conf file before running:

```
sudo update-initramfs
```

? Or do I need to do something else?

---

### Post by ian-weisser on 2017-04-01
Do you wish to re-enable the webcam permanently, so it works-by-default upon booting? If so, then you must update initramfs with the proper list of kernel modules. 

Or do you wish the webcam to be disabled at boot, so that you can enable it manually? If so, then you need not update initramfs. You modprobe the kernel modules upon demand.

---

