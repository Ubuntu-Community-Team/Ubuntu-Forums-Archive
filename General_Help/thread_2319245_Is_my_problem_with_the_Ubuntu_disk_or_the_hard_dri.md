---
title: "Is my problem with the Ubuntu disk or the hard drive or something else"
date: 2016-04-02
forum: General Help
---

### Post by jackyhughes on 2016-04-02
I am writing on an old Toshiba Satellite. I just installed Ubuntu with no problem at all. That took care of a problem with Windows starting. I like Ubuntu better, 
My only issue there is an annoying "system problem detected" thing that keeps coming up, I am fine with that. The Toshiba is not an issue. i am just using it to show the same disk will install at a reasonable speed on a different machine. I do not have a problem with this Toshiba. It is fine That is background information to show the disk works.

THE DIFFICULT ISSUE IS WITH A SECOND MACHINE

I also have an Acer Aspire 6930g,
This already had Ubuntu installed, but for about the fifth time Ubuntu failed. I know how to use gparted to find partitions and also how to use boot manager and so on. I also know how to use the code when grub fails. i have tried all these things. *I know how to cop*y and paste code, but you cannot do this when the machine has failed on booting up. When grub is broken I cannot repair grub because the keyboard lacks a "p" and a "y."( I get around this by using Onboard when the machine has Ubuntu installed).Nor can I get a USB keyboard to work. (So please do not suggest this as it has been tried)

Recently this Acer failed to start and of course, because it has a "p" in it I could not use the code needed to repair grub. 

I have fixed the problem before by using boot repair and know gparted shows me the partitions. I resorted to what I know and tried boot repair and it would not work. Gparted after leaving is for a long time, failed to show up any partition at all. I am sure two partitions exist. I have exhausted all the things I can do by inserting the disk and "Trying Ubuntu" as far as I know.

I have concluded my only hope was is do a clean re-install.

 Now to get to the actual problem unless anyone has other ideas on the above,


**HERE IS THE PROBLEM**-The rest is just the background to show what works and what I have tried that will not work.

it would be nice to re-install Ubuntu. When I try, it hangs for ages on the first part where it says "preparing to reinstall Ubuntu." If I get as far as the bit where you choose the picture, it hangs there forever. I gave up on one effort to install, but did eventually get to where it looked like the installation had started, but then it failed. The disk will not install Ubuntu it seems. It fails over and over and the process in contrast to the install on the Toshiba takes ages. I have installed Ubuntu on the Acer before with no problem, but now it does not seem to want to install. (reinstalled several times when Ubuntu broke.

**THIS IS THE QUESTION**

Is the hard disk broken?

Given I can obviously use the disk (an old 12.04) to install Ubuntu and upgrade in reasonable time on the Toshiba, is my hard disk the problem on the Acer? 

Is that why every so often Ubuntu "breaks" on the Acer.

I cannot think of another reason, but thought it was worth asking someone more technical than me.

**Extra information about what I have tried**

(Please do not tell me to burn any disk. I have never had any success. I will probably purchase a new ready burned one at some point in case the 12.04 has a nervous breakdown.)
(Please do not suggest I replace the Acer Keyboard. It is a back up I would like, but the cost would not justify doing it given I have the Toshiba working with a full keyboard.)
(code to repair grub without a "p" in it would be wonderful, but I am sure that is probably not possible.)

---

### Post by grahammechanical on 2016-04-02
Please talk about the problem of one machine and not two machines. And one problem at a time. Please. For I am confused as to what you want advice with.

Use the Onboard keyboard to create various commands in a Gedit text file and then use copy & paste when you need to run them in a terminal. Or copy and paste from the forum threads. I do this all the time. Typing errors cause frustration.

```
sudo update-grub
sudo grub-install /dev/sda
```

Regards.

---

### Post by jackyhughes on 2016-04-03
Thank you for the information and the code. I have just tried the code. I get:
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
error: cannot read from `/dev/sda'.
error: cannot read from `/dev/sda'.
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
```

Does that mean the hard disk is as I suspect, gone? 

ls brings up:

```
^Cubuntu@ubuntu:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
```

and I got this using some info from elswhere on the board

```
ubuntu@ubuntu:~$ sudo mount /dev/sdYY /mnt/boot
mount: mount point /mnt/boot does not exist
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ # Mount your virtual filesystems:
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
mount: mount point /mnt/dev does not exist
mount: mount point /mnt/dev/pts does not exist
mount: mount point /mnt/proc does not exist
mount: mount point /mnt/sys does not exist
mount: mount point /mnt/run does not exist
```

I guess the question is does this stuff show the hard disk has failed?

I assume from the lack of reply the answer is yes!

---

### Post by Bucky Ball on 2016-04-06
This:

```
sudo mount /dev/sdYY /mnt/boot
```

... means nothing. It tries to mount a non-existant device to a non-existant mount point. Example of the correct way below. 

```
sudo mkdir /mnt/sda1
sudo mount /dev/sd** /mnt/sda1
```

This creates the mountpoint /sda1 (but you could call it anything) in /mnt then attempts to mount a partition to it. You need to replace '/dev/sd**' with the correct details for the partition you are attempting to mount, for instance:

```
sudo mount /dev/sda5 /mnt/sda5
```

Remember, the mount point /mnt/sda5 could be called anything. For example, /mnt/socks. Doesn't matter. What does matter is that you have the correct details for the /dev/sd** that you are trying to mount.

PS: Please start using code tags for terminal output. See the green link in my signature at the bottom of this post.

---

### Post by jackyhughes on 2016-04-06
probably this is all connected to the other threads you merged? I really have no idea and as I already said, If someone had not on this thread said ask only one question it would all still be on this thread.

If I have 2 bad partitions I cannot fix, do I keep replacing the number in the code until I can mount to a partition? Or is that just me completely misunderstanding?

---

### Post by yancek on 2016-04-06
As I understand your post, the Acer is the computer you are having problems with, correct?  So how old/new is this computer and which version of Ubuntu are you using?

You indicate that you have Ubuntu installed on this machine and that for some unknown reason, it failed to start.  What exactly happened there?  Started booting and then failed, did you see any messages on screen and make a note of them?

When you boot and access the BIOS, is your hard drive recognized?  If not, a big problem.
Do you see the Grub boot menu when you try to boot the Acer, that is without the DVD?  If you  can, when you see the Ubuntu entry, hit the c key on the keyboard and if you get a grub prompt (grub>), that would be when you use the ls command.  What you posted just shows what is on the DVD.

From the booted DVD, run from a terminal:  sudo fdisk -l(Lower Case Letter L in the command)  see if there is any output on the disk partitions.  That would tell you which partitions to mount as suggested above.

Just saw your other post and as oldfred says, the boot repair output shows that you have only a small swap partition inside an Etendede partition and almost the entire drive before the Extended is empty and unallocated space.  That would have been your Ubuntu.  You might try the suggestions by oldfred regarding testdisk to get data.

---

