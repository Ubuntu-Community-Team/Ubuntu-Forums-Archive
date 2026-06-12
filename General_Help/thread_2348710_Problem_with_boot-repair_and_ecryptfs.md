---
title: "Problem with boot-repair and ecryptfs"
date: 2017-01-06
forum: General Help
---

### Post by whthompson on 2017-01-06
Hello there, 

Hopefully someone can help me and my data is not lost. So to start it all off Ubuntu 16.04, Lenovo U31

*The cause of the problem. *I have a dedicated boot partition which can run out of memory with new linux headers. Following an answer here (although I now realize there is a better way to do this) I manually deleted old headers from /boot/. This has worked for well over a year, but today something must have gone wrong. Restarted my computer and it boots to black a screen (and flashing cap lock key).

Boot repair does not work. Chroot has problems running. I have mounted the Linux harddrive without any problems. But the home directory is still encrypted (see below). 

In some panic and desperation, I tried to manually fix /boot using the USB ubuntu's /boot but that was just silly and makes problems worse (they now have the wrong owner of those files)

So I have an encrypted home drive since upgrading to 16.04 with encryptfs. I know my mount password. I know my login password for  my user. And I think I know the passphrase (but not 100% sure anymore and the documentation and help getting encryptfs to work is not the best). 

So one of two things are what I want to do: 

1. fix /boot/ despite the homedrive being encrypted and getting chroot to work in this situation. 

2. some pointers to use encryptfs in this situation. I've tried encrypt-recover-private. And I get a file in /tmp/encript.* but when I, for example open this with "sudo nautilus", it says I'm supposed to press on a file to decrypt. But a terminal window just pops up and then closes. 

I'd prefer 1 to fix if possible (seems like the easier route).

Is any solution possible or am I screwed?

---

### Post by oldfred on 2017-01-06
I know the horse has left the barn, so closing barn door now is a little late.
But with Encryption, you must have really good backup procedures. So if major issues, you can reinstall & restore. The entire purpose of encryption is to prevent anyone that does not know passphrase from accessing your data. So even if you forget passphrase or some sort of corruption prevent use of passphrase then reinstall becomes about the only option.

You should be able to boot live installer, add lvm2 & cryptsetup so you can mount the encrypted partition.
About the first third of these instructions is mounting your encrypted partition. Where it says then you can do other tasks like fsck that is then what you may need. And or running Boot-Repair to reinstall boot loader/kernels. But even with Boot-Repair you must have / (root) mounted which is inside encrypted partition so you must manually provide passphrase for Boot-Repair to work. Also check in advanced options full uninstall/reinstall of grub and update kernel.

       How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup 

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by whthompson on 2017-01-06
My backup procedures are relatively good. Only about the last week of things will disappear in the absolute worst case.

So  will go down the route of mounting the encrypted folder. Now I know where I should focus my attention. Thanks.

---

### Post by whthompson on 2017-01-06
Ok. So I can mount my harddrive (sda3). And I can decrypt my /home/ within it  ecriptfs-recover-private and mounts to /tmp/ (which seems to be the recommended  way when googling around) - so worst case, woohoo I can backup all my most recent files get all my files so I am relieved.   

But to prevent reinstalling ubuntu, it appears I still need to get /root/ (and maybe my /home/ directory?) of sda3 unencrypted and within mount for boot-repair to communicate with it. 

And this I can't seem to do. Anyone got any tips here?

---

### Post by oldfred on 2017-01-06
This post is from Yann, who is the developer of Boot-Repair.

[https://ubuntuforums.org/showthread.php?t=2020544&p=12090667#post12090667](https://ubuntuforums.org/showthread.php?t=2020544&p=12090667#post12090667)

---

### Post by whthompson on 2017-01-07
Since I'm booting via USB and don't have my mount passphrase, the necessary folder in ecryptfs-unwrap-passphrase does not seem to decrypt. And this is needed for the stops in boot repair. So moving the files away and reinstalling seems to be the best option. Thanks for all help and I'll close the thread.

---

